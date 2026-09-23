# Matt Calendar: GitHub setup

The app is hosted on GitHub Pages, and your data is stored in a private GitHub repo. That keeps everything on GitHub: nothing else to sign up for, and nobody but you can read the calendar.

You'll make two repos:

| Repo | Visibility | What's in it |
|---|---|---|
| `calendar` | Public | The app files from this folder (no personal data, no keys) |
| `calendar-data` | **Private** | Your entries, projects, highlights and header photos |

## 1. Make the private data repo

1. Go to **github.com/new**.
2. Name it `calendar-data`, choose **Private**, and tick **Add a README file**.
3. Click **Create repository**. Leave it empty; the app fills it in.

## 2. Put the app online

1. Go to **github.com/new** again. Name it `calendar`, choose **Public**, and click **Create repository**.
2. On the new repo page, click **uploading an existing file**. Drag in everything from this folder, then click **Commit changes**.
3. Open the repo's **Settings → Pages**. Under **Branch**, choose `main` and `/ (root)`, then click **Save**.
4. Wait about a minute. The app will be at **https://szarette.github.io/calendar/**

## 3. Make the access token

This token lets the app read and save the one data repo. It can't touch anything else in your account.

1. Go to **github.com/settings/personal-access-tokens/new**. This makes a *fine-grained* token.
2. **Token name:** `Calendar sync`
3. **Expiration:** pick the longest option you're comfortable with. When it runs out, you make a new one (see "When the token expires" below).
4. **Repository access:** choose **Only select repositories**, then pick `calendar-data`.
5. **Permissions → Repository permissions → Contents:** set to **Read and write**.
6. Click **Generate token** and copy it. It starts with `github_pat_`. GitHub shows it only once, so save it in your password manager.

## 4. Connect each device

1. Open **szarette.github.io/calendar/**.
2. Click **Set up sync** at the bottom right of the header (or go to **Customize → Data**).
3. Paste the token and click **Connect GitHub**.
4. Do the same on your phone. To install it like an app:
   - **iPhone:** in Safari, tap **Share → Add to Home Screen**.
   - **Android:** in Chrome, tap **⋮ → Install app**.

The first device to connect uploads what it has. Every device after that loads your calendar from GitHub.

## Good to know

- **Timing.** Changes save about 1.5 seconds after you stop editing. Other devices pick them up within 45 seconds, or right away when you switch back to the app.
- **Editing on two devices at once is fine.** Both sets of changes are merged, and deletions stay deleted.
- **Offline.** The app keeps working without a connection and syncs when you're back online.
- **History.** Every save is a commit in `calendar-data`, so you can see or restore any earlier version from the repo's history.
- **Photos.** Header photos are resized, then saved in `calendar-data/photos`.

## When the token expires

The header will say the GitHub token stopped working. Make a new token (step 3), then on each device go to **Customize → Data**, click **Disconnect this device**, paste the new token, and click **Connect GitHub**.

## Moving data from the old calendar

Export a JSON backup from your old calendar. Then in this app, go to **Customize → Data → Import backup** and choose that file.

## Updating the app later

Upload the new `index.html` to the `calendar` repo (**Add file → Upload files**) and commit. Your data lives in `calendar-data`, so it isn't affected.
