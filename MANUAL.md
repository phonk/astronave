# astronave: manual

*two voices, eight stages, no map*

astronave is a two-voice synth that runs in a browser, in the spirit of the Buchla Music Easel. If you only want to make sound, read [The first five minutes](#the-first-five-minutes) and come back when something puzzles you. The rest covers every control.

[Versione italiana](MANUALE.md)

- [The first five minutes](#the-first-five-minutes)
- [How it is put together](#how-it-is-put-together)
- [Controls in general](#controls-in-general)
- [The header: start, rec, scenes, views, dice](#the-header)
- [Pulser](#pulser)
- [Sequencer](#sequencer)
- [Synth A and Synth B](#synth-a-and-synth-b)
- [Output: tape, cistern, master](#output)
- [Random and mod](#random-and-mod)
- [MARF](#marf)
- [Patch](#patch)
- [Keyboard, scale and arpeggio](#keyboard-scale-and-arpeggio)
- [Traces view](#traces-view)
- [Surface view](#surface-view)
- [Scenes](#scenes)
- [Recording](#recording)
- [Computer keyboard and MIDI](#computer-keyboard-and-midi)
- [On a phone](#on-a-phone)
- [Things to try](#things-to-try)
- [When there is no sound](#when-there-is-no-sound)

## The first five minutes

1. Press **start**. Nothing sounds until you do: browsers do not let a page make sound before you touch it.
2. The scene that opens, *slow comet*, plays by itself. Listen for a moment.
3. Press a key on the keyboard at the bottom. The voices follow the note. Slide your finger up and down inside the key: that position is **Touch**, and it changes the sound if a scene uses it.
4. Open the scene list at the top and try a few. Then press **dice** for a random one.
5. Move **folds** on Synth A. It changes the tone more than any other slider.
6. Load **Init** when you want to start from silence and build a sound yourself.

## How it is put together

Two voices, **Synth A** and **Synth B**. Each one is an oscillator, a wavefolder and a low pass gate. They go to a tape echo and a reverb, then out.

Around them, the things that make them move:

- the **pulser**, a clock that hits the voices;
- the **sequencer**, five steps of a value;
- **random**, a new value at each pulse;
- **mod**, a slow or fast oscillator;
- the **MARF**, eight stages with two levels each, that walk through time;
- **Touch**, where your finger is on a key;
- **cross**, each voice heard by the other.

By default none of these is connected to anything. The **patch** matrix decides which one moves what, and by how much. A scene stores all of it: the sliders, the MARF and the patch.

## Controls in general

- **Sliders**: drag along the line. Double-click to go back to the default. With the keyboard, arrow keys move a focused slider; hold shift for bigger steps.
- **Switches** are words with a small ring in front. A filled ring is on. A row of them is a choice of one.
- **Undo and redo** are the two curved arrows in the header. They step back through your last changes, scene loads included.
- The line under the title shows what you are changing and its value while you move something.

## The header

- **start** turns the sound on and off. It reads **on** while it is running.
- **rec** records what you play. See [Recording](#recording).
- **The scene list**, with arrows for previous and next, and next to it the icons: save as new, rename, overwrite, delete, export, import. See [Scenes](#scenes).
- **panel, traces, surface** are the three views of the same instrument. The app remembers the last one you used.
- **dice** makes a random scene. The four words next to it choose what kind:
  - **rhythm**: short notes on the pulser;
  - **drone**: long low tones that move slowly;
  - **cross**: the two voices bending each other hard;
  - **rain**: fast, short notes at uneven times.

## Pulser

The pulser is the instrument's clock.

- **rate**: 0.25 to 20 pulses per second.
- **wobble**: how much the random value pushes the rate around. At zero the pulser is steady.
- **mode**:
  - **free**: it ticks at its rate;
  - **marf**: it fires once each time the MARF enters a stage that has *pulse* on, so the MARF's timing becomes the rhythm;
  - **burst**: each such stage sets off four quick pulses at the pulser's rate.
- **run** starts and stops it. **pulse** fires one pulse by hand.

Each pulse does several things at once: it hits the voices that are set to be hit by the pulser, steps the sequencer (if the sequencer follows the pulser), draws a new random value, and steps the arpeggio.

## Sequencer

Five steps. Each step is a value between 0 and 1, set with its vertical slider. The small light above shows the step that is playing.

- **1 to 5** under the sliders switch each step on or off. A step that is off is a rest: the voices hit by the pulser stay silent on it.
- **len**: how many steps are used, from 1 to 5.
- **step**: what moves it forward.
  - **pulser**: every pulse;
  - **keys**: every key you press;
  - **marf**: every MARF stage with *pulse* on.
- **in scale**: when the sequencer (or anything else) moves a voice's pitch through the patch, the result is pulled to the nearest note of the scale.

The sequencer makes no sound and changes nothing until you send it somewhere in the patch. Sent to *pit a* it is a melody; sent to *fld a* it is a pattern of timbre.

## Synth A and Synth B

The two voices are identical. A is amber, B is pink.

**oscillator**

- **pitch**: plus or minus two octaves, in semitones.
- **fine**: plus or minus one semitone, in cents. A few cents between A and B make them beat.
- **shape**: the wave before folding. It moves from sine to triangle to saw to square.
- **folds**: the wavefolder. At zero the wave passes untouched. As you raise it the wave is pushed past its limit and folds back on itself, again and again, and the sound gets brighter and more nasal.
- **bias**: pushes the wave up or down before it folds. With bias at zero both halves of the wave fold the same way and the sound is hollow. Away from zero the two halves fold differently and the tone fills out. It only does something when folds is above zero.
- **glide**: how slowly the pitch slides to a new note.

**gate**

The low pass gate is a filter and an amplifier in one. As a note dies it gets quieter and darker together, the way a struck object does.

- **decay**: how long a hit lasts, 30 milliseconds to 4 seconds.
- **peak**: resonance. High values give the hit a ringing, vocal edge.
- **mode**:
  - **lpg**: the voice sounds only when it is hit;
  - **drone**: the gate stays open and the voice sounds all the time.

**out**

- **level** and **pan**.
- **keys**: **follow** makes the voice follow the note you play; **fixed** keeps it where its pitch slider says.
- **hit by**: **pulser**, **keys** or **both**. A voice hit by keys is silent until you press one.

The small light in the corner of each voice shows its envelope.

## Output

- **tape**: an echo with a little wow. **time** from 50 milliseconds to 1.5 seconds, **feedback** for how many repeats, **send** for how much of the voices goes in.
- **cistern**: a reverb. **size** for the length of the tail, **dark** to take the top off it, **send** for how much goes in.
- **master**: the output volume, with two level lines under it.
- **limiter**: the last thing before the output. It looks 5 milliseconds ahead and turns the level down just before a peak arrives, so nothing goes over −1 dB and nothing clips. A light saturation comes just before it, so loud scenes keep their body and the limiter has little left to do. The number next to it shows how much it is turning down. With the limiter off, loud passages are rounded off by a heavier saturation instead, which is louder and dirtier. The limiter is a setting of the instrument and is not saved in scenes.

## Random and mod

- **random** takes a new value at every pulse.
  - **slew** smooths the jump between one value and the next.
  - **drift** mixes in a slow wandering value that does not wait for the pulser.
- **mod** is an oscillator used for movement.
  - **rate** from 0.05 Hz, one cycle in twenty seconds, to 400 Hz, which is already a sound.
  - **shape**: sine to triangle to saw to square.

Both do nothing until the patch sends them somewhere. The two small curves next to their names show them moving.

## MARF

The MARF is modelled on the Buchla 248, a "multiple arbitrary function generator". Here it has eight stages. Each stage has two levels, **A** and **B**, and a **time**. The MARF goes from stage to stage, and at each moment it puts out its A level and its B level as two separate sources for the patch.

The graph shows the eight stages left to right. The amber line is A, the pink line is B. The stage that is playing is lit.

- **draw a / b** chooses which line you draw. Then drag across the graph to set the levels.
- **run** starts and stops it. **restart** sends it back to the first stage.
- **clock**:
  - **time**: every stage lasts its own time;
  - **pulser**: every stage lasts a number of pulses.
- **speed** stretches or squeezes all the times together, from four times slower to four times faster.
- **keys**:
  - **off**: the keyboard does not touch the MARF;
  - **restart**: every key sends it back to the start;
  - **address**: each key jumps to a stage, so you choose the stages from the keyboard.

Under the graph, one column per stage:

- **time**: drag the number up or down. With the clock on *time* it goes from 30 milliseconds to 4 seconds. With the clock on *pulser* it counts pulses, 1 to 8.
- **ramp**: the level slides from the previous stage to this one over the stage's time. When it is off, the level jumps.
- **pulse**: entering this stage counts as an event. It fires the pulser when the pulser is in *marf* or *burst* mode (and its *run* is on), and steps the sequencer when the sequencer follows the MARF.
- **hold**: the MARF waits on this stage for as long as a key is held.
- **stop**: the MARF halts at the end of this stage until you restart it or address a stage.
- **skip**: the stage is left out.

A few stages with *ramp* on and long times make an envelope or a slow curve. All stages short, no ramp, clock on *pulser*, make a second sequencer with two outputs.

## Patch

The matrix connects the parts of the instrument. Rows are sources, columns are destinations. Every cell is a connection with an amount from minus 100% to plus 100%.

- **Drag a cell up or down** to set the amount. Amber is positive, pink is negative.
- **Double-click** a cell to clear it.

**Sources (rows)**

| row | what it is |
|---|---|
| marf a, marf b | the two levels of the MARF |
| seq | the value of the current sequencer step |
| mod | the mod oscillator |
| rnd | the random value |
| touch | where your finger is on the key |
| cross | the other voice, at audio rate |

**Destinations (columns)**

| column | what it moves | at 100% |
|---|---|---|
| rate | the pulser's rate | three octaves |
| trsp | the pitch of both voices, in scale | one octave |
| pit a, pit b | the pitch of one voice | two octaves |
| fld a, fld b | folds | four folds |
| dec a, dec b | the gate's decay | eight times longer or shorter |
| fm | how much each voice frequency-modulates the other | |
| tape | the echo time | about three times longer or shorter |
| verb | the reverb send | the whole range |
| bia a, bia b | bias | the whole range |

The **cross** row only reaches pitch and folds: with it, B modulates A's pitch or A's folds at audio rate, and the other way round. Small amounts give a rough edge, large ones give noise and bells.

## Keyboard, scale and arpeggio

The keyboard is a row of plates, two octaves from the octave you choose.

- **Touch**: the vertical position of your finger on a plate. Lower is stronger. It sets how hard the note is hit, and it is also the *touch* source in the patch.
- **Root and scale**: the two menus on the left. The root note has an amber dot.
- **scale only**: shows only the notes of the scale, so no plate is out of key.
- **− and +** move the octave.

**Other tunings**

The last group in the scale menu, *other tunings*, holds scales whose notes fall between the keys of a piano:

- **just major**, **just minor**, **pythagorean**: built from simple ratios. Chords and drones in these beat less than in ordinary tuning.
- **harmonics 8-16**: eight notes from the harmonic series of the root.
- **rast**, **bayati**, **saba**, **sikah**: maqam scales with quarter tones.
- **slendro** and **pelog (gamelan)**: approximations, since every gamelan is tuned its own way.

With one of these selected, the keyboard always shows only the notes of the scale, and each key is labelled with the nearest note name and how many cents it is off, like *e−14*. On a MIDI keyboard the keys become the steps of the scale in a row, starting from the root at middle C. *In scale*, the arpeggio and the surface view follow the tuning as they do any other scale.

**arpeggio**

- **arpeggio** on: the notes you hold are played one at a time.
- **hold**: the notes stay after you lift your fingers. Press new notes after letting go and they replace the old ones.
- **up, down, up-down, random, played**: the order.
- **oct**: over how many octaves.
- **step**: a new note every pulse, every two, or every four.

The arpeggio moves with the pulser. If the pulser is stopped it keeps its own time at the pulser's rate, so the **rate** slider is the speed of the arpeggio either way. A voice hit by keys is hit at every step of the arpeggio.

A scene saved with arpeggio and hold on keeps the notes that were held, and plays them as soon as it loads.

## Traces view

The same patch, seen as signals. One lane per source, with its value scrolling from right to left while the sound runs. A source that goes nowhere is faded.

On the right of each lane are its destinations, as tags like *pit b +87*.

- **Drag a tag** up or down to change the amount.
- **Drag it to zero**, or double-click it, to cut the connection.
- **+** lists the places this source does not go yet. Pick one and it starts at +50%.

Under the lanes, the MARF as a timeline. Each stage is as wide as its time. Drag on it to draw levels (the *draw a / b* choice is in the panel view).

## Surface view

A large touch surface made of zones, for playing with all your fingers. Every finger is independent, and sliding from one zone to the next changes note.

Three layouts:

- **touch**: two fans of notes, one per hand, six notes each. A thin outer arc holds the eight MARF stages. Under each palm, a quarter disc that sends Touch and plays nothing. In the middle, a round control for *pulse*, *restart* and *hold*.
- **thunder**: slanted plates after the Buchla 222e, with the same jobs.
- **grid**: three rows of eight notes. Each row is three scale steps above the one under it.

Inside a fan, Touch is the distance from the palm: nearer is stronger. In the other layouts it is the vertical position. A zone lights up more the harder you play it. Where the device reports pressure (a pencil) or the size of the fingertip, that is used instead of the position.

**edit zones** lets you change what each zone does. Tap a zone, then choose:

- **note**: a step of the scale, counted from the root. Minus and plus move it.
- **stage**: jump to a MARF stage, 1 to 8.
- **pulse**: fire the pulser.
- **restart**: restart the MARF.
- **touch**: send Touch only.
- **hold**: switch the arpeggio's hold.
- **off**.

**reset** puts the layout back as it was. Your zone settings are kept in the browser, per layout. They are not part of a scene.

## Scenes

- **Init** is the empty starting point: no pulser, nothing patched, Synth A waiting for a key.
- The other names in the first group are the factory scenes.
- Your own scenes come after them.

The icons next to the list:

- **save as new**: a name is suggested; type over it or press Enter.
- **rename**, **overwrite**, **delete** work on your own scenes. Delete asks twice.
- **export** saves all your scenes to one file. **import** reads such a file back.

When you change something in a loaded scene, *edited* appears next to its name until you save.

Your scenes live in the browser you saved them in. To move them to another browser or device, export and import.

## Recording

**rec** records exactly what comes out of the instrument, as a 24-bit stereo WAV.

- Press it to start. If the sound is off, it turns it on. The button shows the time while it runs.
- Press it again to stop. A line appears with the file's name, length and size, and with **download** (and **share…** where the device offers it). The cross throws the recording away.
- A recording stops by itself at 20 minutes. It takes about 16 MB per minute and stays in memory until you download or discard it.
- The screen stays on while you record, where the browser allows it.

## Computer keyboard and MIDI

- **A W S E D F T G Y H U J K** play one octave, laid out like a piano: the middle row is the white keys, the row above is the black ones.
- **Z** and **X** move the octave down and up.

A MIDI keyboard plays the instrument where the browser has Web MIDI: Chrome, Edge or Firefox on a computer or on Android. Safari and iPhone do not have it.

- Note messages play notes.
- **Velocity** sets how hard the note is hit, and sets Touch.
- **Aftertouch** and the **mod wheel** move Touch while the note is held.

## On a phone

- Held sideways, the whole panel fits one screen, small. Held upright, the sections stack and you scroll, with the keys fixed at the bottom.
- The surface view is best sideways.
- It keeps playing with the screen off, and you can pause it from the lock screen. If the phone cuts the sound anyway, one tap on start or on a key brings it back.

## Things to try

**A bass line that changes by itself.** Load Init. Turn the pulser's *run* on. Set Synth A's *hit by* to pulser and its pitch to −12. In the patch, drag *seq → pit a* up to about +40. Move the five sequencer sliders. Then drag *rnd → fld a* up a little: every note gets a different brightness.

**A drone that breathes.** Load Init. Set both voices to *drone*, raise B's level, detune B's *fine* by a few cents. Raise *folds* on both. Slow the *mod* rate right down and patch *mod → fld a* and *mod → bia b*. Add cistern send.

**The MARF as a rhythm.** Set the pulser's mode to *marf*. Give the eight stages different times by dragging their numbers. Now the pulser fires at the start of every stage, so the pattern of long and short stages is the rhythm. Switch *pulse* off on a stage to leave a gap.

**Play with Touch.** Patch *touch → fld a* at +60. Now where you touch a key decides how bright the note is. In the surface view, a finger resting on one of the touch discs does the same without playing a note.

**Voices that disturb each other.** Raise *fm* in the patch from any slow source, or drag *cross → pit a* to a small amount. Then move B's pitch and listen to A change.

## When there is no sound

- Is the button at the top reading **on**? If it says *start*, press it.
- Is **master** up, and the level of at least one voice?
- A voice set to *hit by keys* is silent until you press a key. A voice set to *hit by pulser* is silent while the pulser's *run* is off.
- A sequencer step switched off is a rest.
- After the screen has been off, or after a phone call, tap start or a key once.
- Is the phone's silent switch on? On iPhone it can mute web pages.
