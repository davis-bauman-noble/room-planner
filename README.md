# Room Planner

A top-down, true-to-scale room furniture planner in a single `index.html` — no frameworks, no build step, no network requests. Works on iPhone Safari (touch) and desktop (mouse/keyboard).

## Features

- **Fixed room:** 123.5″ × 155″.
  - East (right) wall: 62″ double door starting 27″ from the top wall, opening inward. The **top** leaf must be able to open: anything in its swing turns red. The **bottom** leaf is optional: blocking it turns its swing amber and isn't counted as a conflict.
  - West (left) wall: 60″ window starting 28″ from the top wall, then a 45″ mirror 10″ below it.
- **Fixed furniture:** bed 56×80, nightstand 16×23, desk 47×19, dresser 64×18 (width × depth, inches). You can't edit the room or the furniture in the app; change them in `index.html` (`ROOM_W`/`ROOM_L`, `FIXED_ITEMS`, `defaultOpenings()`).
- **Arranging:** drag an item to move it; it snaps to a 1″ grid, the walls, and other items. When an item is selected, a round blue button appears on it to rotate it 90°. On desktop, the arrow keys nudge an item (Shift = 6″), R rotates it, and Esc deselects.
- **Checks:** an item turns red when it overlaps another item, a wall, or the top door's swing. When you select an item, the plan shows its clearance to the nearest wall (blue) or item (orange) on each side.
- **Controls:** the layouts button, undo, redo, and PNG export are along the bottom left; zoom and fit are at the bottom right. Pinch-zoom and two-finger pan on phone; wheel-zoom and drag-pan on desktop.
- **Layouts:** the layouts button opens a list where you can switch, add, duplicate, rename, delete, export, and import layouts. Everything autosaves to `localStorage`.

## Publish on GitHub Pages

1. Create a new repository on GitHub (e.g. `room-planner`). It can be public, or private if your plan includes Pages for private repos.
2. Upload `index.html` (and this README) to the root of the default branch. Either use **Add file → Upload files** on GitHub, or run:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Room planner"
   git branch -M main
   git remote add origin https://github.com/<you>/room-planner.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, **Branch** to `main`, folder `/ (root)`, then **Save**.
4. After a minute the site is live at `https://<you>.github.io/room-planner/`.
5. On iPhone, open that URL in Safari and tap **Share → Add to Home Screen** for a full-screen, app-like launcher.

## Moving layouts between devices

Saved layouts live in each browser's local storage. They don't sync on their own, and each origin has its own storage, so a local file and the GitHub Pages URL don't share data. To move layouts:

- **Layouts → Export layout (.json)** (or **Export all**). On iPhone this opens the share sheet, so you can AirDrop or Message the file.
- On the other device: **Layouts → Import .json…**. Imported layouts are added alongside your existing ones and never overwrite them.

## Running locally

Open `index.html` directly in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```
