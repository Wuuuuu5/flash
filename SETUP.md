# Putting Index Card Box online (free)

Two parts: **Firebase** saves your cards and handles sign-in, and **GitHub Pages** hosts the website.
Both are free. It takes about 15 minutes.

## Part 1: Firebase (where your cards are saved)

1. Go to https://console.firebase.google.com and sign in with your Google account.
2. Click **Create a project**. Name it e.g. `flashcards`. You can turn **Google Analytics off**. Click **Create project**.
3. **Add a web app:** on the project's home page click the **`</>`** (Web) icon.
   Give it a nickname like `cards`. Leave "Firebase Hosting" **unticked**. Click **Register app**.
4. You'll see a block of code containing `const firebaseConfig = { apiKey: ..., ... }`.
   **Copy that `firebaseConfig` part and send it to Claude.** (These settings are not secret; they're meant to be in the web page.)
5. **Turn on Google sign-in:** left menu → **Build → Authentication** → **Get started** →
   **Sign-in method** tab → **Google** → turn on **Enable**, pick your email as the support email → **Save**.
6. **Create the database:** left menu → **Build → Firestore Database** → **Create database** →
   pick a location near you → choose **Start in production mode** → **Create**.
7. **Lock it to you:** in Firestore, open the **Rules** tab. Delete what's there, paste in the contents of
   `firestore.rules`, replace `YOUR_GMAIL_HERE` with your Gmail address, and click **Publish**.

## Part 2: GitHub Pages (the website)

1. Make a free account at https://github.com if you don't have one.
2. Click **+** (top right) → **New repository**. Name it `flashcards`, set it to **Public**, click **Create repository**.
   (Public only means the website code is visible. Your cards stay private in Firebase.)
3. On the new repository's page, click **uploading an existing file**. Drag in **all of these files**:
   `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`.
   Click **Commit changes**.
4. Go to **Settings → Pages**. Under "Branch" choose **main** and **/ (root)**, click **Save**.
   After a minute or two your site is live at `https://YOUR-GITHUB-NAME.github.io/flashcards/`.

## Part 3: Connect the two

1. Back in Firebase: **Authentication → Settings → Authorized domains → Add domain** →
   type `YOUR-GITHUB-NAME.github.io` → **Add**. (Without this, Google sign-in is refused.)
2. Open your site, tap **Sign in with Google**, and you're in.

## On your phone

- **iPhone:** open the site in Safari → Share button → **Add to Home Screen**.
- **Android:** open it in Chrome → ⋮ menu → **Add to Home screen** (or **Install app**).

It works offline too: cards you've already loaded stay available, and changes sync when you're back online.

## Updating the site later

Upload the changed file to the same GitHub repository (Add file → Upload files), and it updates within a couple of minutes.
If your phone still shows the old version, close the app fully and open it again.

## Backups

The **Back up cards** button at the bottom of the decks page downloads all your cards as a file.
**Restore from backup** loads that file back in.
