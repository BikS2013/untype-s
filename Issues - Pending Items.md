# Issues - Pending Items

Register of issues, pending items and discrepancies of the untype deck. Pending items first (most critical on top), completed items after.

## Pending

_None._

## Completed

### Section-divider label collided with its caption under the BikS2013 theme (2026-09-12)

- **Issue:** after switching the deck from the NBG theme (Aptos) to the BikS2013 theme (Avenir Next), the 64 px divider label of the sections "Configuration and moving parts" and "Operating and troubleshooting" wrapped to two lines, because Avenir Next runs wider than Aptos, and its second line overlapped the caption fixed at `top: 700px` (visible on slides 34 and 45).
- **Solution:** in `deck/src/shell-head.html` the `.divider .label` is now anchored by its bottom edge (`bottom: 390px`, `line-height: 1.05`, `text-wrap: balance`) so a two-line label grows upwards; the numeral moved from `top: 360px` to `top: 330px` to leave room, and the caption sits at `top: 712px`. The closing slide (slide 50), which positions its label with an inline `top`, sets `bottom: auto` so it keeps its custom layout. Verified on all six dividers at 1440×900.

### Deck photography was teal-toned, off the BikS2013 palette (2026-09-12)

- **Issue:** the 18 generated photos were prompted with the NBG "muted teal and cream" palette; on the ink-and-copper deck they clashed, and the theme forbids teal or cyan anywhere.
- **Solution:** `deck/images/generate-images.sh` now prompts for charcoal ink, warm copper and amber accents, cream and paper surfaces ("no teal, no blue"); the whole set was regenerated with `image-tool` (Azure OpenAI `gpt-image-2`, high quality, about 100 s per image, three in parallel) and re-encoded with `make-datauris.sh`. The previous teal set remains in git history (commit `0dd55e5`).
