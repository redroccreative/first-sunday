# First Sunday

A single-file web app that helps someone find a church to visit this Sunday,
and pairs them with a friendly face so they do not have to walk in alone.

Built for the coders4christ challenge.

## What it does

You enter your zip code or general location, answer five quick questions about
what you're looking for (things like music style, meeting space, and
language), and get a ranked list of nearby churches that fit. Pick one, and
you can request to be met by a greeter when you arrive, someone who will be
watching for you and can walk you in. From there you get a simple Sunday plan
screen with the service time, address, parking, and what to expect.

## The "Visit with Someone" differentiator

Most church-finder tools stop at a list of addresses and service times.
First Sunday's whole reason for existing is the step after that: showing up
somewhere new alone is the actual barrier for a lot of people, not finding
the church's website. So the app lets you request a greeter, a real point of
contact who knows you're coming and will look for you, turning a cold walk-in
into an expected guest.

## Demo-persona honesty

The greeters in this build are fictional demo personas, not real people at
real churches. Every greeter card carries an unmissable label,
`Demo persona, not a real member`, and nothing in the app implies these are
real staff or members. This is a hard design rule, not an oversight: the app
also ships a Report button and a safety page so a real deployment would have
a clear path for correcting or flagging anything that reads as misleading.

## Data sourcing rules

Every fact about every church (service times, address, dress code, music
style, meeting space, language options) came only from that church's own
website. No Yelp, no Google reviews, no blog roundups, no denominational
directories were used as the source of any fact about a church. Where a
church's site did not state something, the field is recorded as unknown
rather than guessed. Full sourcing notes and the exact research method are in
[`data/SOURCES.md`](data/SOURCES.md).

## How to run it

This is a single self-contained HTML file. No build step, no server, no
install.

1. Download or clone this repo.
2. Open `index.html` directly in a browser.

That's it. All data (churches, greeters) is embedded in the page and also
available separately in `data/` as the documented source of truth.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire app: markup, styles, and logic in one file |
| `DESIGN.md` | Locked design record: layout, copy rules, and decisions |
| `PERSONA.md` | The target user this app was designed for |
| `data/churches.json` | Church data, sourced from each church's own site |
| `data/greeters.json` | Demo greeter personas |
| `data/SOURCES.md` | Exactly how and when each fact was sourced |
| `design/mockups/` | Design exploration mockups |
