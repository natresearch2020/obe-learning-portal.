# OBE Learning Portal — GitHub Pages edition

Static HTML/CSS/JS with Firebase Auth and Firestore. No Python server.

## Setup
1. Create a Firebase project at https://console.firebase.google.com/ and add a Web app. Copy its firebaseConfig object into firebase-config.js (keep the export). Never put service account keys or passwords in this file.
2. Authentication > Sign-in method: enable Email/Password. Authentication > Settings > Authorized domains: add YOURNAME.github.io. Configure verification/password reset email templates if desired.
3. Create a Firestore database in production mode. In Rules, replace the rules with firestore.rules and publish. Do not use test mode.
4. In Authentication > Users, add your administrator email/password. Copy its UID. In Firestore create collection users, document ID equal to UID, with fields name (string), email (string), role (string: admin), active (boolean: true), course (string: obe). Do not create admin through public registration.
5. Upload the contents of this ZIP (not an enclosing folder) to a GitHub repository. Settings > Pages > Deploy from a branch > main > / (root). Open the published URL.
6. Sign in as admin. Create course ID obe, title Outcome Based Education. Enter pre-course information and enable when ready. Create course2/course3 if needed. Publish modules 1–10 and final exam (11). No actual course content was supplied, so enter your own.
7. Students and teachers register via the registration form. Admin enables them and assigns role/course. Verification email is sent by Firebase; password reset is available. For removing an Auth account use Firebase console; disable access in portal first. Verification is not enforced by rules in this prototype.
8. Use HTTPS links to hosted videos, notes and live sessions. Direct MP4 playback can record approximate playback seconds; external links cannot be tracked. Ensure sharing permissions are appropriate. Attendance is self-reported. Certificates are manually issued by admin and printed to PDF.

## Test before enrolling
Use separate browser profiles for admin, teacher and student. Verify registration, approval, course isolation, module publishing, assessment submission, grading, private feedback, doubts and certificate. Verify teacher cannot grade final exams or read feedback. Check rules with Firebase emulator before production. JS syntax checked only; no live Firebase project was available for integration testing.

## Limitations
One course per user, one certificate per student, one submission per module, manual descriptive grading, no automatic MCQ or timed exam, no direct uploads, no per-feature permissions, no direct teacher-to-student allocation, no enforced 50-user/3-course cap. No automated certificate eligibility or trusted attendance/engagement. Registration verification email is not a custom enrollment email. Account creation/deletion by admin requires Firebase console or a future trusted backend. Public repository must contain no student records or secrets. Firebase free quotas and GitHub Pages usage terms apply. For production, add abuse protection, stronger validation, verified email enforcement, backups and rules tests.
