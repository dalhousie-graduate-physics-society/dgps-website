# Dalhousie Graduate Physics Society website

A plain HTML/CSS site with no build step and no dependencies.

| File          | What it is                                   |
|---------------|----------------------------------------------|
| `index.html`  | Home page: intro, about, what we do, contact |
| `events.html` | Upcoming and past events                     |
| `style.css`   | All the styling (colours are set at the top) |

## Viewing it locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Adding an event

In `events.html`, copy one `<li class="event">` block inside the Upcoming list and edit it.
Set `data-date="YYYY-MM-DD"`. Once that date has passed, the event moves to
"Past events" by itself, and events are always sorted by date.

## Before going live

Search the files for `TODO` and `example`:

- [ ] Real contact email in `index.html`
- [ ] The society's own "About us" text
- [ ] Replace the example events in `events.html`

## Changing the header or footer

They're copied into both HTML files, so edit them in both.
