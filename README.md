# Lexicard

English–English vocabulary flashcards with spaced repetition. Lexicard runs in your browser, installs on your phone like an app, works offline, and keeps your words on your own device.

**Open the app:** https://goktug445.github.io/Lexicard/

## Features

- **Flashcards.** The front shows the word, its word class and an example sentence. The back shows an English definition, the way a learner's dictionary would explain it.
- **Swipe to answer.** Swipe right if you knew the word, left if you didn't, up to review it again later today.
- **Smart review schedule.** Lexicard uses FSRS, the scheduling algorithm available in Anki. Each word comes back right before you are likely to forget it, so easy words appear rarely and difficult ones often.
- **Decks.** Group words into decks, study one deck or all of them, and move or delete words in bulk. A word can be in several decks, but only once per deck.
- **Word list.** Collect new words as you meet them, then get definitions, pronunciation (IPA) and three example sentences for all of them at once with Claude.
- **Three example sentences per word,** shown in turn, so you learn the word and not one sentence.
- **Stats.** A study streak, today's reviews, your success rate and a calendar of the last 18 weeks.
- **Day and night themes, offline use and backups.**

## Getting started

1. Open the link above. On Android, open the Chrome menu (**⋮**) and choose **Add to Home screen** (or **Install app**). On a computer, use the install icon in the address bar.
2. Go to **Add word → Word list** and type one word or phrase per box.
3. Press **Get definitions**, then:
   1. **Copy request**.
   2. Paste it into a new chat at [claude.ai](https://claude.ai) (a free account works) and send it.
   3. Copy Claude's whole answer, paste it back into Lexicard and press **Fill in the words**.
   4. Check the entries and press **Save**.

   Up to 30 words per request. If you have your own Claude API key, add it in **Decks → Claude API key** and this becomes a single tap (Anthropic charges your Console account per use).
4. Go to **Study** and start reviewing.

### Answering a card

| Action | Touch | Keyboard |
|---|---|---|
| Flip the card | Tap | Space |
| Knew it | Swipe right | → |
| Didn't know (comes back in a few cards) | Swipe left | ← |
| Review again (comes back later today) | Swipe up | ↑ |

## Your data

- Words are stored in your browser on that device (IndexedDB). They are never uploaded. There is no account, no server and no tracking.
- Each device has its own words. To move them, use **Decks → Backup → Download backup** on one device and **Restore from backup** on the other. Restoring only adds missing words; it never deletes or overwrites anything.
- Clearing your browser's site data deletes your words too, so download a backup now and then.
- An API key, if you add one, stays in that browser and is sent only to Anthropic's API.

## Host your own copy

1. Fork this repository, or create a new public repository and upload the files below.
2. In the repository, go to **Settings → Pages**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, and press **Save**.
3. After a minute or two, your copy is live at `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/`.

| File | Purpose |
|---|---|
| `index.html` | The app |
| `sw.js` | Offline support |
| `manifest.webmanifest` | Lets phones install it as an app |
| `icon-192.png`, `icon-512.png` | App icon |

## How the review schedule works

Lexicard uses FSRS-6 with its published default parameters. Every word has a *stability* (how long you can remember it) and a *difficulty*. A word is shown again when the chance that you still remember it falls to your target, 90% by default (adjustable in **Decks → Study settings**). "Knew it" lengthens the interval, "Review again" counts as a hard recall, and "Didn't know" counts as a lapse. The number of new words per day can be limited (20 by default) so reviews don't pile up.
