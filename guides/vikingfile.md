# Use a Vikingfile account

Use matching ELF, native app and Orbit Zero builds. The settings paths below follow Orbit 1.8.0.

Vikingfile identifies an account with an **account hash**: the private code it gives you instead of an email/password login. Treat it like a password and do not include it in issues, screenshots or diagnostic reports.

## On PS5

In the native TV app, open **App settings → Sources & accounts** and scroll to **Vikingfile**. In the browser, open **App settings → Sources & accounts → Vikingfile** (or **Settings → Sources & accounts → Vikingfile** in Crossbar, Cinema and Panorama). Choose **Open Vikingfile account**. On the official provider page, enter your account code, complete human verification if requested and select **Login**. Return to Orbit and choose **Check sign-in**.

![Orbit 1.7.0 native Vikingfile settings with Open Vikingfile account and Check sign-in controls](../assets/1.7.0/native-vikingfile-account.png)

*Native app preview before sign-in. No account code is shown.*

Orbit shows **Signed in** only after Vikingfile confirms the session. Opening the page alone does not count. To manage the account or sign out, reopen the same account page. The PS5 browser and native app use separate browser stores, so you may need to sign in once in each interface you use.

Orbit uses the selected browser session when resolving and checking the file link, downloading it and resuming it. On PS5, it reads only Vikingfile’s session for the active user; Zero uses its own provider session. These cookies are not stored in download history, exposed in diagnostics or sent to TorBox or unrelated hosts. The session check also supplies the sign-in indicator.

## On your computer

In Orbit Zero’s **Settings → Sources & accounts → Vikingfile**, enter your account hash and choose **Sign in**. Zero fills the official page’s account field. Complete any human verification there. The account field is cleared after submitting; the resulting browser session stays on that computer. Use **Check sign-in** or **Sign out** in the same settings.

Computer sign-in and PS5 sign-in are separate. Pairing does not copy credentials between them.

## Downloading after sign-in

Orbit first asks Vikingfile for the selected file using the signed-in session. If Vikingfile supplies a matching direct link, the download can start without opening a provider window. If it requires verification, the page opens: complete verification and wait without pressing Download. Orbit captures the matching ready link and returns to the app.

Premium privileges are controlled by Vikingfile. A **Signed in** status does not claim premium membership or guarantee every file will skip verification. Expired sessions and provider challenges fall back to the provider page; sign in again if needed. Free-account downloads remain supported.

[Download guide](downloads.md) · [Orbit Zero](orbit-zero.md)
