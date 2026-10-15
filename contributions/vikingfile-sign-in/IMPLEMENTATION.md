# Vikingfile sign-in for direct PS5 downloads

This is an implementation patch against Orbit Store **1.3.5** (native app
**1.7.0**), source commit `8043189a7d319be3ffdf828e08bf5a0f105a30fd` as
identified by that release's `BUILD-INFO.json`. The public `main` branch
publishes documentation and distribution metadata; the implementation is
distributed in the release source bundle. The patch lets the maintainer
review and apply the changes to the implementation checkout without adding
the entire release source to this repository.

## Behavior

In **App settings → Download sources**, select **Vikingfile → Sign in**.
Orbit opens `https://vikingfile.com/login` on the PS5. Enter the account hash
and complete any verification on Vikingfile's own page, then close the page
and return to Orbit. In the browser interface, select **Done** after returning.
Use the same Orbit interface to open the later Vikingfile download page.

The native app uses the same `ProviderWindow` instance for sign-in and later
download pages. The browser interface uses the existing PS5 system browser.
These are separate browser contexts; signing in through one is not reported
as signing in through the other.

Orbit does not receive or persist the account hash or copy browser cookies
into its download service. A sign-in session never enters download capture,
scans browser memory, validates a file, or creates a download. Only the fixed
Vikingfile HTTPS login page is supported. Existing authenticated local API
access, native dialog ownership, concurrent-session exclusion, cancellation,
and bounded session lifetimes are retained. Other download providers and
TorBox use their existing paths.

The UI reports opening/ending the provider page, rather than claiming that
authentication succeeded. Later download capture retains the existing
provider/filename/response validation.

## Apply to the published source

1. Download `orbit-store-1.3.5-source-bundle.zip` from the
   [official 1.3.5 release](https://github.com/saawant12/orbit-store-ps5/releases/tag/v1.3.5).
   Its SHA-256 is
   `c0fe51d94b199daa77b620b5d596afc13b77902076db313891885d0e54339858`.
2. Extract its `orbit-store-1.3.5-source.tar.gz`, then extract that archive.
3. From the resulting `orbit-store-1.3.5/` directory, run:

   ```sh
   git apply --check /path/to/orbit-1.3.5-vikingfile-sign-in.patch
   git apply /path/to/orbit-1.3.5-vikingfile-sign-in.patch
   ```

Follow the release's `BUILDING.md` for the pinned build inputs, browser build,
PS5 payload, native app, and licence/source packaging. The browser and native
app require the patched service's advertised `signInAvailable` capability;
older services hide the new control.

## Validation

With the release build prerequisites installed and cJSON bootstrapped:

```sh
node --test tests/viking-sign-in.test.mjs
npm run typecheck
node tools/i18n.mjs check
npm run build
```

The new offline regression test compiles the actual browser-session backend,
native API client, model parser, and dialog controller with AddressSanitizer
and UndefinedBehaviorSanitizer. It checks fixed-destination routing,
unsupported-provider rejection, session ownership, cancellation, launch failure,
concurrent-session exclusion, zero download activity during sign-in, and a
normal captured download afterward. It uses only synthetic identifiers.

These checks passed locally, along with strict syntax checks for all modified
native C++ translation units and the production backend browser translation
unit. Translation completeness passes for all ten non-English catalogues.
The release source omits the upstream root development tests; those existing
tests still need to run in the maintainer's implementation checkout.

## PS5 validation still required

Before release, verify the actual provider/browser behavior on hardware:

- Open sign-in in both the native dialog and browser interface; complete
  Vikingfile's normal verification manually.
- Close and reopen the corresponding provider browser and confirm whether
  Vikingfile retains its signed-in session. The offline tests establish reuse
  of the browser instance, not cookie persistence by the PS5 implementation.
- Download a small file the tester owns, using a direct Vikingfile option,
  and verify that its generated link works with Orbit's existing transfer
  validation. Account-specific or premium benefits are not yet verified.
- Exercise cancellation, app/service restart, and expired provider sessions.
  No successful sign-in status should be inferred from closing a page.

No test binary was installed on a console or published with this contribution.
