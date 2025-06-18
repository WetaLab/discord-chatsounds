# MetaSounds Usage Guide

MetaSounds is a Discord bot that converts messages into sounds.

---

## Table of Contents

- [Commands](#commands)  
- [Search Command Advanced Features](#search-command-advanced-features)  
- [Sound Effect Modifiers](#sound-effect-modifiers)  

---

## Commands

| Command        | Description                                                                 | Usage                    |
|----------------|-----------------------------------------------------------------------------|--------------------------|
| `$enable`      | Enable the bot to listen for your messages and convert them into sounds     | `$enable`                |
| `$disable`     | Disable the bot from listening for your messages (chat sounds won't trigger)| `$disable`               |
| `$search`      | Search for sounds in the sound database                                     | `$search [query/category]`|
| `$details`     | View detailed information about a sound                                     | `$details [sound_name]`  |
| `$stop`        | Stop any sound that is currently playing                                    | `$stop`                  |

---

## Search Command Advanced Features

The `$search` command supports flexible querying and browsing of the sound database:

- `$search [category]`  
  Lists all sounds within a specific **category**.

- `$search {prefix}`  
  Searches for categories that **start with** the given prefix inside curly braces `{}`.  
  Example: `$search {asd}` will find all categories starting with "asd".

- `$search {*}`  
  Lists **all available categories** in the sound database.

---

## Sound Effect Modifiers

Modifiers can be appended **after** the sound effect string to customize playback. Multiple modifiers can be chained together.

| Modifier                   | Description                                                       | Example                         |
|----------------------------|-------------------------------------------------------------------|--------------------------------|
| `#x`                      | Select the x-th variant of a sound if multiple are available      | `sound#2`                      |
| `=x`                      | Interrupt the sound after **x seconds**                           | `sound=5`                      |
| `%x`                      | Set the pitch of the audio to x                                   | `sound%2`                      |
| `^x`                      | Set the volume of the audio to x                                  | `sound^2`                      |
| `--x`                     | Interrupt after **x%** of the sound has been played               | `sound--50`                    |
| `%%x.x`                   | pitch(x) to pitch(x) fade                                         | `sound%%2.5`                   |
| `^^x.x`                   | volume(x) to volume(x) fade                                       | `sound^^2.5`                   |
| `:select(index)`          | Same as `#x`, selects the variant by index                        | `sound:select(3)`              |
| `:speed(speed)`           | Change playback speed (e.g., 1.5 for 1.5x speed)                  | `sound:speed(1.2)`             |
| `:pitch(semitones)`       | Change pitch by semitones (positive or negative)                  | `sound:pitch(3)`               |
| `:echo(delay, decay)`     | Apply echo effect with delay (ms) and decay factor (0-1)          | `sound:echo(500,0.6)`          |
| `:lfopitch(freq, semi)`   | Apply LFO (low frequency oscillator) to pitch                     | `sound:lfopitch(5,2)`          |
| `:lfovolume(freq, depth)` | Apply LFO to volume                                               | `sound:lfovolume(2,0.3)`       |
| `:lowpass(ratio)`         | Apply low-pass filter with given ratio (0-1)                      | `sound:lowpass(.5)`            |
| `:highpass(ratio)`        | Apply high-pass filter with given ratio (0-1)                     | `sound:highpass(0.8)`          |
| `:reverse()`              | Play the sound in reverse                                         | `sound:reverse()`              |
| `:bass(intensity)`        | Apply bass boost (0-1)                                            | `sound:bass(0.5)`              |
---

## Example Usage

- Enable chat sounds:  
```

$enable

```

- Search for all sounds in the "music" category:  
```

$search [music]

```

- List all categories starting with "game":  
```

$search {game}

```

- List all categories:  
```

$search {*}

```

- Play the 2nd variant of "alert" sound at 1.5x speed and pitch shifted up 2 semitones:  
```

alert#2:speed(1.5):pitch(2)

```

- Stop currently playing sounds:  
```

$stop
```
