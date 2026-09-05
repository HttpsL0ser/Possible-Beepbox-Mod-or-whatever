# froupbox – hover & polish patch

A small, drop-in usability/visual patch for [froupbox](https://github.com/froupbox/froupbox), the BeepBox-family music tracker (froupbox → Slarmoo's Box → Ultrabox → JummBox → [BeepBox](https://beepbox.co)).

This isn't a fork of the whole project — froupbox already includes a lot of large sample-audio assets that don't need to be duplicated here. It's just the two files that were actually changed, so it's easy to drop into an existing froupbox checkout or open as a small PR.

## What changed

Every change is additive — no layout, feature, or behavior logic was touched.

1. **Buttons get a hover state.** Previously every `<button>` (play/pause, export, copy/paste instrument, zoom, etc.) only reacted on `:focus`. They now lighten on `:hover` too, using the theme's own `uiWidgetFocus` color, so it looks correct in every color theme, not just the default one.
2. **Dropdowns (`<select>`) get a matching hover state**, same reasoning as buttons.
3. **select2-powered menus** (instrument type, scale, key, theme picker, etc.) get the same hover treatment for consistency.
4. **All of the above fade smoothly** (`transition: background-color 0.15s ease-in-out`) instead of snapping instantly, so the interface feels more responsive.
5. **The custom scrollbar thumb** (thin-scrollbar mode) gets slightly rounded corners and lightens on hover, matching the rounded look buttons and dropdowns already have.

Net effect: on every screen of the editor, you can tell what's clickable before you click it.

## Files

- `editor/style.ts` — the TypeScript source. Replace this in your froupbox checkout and rebuild (see below) if you maintain the project from source.
- `dist/beepbox_editor.min.js` — the same fix already applied to a built bundle. Replace this file directly in an existing `dist/` folder and refresh the page — no build step required.

## Applying this patch

**If you just want to see it live:**
1. Copy `dist/beepbox_editor.min.js` into your froupbox `dist/` folder, overwriting the existing file.
2. Refresh the page.

**If you build from source:**
1. Copy `editor/style.ts` into your froupbox `editor/` folder, overwriting the existing file.
2. Rebuild:
   ```sh
   npm install
   npm run build
   ```

## Credit

All original code, design, and assets belong to the [froupbox](https://github.com/froupbox/froupbox) project and the chain of BeepBox mods it's built on. This patch only adds a handful of CSS rules on top of `editor/style.ts`; see [LICENSE](./LICENSE) (MIT, inherited from froupbox) for terms.
