# Nanoids Yandex Auth

This repository contains the static HTML page used to finish Nanoids Yandex sign-in.

## Important: redirect URI

The uploaded original Supabase function contains these settings in its comments:

- Function name: `yandex-callback`
- Current Yandex Redirect URI: `https://nwfrswfidmgfiztutbvk.supabase.co/functions/v1/yandex-callback`
- Supabase JWT verification: OFF

The original function does not exchange an authorization code or call the Yandex API. It only returns an HTML page that reads `access_token` (or `token`) from the URL and forwards it to the opener window, with `nanoids://oauth` as a fallback.

## GitHub Pages

1. Open **Settings → Pages** in this repository.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Choose branch `main` and folder `/(root)`.
4. Save and wait for GitHub Pages to publish.
5. The expected page address is `https://nikitosik20mihapika-netizen.github.io/nanoids-yandex-auth/`.

## Do not change the Yandex redirect URI blindly

The existing Yandex application is documented as using the Supabase Function URL above. GitHub Pages has a different URL. Before changing the redirect URI in Yandex or in the Nanoids client, verify how the client starts OAuth and which exact callback URL it expects.

If you decide to move the callback to GitHub Pages, update the redirect URI in the Yandex OAuth application and the corresponding URL in the Nanoids client to the exact GitHub Pages URL. Do not keep the old Supabase URL in one place and the new URL in another.

## Files

- `index.html` — static browser callback page.
- `README.md` — setup notes.

The original source file `edge_yandex_callback-1.ts` should be kept separately as a reference. It is not included as a deployable Supabase function here because it only serves this HTML page; its HTML response was being returned as `text/plain` on the standard Supabase domain.
