# glance

A minimal, all-black clock for your desk or classroom screen: bell schedule countdown with A/B days, weather, and widgets you can move around (checklists, notes, homework with Canvas import, study timer, reminders, alarms and more).

Made by Dominic Schoenherr.

Live at **https://stratus-1221.github.io/glance/**

## Use it

Open the site, go through the short setup, and you're done.

- Move your mouse to show the settings gear (bottom right).
- Press **E** to move, resize and set up widgets. Each widget has its own gear.
- Press **?** to see every shortcut.
- Double-click for fullscreen.

## Feedback and shared schedules

Feedback people send shows up in the Firebase console under **Firestore → Data → feedback**.
Shared bell schedules are stored under **schedules**, one document per code.

## Turn on accounts (Firebase)

Accounts let people sign in and get the same clock at school and at home. It's free.

1. Go to [console.firebase.google.com](https://console.firebase.google.com) and create a project (Google Analytics not needed).
2. **Build → Authentication → Get started → Email/Password → Enable → Save.**
3. **Build → Firestore Database → Create database** (production mode, any location near you).
4. In Firestore, open the **Rules** tab, replace everything with the contents of `firestore.rules`, and click **Publish**.
5. **Project settings (gear) → Your apps → Web (`</>`)**, register an app, and copy the `firebaseConfig` object.
6. In `index.html`, replace `const FIREBASE_CONFIG = null;` with `const FIREBASE_CONFIG = { ...the config you copied... };`
7. **Authentication → Settings → Authorized domains → Add domain:** your GitHub Pages domain (like `yourname.github.io`).

The config values are meant to be public. The rules in `firestore.rules` are what keep each person's data private.

Sign-in only works on the website, not when you open the file straight from your computer.
