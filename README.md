# Social post builder

A static page that builds a 1080 × 1350 social post from the Figma frame "Full bleed date" and downloads it as a JPEG. Everything runs in the browser, so no images are uploaded anywhere.

## Video

The photo templates also accept a video. It plays muted on a loop in the preview, and **Download video** plays it once from the start while recording the post, with the video's sound. Export takes as long as the video (capped at 60 seconds), and the tab must stay open and visible while it runs. Browsers that can record MP4 (current Chrome, Edge and Safari) save `.mp4`; others save `.webm`, which Instagram won't accept.

## Formats

The Format toggle switches between **Post** (1080 × 1350, the size the Figma frames were designed at) and **Story** (1080 × 1920). Both use the same 100px padding at the top and bottom. Photos fill the extra height, and the Message template's leaves are spaced out to fill the taller frame without being resized. Both sizes are set in `FORMATS` in `index.html`.

## Templates

Pick one from the Template dropdown. Each one is defined in the `TEMPLATES` object in `index.html`.

**Full bleed photo** (Figma frame "Full bleed date")
1. Photo (uploaded, fills the frame, with zoom and position controls)
2. Gradient (fixed)
3. Logo (`assets/logo.svg`, fixed)
4. Heading (Wilden 80px, #ffa74f)
5. Summary (PT Serif 40px, #f7dfba)
6. Call to action (Wilden 40px, #f0531c)

**Split photo** (Figma frame "split")
1. Green background (#2e4b3c, fixed)
2. Photo (uploaded, clipped to the wavy shape from Figma, with zoom and position controls). The shape is `assets/split-mask.png`, the alpha channel of Figma's "Union" layer.
3. Heading (Wilden 70px, #ffa74f)
4. Summary (PT Serif 40px, #f7dfba)
5. Call to action (Wilden 40px, #f0531c)

**Message** (Figma frame "Message")
1. Green background (#2e4b3c, fixed)
2. Heading (Wilden 80px, #fbeed9, centred in the frame)
3. Call to action (Wilden 50px, #fbeed9)
4. Leaves (`assets/leaves.svg`, fixed)

## Adding a template

Add an entry to `TEMPLATES` with its `fields`, text `styles`, a `drawBackground()` (and optional `drawForeground()`), and a `place()` function that returns the top of each text block. Then add a matching `<option>` to the Template dropdown.

## Run locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173. Opening `index.html` directly from disk will not load the fonts reliably.

## Host on GitHub Pages

1. Push this folder to a GitHub repository.
2. In the repository, go to Settings → Pages.
3. Set Source to "Deploy from a branch", choose `main` and `/ (root)`, then save.
4. The tool will be live at `https://<org>.github.io/<repo>/` after a minute or so.

## Changing the design

All sizes, colours and spacing for each template sit in `TEMPLATES` at the top of the `<script>` in `index.html`.

## Font licence

`fonts/wilden-regular.woff` is served publicly on GitHub Pages. Check the Wilden licence covers web embedding before publishing, or use a private repository with Pages restricted to your organisation.
