# Student Progress Tracker (two-page build)

- `login.html`: email/password auth
- `app.html`: the actual app (redirects to login if not authenticated)
- Pastel minimalist theme (Source Serif 4)
- Smooth fades/slides and custom dropdowns
- Sign out button returns to login

## Setup
1) Create Firebase project → add Web app → paste config into **both** `login.html` and `app.html`.
2) Enable Auth → Email/Password; create Firestore; publish the included `firestore.rules`.
3) Deploy both HTML files to GitHub Pages.
