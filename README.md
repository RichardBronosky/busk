# busk

A tip page for busking, live at <https://bronosky.com/busk/>. Styled after
[brand-bot](https://github.com/RichardBronosky/brand-bot).

| File | What it is |
|---|---|
| `index.html`, `style.css` | Main page: Venmo and Cash App codes. Each one is a link that opens the app on a phone. |
| `print.html` | A printable letter-size sign: one QR code for the main page, with editable messages above and below (`?top=…&bottom=…`). |
| `qr/*.svg` | Codes generated with `qrencode`. |

Regenerate a code:

```sh
qrencode -t SVG -o qr/main.svg -m 2 -s 8 --level=Q 'https://bronosky.com/busk/'
sed -i 's/<svg width="[^"]*" height="[^"]*" /<svg shape-rendering="crispEdges" /' qr/main.svg
```

To check a code, decode a screenshot of the rendered page with `zbarimg`, not the SVG file.
