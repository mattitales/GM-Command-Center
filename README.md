# GM Command Center v3.1 — GitHub Pages / PWA

A deployment package based on **v3**. The library, modes, filters, editor, audit, and Session Kit are retained. This update adds installability, offline app-shell caching, and **full backup/restore** (library + Session Kit).

## First: protect your existing changes

1. Open the **old v3 file in the same browser and location** you used previously.
2. Click **Export backup**. This older backup protects the library (but not the Session Kit).
3. If you have a populated kit, keep the old HTML file/browser profile available until it is migrated. The new full export includes both library and kit after you load them into v3.1; note that files hosted at another address cannot read the old file's browser storage automatically.
4. After deploying v3.1, open the hosted app and choose **Import backup**. Select your original library JSON. If you still have kit entries in the old v3, re-add them to the hosted app, then use **Export full backup** to protect both.

**Important:** Browsers isolate local storage by website address. Moving to GitHub Pages does not automatically move existing edits. Export / import is required. GitHub Pages does not provide database sync. PC and phone remain separate until a future cloud-sync feature.

## Publish using GitHub's web interface

1. Sign in at https://github.com and create a **new public repository** called `GM-Command-Center` (or another unique name). You do not need to initialize it with a README.
2. In the repository, select **Add file → Upload files**. Upload the **contents of this folder** at the repository root: `index.html`, `manifest.webmanifest`, `service-worker.js`, `README.md`, and both PNGs under `icons/`. Keep the folder structure. If GitHub's web upload flattens the folder, use the GitHub web editor to create `icons/icon-192.png` and `icons/icon-512.png` paths or use the ZIP with a local Git client.
3. Commit the upload.
4. Go to **Settings → Pages**. Under **Build and deployment**, select **Deploy from a branch**, then choose **main** and **/(root)**. Save.
5. GitHub will display the published URL on the Pages settings screen. It typically follows `https://USERNAME.github.io/REPOSITORY/`, but use the address GitHub actually shows.
6. Open that URL on your PC. **Import backup** from v3. Verify a resource you edited appears.
7. On Chrome/Edge desktop, use the **Install app** button when offered, or the browser's menu **Install GM Command Center** / **Apps → Install this site as an app**. You can also bookmark it or pin the installed app to the taskbar.
8. On Android Chrome, open the same URL and choose **Install app** / **Add to Home screen** from the browser menu. Import the backup separately if you want your phone to have the same catalog.

## Updating after deployment

Upload and commit updated app files in the repository. The installed PWA loads the updated page when it is next opened online. Existing local catalog data is retained in that browser's storage. Export a backup before upgrades.

## Offline use

Visit the published site once while online. The service worker caches the app shell. After the service worker installs, the app itself is available offline, including your locally saved catalog and editing. External resources linked in Google Drive and other websites still require internet unless separately cached by those services.

## Storage / backup limitations

- Data stays in each browser/profile/device via localStorage.
- Deleting site data, switching browsers, or changing the hosted domain can lose access to that local data.
- **Export full backup** creates a JSON file containing the catalog and pinned Session Kit IDs.
- **Import backup** supports old library-only JSON files and new full backup JSON files. Imports replace current catalog data; export first.
- A local file opened with `file://` cannot install the PWA or activate the offline worker. Serve over GitHub Pages (HTTPS) or local `http://localhost` for testing.
