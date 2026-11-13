# Connect another app to Orbit Zero

Available in Orbit Zero 1.9.0. The supported integration API is separate from Zero's internal browser interface.

Keep Orbit Zero running on the same computer as the other app. In **Settings → Devices → Connected apps**, turn on **Allow other apps**. You can connect in either of these ways:

- **Create a token yourself:** select **Create API token**, enter the app's name, review its access and create the token. Copy it into the other app's API-token setting. Zero shows the token only once; if you lose it, disconnect that entry and create another.
- **Approve a request:** start the connection from the other app, select **Review request** in Zero, check its name and choose **Allow app**. The other app receives its token automatically.

Both methods grant the same access. Each app has its own token, remembered until you disconnect that app or turn app access off. It does not receive your PS5 pairing credentials or provider accounts. Creating a token manually avoids the connection-request step; the other app still needs to reach Zero's local API on the same computer.

Approved apps can search games and add-ons, read available editions/sources/formats, start downloads, pause or resume them, retry another source, send retained computer downloads to PS5, read progress, and find the files kept on this computer. They can manage the same download list you see in Zero. Installation, arbitrary file actions, file deletion, account settings and PS5 pairing are outside this API.

Downloads appear in Zero's normal Downloads page. Computer-only downloads work without a PS5. PS5 destinations need the paired console online and use the usual space checks. Direct/TorBox choices follow Zero's settings, including **Always use TorBox**. If a provider needs human verification, its ordinary Zero window opens and the start request remains pending until that step completes or fails.

## Developer interface

Base URL: `http://127.0.0.1:34179/api/integrations/v1` (or Zero's configured port). Connect only over IPv4 loopback. Requests with another Host, a non-local peer, or an Origin header are rejected. There is no browser CORS interface. Existing UI cookies, the native PS5 token and `X-Orbit-Zero` are not authentication for this API.

Use `Content-Type: application/json` for POST requests. Do not attach an Origin header. Response errors are `{ "error": { "code": "STABLE_CODE", "message": "Explanation" } }`. Handle the code rather than matching the English message.

### Connect once per app

If your app accepts a manually supplied API token, the user can create one in Zero as described above. Use it directly as `Authorization: Bearer <token>` and skip `/connect`. Store it in the operating system's credential store.

For automatic token delivery with approval in Zero:

1. `POST /connect` with `{ "name": "Your app" }`. The response is HTTP 202 with `requestId`, `requestSecret`, `expiresAt` (Unix milliseconds) and `pollAfterSeconds`.
2. Ask the user to approve in Zero. Poll `POST /connect/status` with `{ "requestId": "…", "requestSecret": "…" }` no faster than the returned interval.
3. A `pending` result needs approval; `denied` means stop. An `approved` result includes `token` and `appId`. Connection requests expire after five minutes.
4. Store the token in your operating system's credential store. Send `Authorization: Bearer <token>` on all other API calls. Never log it, put it in a URL, or reuse Zero's own session cookies.

The app name is supplied by your app; it is not a verified publisher identity. Users should approve only requests they initiated. A 401 response means the token is missing, invalid or revoked. A 403 `API_DISABLED` response means app access is off. Turning app access off revokes existing grants; turning it on again requires new approval.

### Catalogue and destinations

| Request | Result |
| --- | --- |
| `GET /status` | API version, this app's identity, console connection and capabilities |
| `GET /catalogue?q=Example&platform=ps5&limit=50&offset=0` | Matching games and their options; `total`, `offset`, `limit`, `revision` |
| `GET /catalogue?kind=addons` | Separate add-on results; base-game results remain separate |
| `GET /catalogue?source=vikingfile&format=FFPFSC` | Filter options by source and format; repeat each query parameter for multiple choices |
| `GET /games/{gameId}` | Game details and all its available options |
| `GET /destinations` | This computer and available paired-PS5 drives, including free space |

Use option `id` values as `releaseId`. Keep a user's exact platform, title ID, edition and format choice. Options contain display and file information, not provider sessions or temporary download URLs. Pagination is by game, not by option; the maximum limit is 100.

### Start a download

`POST /jobs`, with a unique `Idempotency-Key` header:

```json
{
  "releaseId": "an-option-id-from-the-catalogue",
  "destination": { "type": "computer" },
  "delivery": "direct",
  "route": "auto"
}
```

For a PS5 drive, use `"destination": { "type": "ps5", "id": "usb0" }` with an ID returned by `/destinations`.

`delivery` is optional (`direct` or `torbox`). Omission uses the remembered method; Always use TorBox overrides it. `route` is optional: `auto` follows Zero's download preference, `computer` downloads on the computer and transfers when appropriate, and `ps5` requires a direct console download. Explicit `ps5` does not silently fall back to the computer and does not support the computer's TorBox connection. These per-request choices do not change the global download preference.

The response is HTTP 202:

```json
{ "requestId": "…", "state": "preparing", "createdAt": 1790000000000 }
```

Poll `GET /requests/{requestId}`. `complete` includes `result.jobId` (for example `computer:…` or `ps5:…`); `failed` includes a structured error. Completion here means that the action was accepted/finished, not that the entire game has downloaded. Read the job to follow its progress. A provider window can keep the start request pending while the user completes verification.

Reuse the **same action key and body** after a lost HTTP response. Concurrent requests with the same key start only once. Reusing a key with another body returns 409 `IDEMPOTENCY_CONFLICT`. Recent completed requests are retained for up to seven days, subject to a 200-request history bound; pending requests are not evicted. Do not reuse old keys for new actions. If Zero restarts during an uncertain start, its request becomes `interrupted` and is not automatically resubmitted. Inspect `/jobs` before issuing a new action key.

### Progress, retry and transfer

| Request | Purpose |
| --- | --- |
| `GET /jobs` | Computer-managed and direct PS5 jobs, current state, byte counts, rates and errors |
| `GET /jobs/{jobId}` | One job with the same fields |
| `GET /cache` | Per-job availability, completion and saved computer path; read-only |
| `POST /jobs/{jobId}/actions` | Pause, resume, retry or send a computer copy |

All action POSTs need a unique `Idempotency-Key` and return a request to poll, just like starting a job. Examples:

```json
{ "action": "pause" }
```

```json
{ "action": "resume" }
```

```json
{ "action": "retry", "releaseId": "another-source-option-id" }
```

```json
{ "action": "send", "destination": { "type": "ps5", "id": "usb0" } }
```

A retry without a replacement option resumes the saved job and its normal recovery checks. Your app chooses alternate sources. A replacement must match the original game, platform, title ID and format, and the old job must be paused or failed. Zero pauses the old job and starts a separate download, keeping its files. It never concatenates bytes from two source options or silently changes editions. Completed computer copies can be sent without downloading them again.

Poll about once a second while following active work, and less often while idle. A disconnected PS5 must not be treated as a completed download. If `/jobs` reports a PS5 error, the local jobs remain usable; reconnect through Zero. Cache paths can disappear after the user moves files or clears copies in Zero, so recheck availability before using them. An active or partial path is not a completed game. This API does not expose cache deletion or cancellation that would delete partial files.

## Compatibility

Clients must ignore unknown fields and handle unknown job states conservatively. Breaking changes require another integration API version.

[Orbit Zero](orbit-zero.md) · [Settings](settings.md) · [Project home](../README.md)
