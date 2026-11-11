# TV dashboard

A dashboard for the living-room LG (43UN70006LA, webOS 5).

- `index.html` is the dashboard page, served by GitHub Pages at
  https://teetats-hub.github.io/tv-dashboard/
- `data.json` holds the curated content (headlines, markets, sport, rates).
  A scheduled Claude task rewrites it a few times a day.
- Weather (Open-Meteo), exchange rates (ECB via Frankfurter) and live scores
  (ESPN) are fetched by the page itself on the TV.
- Nothing personal goes in this repo. It is public.

Test a layout by adding `#morning`, `#day`, `#evening`, `#night` or `#live`
to the address.

## Installing the LG app (one time)

The app is a "hosted web app": a home-screen icon that opens the page above
full screen. Updates to the page reach the TV without reinstalling.

1. **LG developer account.** Sign up free at https://webostv.developer.lge.com
2. **Developer Mode on the TV.** On the LG, open the Content Store, install
   "Developer Mode", sign in with that account, switch **Dev Mode Status** on
   (the TV restarts), then reopen the app and switch **Key Server** on.
   Note the IP address and passphrase it shows.
3. **webOS Dev Manager on your PC.** Download the Windows installer from
   https://github.com/webosbrew/dev-manager-desktop/releases
   Add your TV with the IP address and passphrase from step 2.
4. **Install the app.** In Dev Manager, open Apps, click install and choose
   `com.teetats.dashboard_1.0.0_all.ipk`. A "Dashboard" icon appears on the TV.

If the install is rejected, build the package with LG's own tool instead:
install Node.js, run `npm install -g @webos-tools/cli`, then
`ares-package webos-app` in this folder, and install the file it produces.

## Keeping it alive

Developer Mode lasts up to 1000 hours (about six weeks). Open the Developer
Mode app and press **Extend** every month or so, or let Home Assistant do it
later. If the session runs out, the app disappears and needs installing again.
