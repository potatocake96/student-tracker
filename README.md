# trackME — full bundle
Includes:
- Landing page (`index.html`) with animated logo, screenshots, pricing toggle, contact form (Formspree/EmailJS).
- App (`app.html`) with **Class selector**, **Classes** tab, and **All Subjects Progress** tab.
- Login (`login.html`) with centered layout + modals + animated logo.
- Firestore rules + placeholder screenshots in `/assets`.

## Firebase config
Paste your project's config in `login.html` and `app.html`.

## Admin identity
Set your admin email/UID in `app.html`:
```js
const ADMIN_EMAIL = "YOUR_ADMIN_EMAIL@example.com";
const ADMIN_UID = "PASTE_ADMIN_UID";
```

## Data model (per user)
- `/users/{uid}/classes/{classId}`: { name }
- `/users/{uid}/students/{studentId}`: { name, preferredName, classId }
- `/users/{uid}/students/{studentId}/subjects/{subjectId}`: { enrolled:true }
- `/users/{uid}/progress/{studentId}/subjects/{subjectId}/skills/{skillId}`: { completed: bool, updatedAt }

Global catalog (admin-writable, everyone readable):
- `/catalog/global/subjects/{subjectId}`
  - `/areas/{areaId}`
    - `/skills/{skillId}`

## Class filtering
Selecting a class in the header filters every student dropdown to that class. Add students into a specific class via the Students tab.

## Contact form
- **Formspree**: create a form and paste endpoint into `index.html` (FORMSPREE_ENDPOINT).
- **EmailJS**: paste Public key, Service ID, Template ID into hidden inputs; EmailJS script is already included.
