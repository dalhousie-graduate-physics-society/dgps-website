# Editing the website

This guide is for anyone in the society who needs to update the website,
with or without coding experience.

The site lives at https://dalhousie-graduate-physics-society.github.io/dgps-website/.
GitHub hosts it for free from this repository, and any change saved to the `main`
branch goes live automatically within a minute or two.

## Contents

- [What's in here](#whats-in-here)
- [Getting access](#getting-access)
- [The easy way: edit on GitHub](#the-easy-way-edit-on-github)
- [Adding an event](#adding-an-event)
- [Changing other text](#changing-other-text)
- [Editing on your own computer](#editing-on-your-own-computer)
- [Checking the site after a change](#checking-the-site-after-a-change)
- [If something breaks](#if-something-breaks)
- [Handing over to the next exec](#handing-over-to-the-next-exec)

## What's in here

| File          | What it is                                                     |
|---------------|----------------------------------------------------------------|
| `index.html`  | The home page: intro, About us, What we do, Contact            |
| `events.html` | The Events page                                                |
| `style.css`   | How everything looks: colours, fonts, spacing                  |

There's no build step and nothing to install. The files on GitHub are exactly
what visitors get.

## Getting access

You need a free GitHub account (https://github.com/signup). Then ask a current
owner of the [dalhousie-graduate-physics-society](https://github.com/dalhousie-graduate-physics-society)
organization to invite you. Once you accept the invitation (it arrives by email),
you can edit the site.

## The easy way: edit on GitHub

For small changes like adding an event or fixing a typo, you never need to leave the browser.

1. Go to https://github.com/dalhousie-graduate-physics-society/dgps-website
2. Click the file you want to change, for example `events.html`.
3. Click the pencil icon (✏️ "Edit this file") at the top right of the file.
4. Make your change.
5. Click **Commit changes…**, write a short note about what you changed
   (for example "Add March trivia night"), and click **Commit changes** again.

That's it. The site updates within a minute or two. You can watch it go live
in the **Actions** tab: a green check means it's published.

## Adding an event

Open `events.html` and find the list under `<ul class="event-list" id="upcoming">`.
Each event is one block like this:

```html
<li class="event" data-date="2026-11-20">
    <div class="date"><span class="month">Nov</span><span class="day">20</span></div>
    <div>
        <h3>Trivia night</h3>
        <p class="meta">Thursday · 6:00 pm · Dunn Building</p>
        <p>Grab a team and test your knowledge.</p>
    </div>
</li>
```

To add one, copy a whole block (from `<li` to `</li>`), paste it inside the
list, and change:

| Part                      | What to put                                   |
|---------------------------|-----------------------------------------------|
| `data-date="2026-11-20"`  | The date, written as year-month-day           |
| `<span class="month">`    | The month as it should appear: `Nov`          |
| `<span class="day">`      | The day of the month: `20`                    |
| `<h3>`                    | The event's name                              |
| `<p class="meta">`        | Day of the week, time, and place              |
| the last `<p>`            | A sentence or two about it                    |

You don't need to worry about order or old events:

- Events are sorted by date automatically, so paste a new one anywhere in the list.
- Once an event's date has passed, it moves itself to **Past events**.
  Leave old events in; they show what the society has been up to.

To remove an event entirely, delete its whole block from `<li` to `</li>`.

**Check `data-date` carefully.** It's what decides where the event shows up.
It must be in the form `YYYY-MM-DD`, with leading zeros: `2027-03-05`, not `2027-3-5`.

## Changing other text

All the words on the home page are in `index.html`. Find the sentence you want
to change and edit it, leaving the `<tags>` around it alone. For example, in

```html
<p>Email us at <a href="mailto:dgps@example.com">dgps@example.com</a></p>
```

the email address appears twice: once after `mailto:` (where the link goes)
and once as the text people see. Change both.

A few things to know about HTML:

- Text goes between an opening tag like `<p>` and its closing tag `</p>`. Keep them in pairs.
- `<h1>`, `<h2>` and `<h3>` are headings, from biggest to smallest. `<p>` is a paragraph.
- `<a href="...">text</a>` is a link.
- To write a literal `&`, type `&amp;`.
- Lines starting with `<!--` and ending with `-->` are notes for editors. Visitors never see them.

The header (the black bar with the menu) and the footer are copied into both
`index.html` and `events.html`. If you change one, change the other to match.

## Editing on your own computer

For bigger changes it's nicer to work locally and preview before publishing.
You'll need [git](https://git-scm.com/downloads) and a text editor
(VS Code is a good free one).

**First time:** download a copy of the site.

```bash
git clone https://github.com/dalhousie-graduate-physics-society/dgps-website.git
cd dgps-website
```

**Each time you make changes:**

```bash
git pull                     # get everyone else's latest changes first
```

Edit the files, then preview the site (see below). When you're happy, publish:

```bash
git add -A
git commit -m "Short description of what you changed"
git push
```

**Previewing:** double-click `index.html` to open it in your browser, or run
a small local web server from the site's folder:

```bash
python3 -m http.server 8000
```

and open http://localhost:8000. Refresh the browser after each edit. Press
Ctrl-C in the terminal to stop the server.

## Checking the site after a change

After publishing, open the live site and check that:

- the page you changed looks right, and nothing else moved;
- the Home, Events and Contact links still work;
- it looks fine on a phone too.

If a change doesn't appear, wait a minute and refresh. Your browser may be
showing an old copy, so try Ctrl-Shift-R (Cmd-Shift-R on a Mac).

## If something breaks

Don't panic: every past version of the site is saved, so nothing is ever lost.

- **A page looks messed up after your edit:** usually a tag was deleted or left
  unclosed. Compare your change with the version before it: on GitHub, open the
  file and click **History**, then click your change to see exactly what changed.
- **To undo a change:** on GitHub, find it under **Commits** (on the repository's
  front page) and copy the old text back. Or, on your own computer, run
  `git revert <commit id>` and then `git push`.
- **The Actions tab shows a red ✗:** the publish step failed. Click it to see
  why, or just make another small commit to retry.

If you're stuck, ask whoever looked after the site before you.

## Handing over to the next exec

When the executive changes over:

1. Invite the new exec members to the GitHub organization
   (**People → Invite member** on the organization's page).
2. Make at least two people **Owners**, so the site never depends on one person.
3. Point them to this file.
