# Mehfil

Hire Mumbai's college musicians. Front-end prototype: students sign up and get verified,
recruiters browse artists, book them, chat, post events and form bands. An admin
dashboard approves students and recruiters.

## Run it
1. Open this folder in VS Code.
2. Install the **Live Server** extension (recommended automatically).
3. Right-click `index.html` -> **Open with Live Server** (http://localhost:5500).

No build step, no npm install.

## Tech stack
- HTML5, CSS3 (custom properties, grid, flexbox, media queries)
- Vanilla JavaScript (ES2020), no framework, hash-based single-page router
- Supabase (Postgres + Storage) through supabase-js v2, loaded from a CDN
- Google Fonts: Bricolage Grotesque, Instrument Sans
- Cover art generated as inline SVG (no image files)

## Folder structure
```
mehfil-project/
├── index.html              page shell, loads CSS then JS in order
├── css/
│   ├── base.css            colour tokens (--lamp is the amber accent), reset
│   ├── components.css      buttons, chips, form fields
│   ├── layout.css          nav, page layout
│   ├── home.css            hero, discover grid, how-it-works, CTA boxes
│   ├── profile.css         artist profile page
│   ├── modals.css          modals
│   ├── chat.css            messaging
│   ├── auth.css            sign up / sign in
│   ├── responsive.css      media queries
│   └── extras.css          ID viewer, events, bands, availability
└── js/                     (plain scripts, order matters, see index.html)
    ├── config.js           Supabase URL + anon key
    ├── data/
    │   ├── artists.js      mock artists, categories
    │   ├── band-roles.js   which artists can fill band seats
    │   └── seed-data.js    demo chat, demo bands, booked days
    ├── state.js            app state, booking/availability helpers
    ├── icons.js            SVG icons
    ├── cover-art.js        generated SVG cover art, avatars
    ├── artist-mapper.js    turns a database student into an artist card
    ├── views/              home, profile, booking, chat, auth, admin, bands
    ├── media.js            simulated audio/video playback
    ├── services/
    │   └── supabase-db.js  all database + storage calls
    ├── router.js           hash router and render()
    ├── events.js           click/submit/input handlers
    └── main.js             first render and database polling
```

## Database (Supabase)
Tables used: `students`, `recruiters`, `bookings`, `events`, plus a storage bucket
for ID cards. Set your project URL and anon key in `js/config.js`.
If they are missing the app falls back to in-memory demo data.

## Notes
- Admin password is hard-coded in `js/state.js` (`ADMIN_PASSWORD`). Fine for a demo, replace before going live.
- Brand accent colour: change `--lamp` in `css/base.css`.
