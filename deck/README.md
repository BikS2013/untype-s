# untype technical deck

A 50-slide HTML presentation about untype (what it is, how it works, installation, configuration, operation), built on the NBG design system skill and decorated with photorealistic images generated for this purpose.

## Deliverables

| File | Purpose |
|---|---|
| `untype-deck.html` | The self-contained deck (all images embedded). Open in any browser; arrow keys or the on-screen buttons navigate. Right-click for the in-deck menu (edit text, resize shapes, export to PDF, save an edited copy). |
| `untype-deck.pdf` | One page per slide, exported from the HTML with the skill's exporter. |
| `untype-deck.rebuild.mjs` | Re-embeds the newest version of the in-deck editing tools after the nbg-design skill is updated (`node untype-deck.rebuild.mjs --check` reports, without `--check` it rebuilds and re-exports the PDF). |

## Sources and how to rebuild

- `src/shell-head.html`, `src/slides.html`, `src/shell-tail.html`: the deck source, authored with `{{TOKEN}}` image placeholders.
- `images/generate-images.sh`: generates the photo set with `image-tool` (Azure OpenAI `gpt-image-2`). Existing PNGs are skipped, so delete a file to regenerate it. Prompts live in the script.
- `images/make-datauris.sh`: converts every PNG to a 1600 px JPEG and writes `assets/<name>.datauri.txt`, the form the embedder consumes. `assets/logo-*.datauri.txt` are copied from the skill.
- `build.sh`: concatenates the sources, embeds the assets, inlines the NBG deck menu, runs the strict verifier, writes the rebuild script and exports the PDF. Requires the `nbg-design` plugin (path overridable with `NBG_DESIGN_SKILL`) and Chrome for the PDF.

```
./images/generate-images.sh   # only when images must be (re)generated
./images/make-datauris.sh
./build.sh                    # or ./build.sh --no-pdf
```

`untype-deck.src.html` is an intermediate file produced by the build.
