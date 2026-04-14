# Slide Library Add-in — Setup Guide
## Beyond Group · BG Outreach and Communications

---

## What's in this package

| File | Purpose |
|------|---------|
| `taskpane.html` | The add-in UI — connects live to SharePoint |
| `manifest.xml` | Registers the add-in with PowerPoint |
| `SETUP_GUIDE.md` | This file |

Your Azure App is already configured:
- ✅ App ID: `51dfcadf-0efa-4d32-afd6-cdf7fdcc1574`
- ✅ Permissions: Files.Read.All · Sites.Read.All · User.Read
- ✅ SharePoint: `beyondgroupconsulting.sharepoint.com/sites/Unit-Outreach`
- ✅ Slide Library folder structure ready

---

## STEP 1 — Add Redirect URI in Azure (5 min)

You need to tell Azure where the add-in will be hosted.

1. Go to [portal.azure.com](https://portal.azure.com)
2. Search **App registrations** → open **Slide Library Add-in**
3. Click **Authentication** in the left sidebar
4. Click **Add a platform** → choose **Single-page application**
5. Enter your hosted URL (you'll get this in Step 2):
   `https://YOUR-VERCEL-URL.vercel.app`
6. Click **Configure** → **Save**

---

## STEP 2 — Host the files (10 min)

### Option A: Vercel (Recommended — free)

1. Go to [vercel.com](https://vercel.com) → sign up free with your email
2. Click **Add New → Project**
3. Choose **"Deploy without a Git repository"** → drag this folder
4. Your URL will be: `https://slide-library-xxxx.vercel.app`
5. **Copy this URL** — you need it for Steps 1 and 3

### Option B: Netlify (also free)

1. Go to [netlify.com](https://netlify.com) → sign up
2. Drag this folder onto the deploy area
3. Your URL will be: `https://slide-library.netlify.app`

---

## STEP 3 — Update manifest.xml (2 min)

Open `manifest.xml` in Notepad or any text editor.

Use **Find & Replace**:
- Find: `https://YOUR-HOSTED-URL`
- Replace with: `https://YOUR-ACTUAL-VERCEL-URL.vercel.app`

There are **8 places** to replace. Save the file.

---

## STEP 4 — Deploy to your team via M365 Admin (10 min)

This pushes the add-in to everyone automatically — no installs needed.

1. Go to [admin.microsoft.com](https://admin.microsoft.com)
2. Navigate to: **Settings → Integrated Apps**
3. Click **Upload custom apps**
4. Select: **Office Add-in**
5. Upload your updated `manifest.xml`
6. Assign to: **Entire organization** (or specific group)
7. Click **Deploy**

✅ Within **24 hours**, the **"Slide Library"** button appears in PowerPoint's Home ribbon for your entire team.

---

## How your team uses it

```
1. Open PowerPoint → start a client deck
2. Click "Slide Library" in the Home ribbon
3. Pick a theme → Blue / Corporate / Green / Red / Yellow
4. Pick a category → Charts, M&A, Assessment…
5. Browse slides — tap to select, hold to preview
6. Click ⚡ Insert — slides drop into the deck
```

---

## Updating the library (weekly workflow)

To add or update slides — **no code changes needed, ever**:

1. Go to your SharePoint:
   `beyondgroupconsulting.sharepoint.com/sites/Unit-Outreach`
2. Navigate to: **Documents → Slide Library → [Theme folder]**
3. Replace or add `.pptx` files
4. Team members click the **🔄 Sync** button in the add-in
5. New slides appear instantly

---

## Adding a new theme in future

1. Create a new folder inside `Slide Library/` on SharePoint
   (e.g. `Purple`)
2. Upload the 9 `.pptx` files
3. Open `taskpane.html`, find the `THEMES` array near the top
4. Add a new entry:
   ```javascript
   { id: "Purple", label: "Purple", emoji: "🟣", color: "#9333ea", desc: "Purple deliverables template" },
   ```
5. Re-upload `taskpane.html` to Vercel (drag & drop, 30 seconds)
6. Done — no manifest re-deployment needed

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Sign-in popup blocked | Allow popups for your hosted URL in browser settings |
| "Redirect URI mismatch" | Make sure Azure has your exact Vercel URL (Step 1) |
| Add-in doesn't appear in ribbon | Wait 24h after M365 deployment |
| Slides show no thumbnails | Open the .pptx in PowerPoint Online once to generate thumbnails |
| "Files not found" error | Check SharePoint folder names match exactly: Blue, Corporate, Green, Red, Yellow |
| Can't access admin.microsoft.com | You're already admin — use your bgadmin account |

---

## Support

Add-in built for: **BG - Outreach and Communications**
SharePoint site: `beyondgroupconsulting.sharepoint.com/sites/Unit-Outreach`
Azure App: `Slide Library Add-in` (51dfcadf-...)
