# MamaOko

Japanese Okonomiyaki by Khmer — single-page menu site (GitHub Pages).

Phone-first. A sticky nav bar holds the brand plus call and Telegram shortcuts,
the menu is a 2x2 grid of dish tiles, and tapping a tile opens a bottom-sheet
pop-up with the full-size photos, both flavors, all prices and order buttons.
All copy is bilingual English + Khmer (Japanese names shown as accents).

## Menu

Four main dishes:

| Dish | Flavors | Sizes & prices |
|---|---|---|
| Steam-Fry Japanese Noodle | beef, seafood | One size — $3.00 |
| Mama Oko Special | beef, seafood | S $3.00 · M $4.50 · L $6.00 |
| Mama Oko Okonomiyaki | beef, seafood | S $3.50 · M $5.00 · L $6.50 |
| Mama Oko Salad | one | Big — $1.50 |

Both flavors of a dish share the same price.

The pop-up markup lives in the hidden `<div>` blocks at the bottom of
`index.html` (`#d-noodle`, `#d-special`, `#d-okonomiyaki`, `#d-salad`); each dish
tile references one by `data-dish`. To change a price or description, edit the
tile and its matching detail block. No build step, no dependencies.

## Ordering

Grab is the delivery channel — the store link appears twice in `index.html`
(the Delivery section button, and the `orderBtn` string in the script that
builds the pop-up buttons). Update both if the Grab store link ever changes.
Telegram `@Sokhan_7` handles bulk orders.

## Images

```
images/
  dishes/      web-optimized JPEGs used by index.html (800px, ~200 KB each)
  originals/   full-resolution source artwork, kept for reprints/edits
  brand/       Grab logo + mobile operator logos used on the buttons
  archive/     superseded assets, not referenced by the site
```

To add or replace a dish photo, drop the full-size file in `images/originals/`
and generate the web copy with:

```sh
sips -Z 800 -s format jpeg -s formatOptions 62 \
  images/originals/<name>.jpg --out images/dishes/<name>.jpg
```

Photos are square (1:1) with the dish name and flavor already set into the
artwork, so the page renders them uncropped.
