# Rhythm-Drum
A drum practice tool that turns a song's drum sheet into a rhythm game. Load a Guitar Pro 7+ file (`.gp`) and the drum track scrolls toward a hit line like Guitar Hero or Clone Hero, while you play along on a real kit. It doesn't judge what you hit, so there's no HP drain and no failing the map.

## Why I made this

I've always loved rhythm games and music. When I practiced instruments, I used a lot of MIDI files. I also tried playing Clone Hero drums with my keyboard, which didn't turn out so great, and I couldn't hook it up to an e-kit because I only had an acoustic kit.

Then it clicked: drum sheet music is a lot like how a rhythm game works. What if I could play along to a song like a rhythm game, without the fear of HP drain or failing the map?

I made this project with Clause Sonnet 5.5 just to test it out, and I think it turned out pretty great.

## Features

- Falling-notes view with one lane per drum piece (hi-hat, snare, toms, crash, ride) and the kick as a full-width bar
- Speed control (40-120%), bar range with looping, and a 4-beat count-in
- Metronome with an accented first beat, following the song's time signature and tempo changes
- Play-along backing tracks: pick any other track in the file (guitars, bass, keys...) and set per-track and overall volume
- Bring your own SoundFont (`.sf2`): loaded from your device and remembered in your browser. Without one, backing tracks use a basic built-in tone
- Drum sound: built-in synth or the SoundFont's drum kit, with its own volume

No build step, no dependencies, no server: everything runs in the browser from one `index.html`.

## Usage

Open `Rhythm-Drum.html` in a modern browser (Chrome, Edge, Firefox, Safari). Some browsers restrict storage on `file://` pages, so serving it is more reliable:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

1. Click **Open .gp file** and choose a Guitar Pro 7+ file.
2. Optional: open **Play-along tracks & sounds**, load an `.sf2` SoundFont, and tick the tracks you want to hear.
3. Press **Play**.

Your files and SoundFont stay on your device. Nothing is uploaded.

## Hosting on GitHub Pages

Settings -> Pages -> deploy from the `main` branch, root folder. The site is then served from `https://<user>.github.io/<repo>/`.

## Limitations

- Guitar Pro 7+ (`.gp`) only; older `.gp5` / `.gpx` files are not supported
- Repeat signs are not expanded; each bar plays once, in order
- Bends, slides, vibrato and automation are ignored
- Hi-hat and cymbal variations share a lane
- Not tested across many files yet; lane mapping may need tweaks for unusual drum kits

## Ideas

- Strict mode: keyboard or Web MIDI e-kit input with timing windows and scoring
- Repeat support
- Per-track instrument override
- Separate metronome volume

## Notes on content

Guitar Pro tabs are transcriptions of copyrighted songs. Please don't commit tab files or SoundFonts to this repository; load your own locally. SoundFonts have their own licenses (for example, GeneralUser GS is free to use but asks that you link to its author's site rather than its download files).

