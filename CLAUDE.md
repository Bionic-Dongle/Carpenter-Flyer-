# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static HTML website for Valley Carpentry (tradie business, Eastern Melbourne). No build process, no framework, no package manager. Everything is in `index.html` and `review.html`.

Deploying = `git add`, `git commit`, `git push`. That's it.

## Adding photos to the slideshow

All images live in `Assets/` organised by job folder. To add a new job to the slideshow, add entries to the `projectImages` array in `index.html` (around line 640+):

```js
{ src: 'Assets/Folder Name/filename.JPG', caption: 'Job Label' },
```

The array order controls the display order. Flashiest jobs go first. After editing, commit and push — no other steps.

New image folders must also be `git add`ed explicitly before committing.

## Adding a review to the carousel

Reviews live in the `reviews` array in `index.html` (near the bottom, before the DOMContentLoaded listener):

```js
{
    stars: 5,
    text: "The review text.",
    author: "A. Name, Suburb",
    avatar: "Assets/Reviews/filename.png"  // optional
}
```

If no avatar is provided, the carousel automatically shows a coloured circle with the reviewer's initial. Avatar images go in `Assets/Reviews/`.

## Review submission form

`review.html` is a standalone page sent to customers via text message link. It submits to Formspree endpoint `https://formspree.io/f/mvzlpyoz` which emails the submission. Reviews are then manually added to the `reviews` array above.

## Key owner preferences

- Keep everything centralised — do not send the user off to external apps or services unless unavoidable
- User provides avatar images (AI-generated portraits); Claude inserts them
- Captions in the slideshow are short job-type labels, not specific addresses or client names
