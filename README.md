# Student Progress Tracker (Firebase + GitHub Pages)

A single-file HTML app you can deploy on GitHub Pages. It uses Firebase Authentication (email/password only) and Firestore to store your data **per user**.

## What it imports from your Excel
Only **subject names** — i.e., the names of each worksheet/tab. Your uploaded file contained these tabs:

- Sheet1
- LIT_UNIT_1
- LIT_UNIT_2
- NUM_UNIT_1
- NUM_UNIT_2
- WRS_UNIT_1
- WRS_UNIT_2
- PDS_UNIT_1
- PDS_UNIT_2
- Consolidation

The app lets you add more subjects and define **Areas of Study** and **Key Skills** per subject.

## Quick start
1. Create a Firebase project → Add a Web app.
2. Enable **Authentication → Sign-in method → Email/Password**.
3. Create a **Firestore** database in production mode.
4. Paste the contents of `firestore.rules` into **Firestore → Rules**, then **Publish**.
5. Open `index.html` and paste your `firebaseConfig` (Project settings → General → Your apps).
6. Commit both files to a GitHub repo and enable **GitHub Pages** (Settings → Pages).

## Data model (under `/users/{uid}/…`)
- `students/{id}`: `{ name, preferredName, createdAt }`
- `subjects/{id}`: `{ name, createdAt }`
- `subjects/{id}/areas/{id}`: `{ name }`
- `subjects/{id}/areas/{id}/skills/{id}`: `{ name, order }`
- `students/{id}/subjects/{subjectId}`: `{ enrolled: true }` (student→subject mapping)
- `progress/{studentId}/subjects/{subjectId}/skills/{skillId}`: `{ completed, updatedAt }`

> The **Marking** page filters subjects by the selected student's enrolments, then shows the skills for the chosen area. Ticking a checkbox writes to the `progress` path above.

## Notes
- Deleting a subject in the UI removes the subject doc only (simplified). For deep cleanups (areas/skills/progress), remove nested docs manually or add a function.
- Everything is responsive for desktop and mobile.
- No Google sign-in — only email/password by design.

Happy teaching!
