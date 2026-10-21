JeevanSetu Citizen SOS + Timeline + Admin Search update
1. Extract ZIP.
2. Replace the repository ROOT index.html with the included index.html.
3. Commit changes, wait for GitHub Pages deployment, then Ctrl+F5.
Features:
- Citizen live-location area now includes a timestamped GPS/SOS timeline and emergency contact save/call links.
- SOS first requests real browser GPS, then creates a local demo incident if backend is unavailable; the incident includes captured coordinates and an ID.
- Live sharing uses browser geolocation watch while page stays open.
- Admin search filters incident ID, citizen/user name, status, severity, location and responder fields; searches local records available in that browser.
Safety/limitations:
- This is a demo front end. If no real backend is configured, SOS and responder alerts are local simulations, not dispatched to police/ambulance. Emergency call 112 link is provided.
- LocalStorage is device/browser-local and cannot synchronize different devices.
- Location requires browser permission and may fail on devices without location services.
