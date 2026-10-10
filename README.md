# Social post builder

A static page that builds a 1080 × 1350 social post from the Figma frame "Full bleed date" and downloads it as a JPEG. Everything runs in the browser, so no images are uploaded anywhere.

## Layers

1. Photo (uploaded, fills the frame, with zoom and position controls)
2. Gradient (fixed)
3. Logo (`assets/logo.svg`, fixed)
4. Heading (Wilden 80px, #ffa74f)
5. Summary (PT Serif 40px, #f7dfba)
6. Call to action (Wilden 40px, #f0531c)

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

All sizes, colours and spacing sit in the constants at the top of the `<script>` in `index.html`.

## Font licence

`fonts/wilden-regular.woff` is served publicly on GitHub Pages. Check the Wilden licence covers web embedding before publishing, or use a private repository with Pages restricted to your organisation.
