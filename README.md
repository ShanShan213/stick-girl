# Stick Girl: Colour Quest

Single-file HTML5 canvas game (`index.html`, no dependencies) for two sisters (ages 7 and 4).
Open `index.html` in a browser (or serve the folder over http/https to enable "Add to Home Screen" via
`manifest.webmanifest` + `sw.js` + `icon.svg`). Progress is saved in `localStorage` (key `stickgirl.v1`).

## Story
A grumpy Storm Cloud stole all the colours. Stick Girl frees them by opening glowing gates (quizzes), smashing the
Test Your Might dojo gate, befriending animals, and finally beating the Storm Cloud in a maths duel.

## Controls
| Action | Keyboard | Touch |
|---|---|---|
| Move | ← → / A D | ◀ ▶ |
| Jump (double jump from Lv 2, hold to glide with dragon) | ↑ / W / Space | ⤒ |
| Punch / Kick | Z (or J) / X (or K) | 👊 / 🦶 |
| Throw ninja star | C (or L) | ⭐ |
| Bending special (needs full meter) | V (or U) | ✨ |
| Switch element (Fire/Water/Earth/Air) | Q | 🔄 |
| Talk / befriend / dig / confirm | E or Enter | E |
| Pets & scrolls book | P | 🐾 button |
| Pause / Mute | Esc / M | ⏸ / 🔊 buttons |
Quiz answers: tap/click, or keys 1-4. Stomping on enemies' heads also defeats them.

## Contents (Level 1, ~20,000 px long, about 5 minutes)
* Heroes: 2 editable characters (name, colour, tier `age7` standard / `age4` easy mode: bigger hit window,
  half damage, slower enemies, simpler questions, longer timers). Both saved separately (XP, pets, scrolls...).
* Combat: punch, kick, stars, 4 bending specials with charge meter; enemies: ninjas, star-throwing ninjas,
  hoppers, storm cloudlets. Defeats are "poofs"; no gore. Hazards: gaps, spikes, moving platforms, bouncing spiky balls, springs.
* Progression: XP bar, levels (2 double jump, 3 stronger special, 4 star magnet, 5 triple stars, 6 rainbow aura),
  stars, 3 hearts with friendly respawns (never a game over), checkpoints.
* Quiz gates (maths / reading+spelling / science / mixed): gentle hint + retry, never a game over.
* Test Your Might: break-the-boards sum race (mid-level), and a Street-Fighter-style duel with health bars, combo chain
  (3 right = special), power meter that must stop on the answer number. You can't lose: Stick Girl just gets back up.
* Side quest: Pip the Painter's Colour Catch mini-game (stars, treat, XP).
* Exploration: sky route (Cloud scroll), a bamboo pit nook (panda), buried mound (needs panda), dark cave (owl, Sun scroll),
  swimming pond (dolphin, Rainbow scroll), sky springs (unicorn, Bee scroll), ember cave (dragon, Lightning scroll).
* Pets (6): Ember the Fox (quiz hints), Hoot the Owl (night light), Bamboo the Panda (digging), Splash the Dolphin (swim/leap),
  Sparky the Dragon (glide), Twinkle the Unicorn (rainbow heal). Befriend by choosing their favourite food, feed 🍎 treats
  in the 🐾 book to raise bond (5 levels, stronger powers). Each has a real-animal fact (dragon/unicorn give the real cousin: Komodo dragon/narwhal).
* WebAudio sound effects and a tiny music loop, mute button (saved).

## Editing content
Everything is data near the top of `index.html`:
* `QB.age7.{maths,reading,science}` and `QB.age4.{counting,shapes,colours,letters,sums,animals}`: `Q('question','right',['wrong',...],'hint')`.
* `GATE`: which categories each gate type draws from per tier. `PETS`, `SCROLLS`, `REWARDS`, `ELEMS`: pets, facts, level rewards.
* `buildLevel()`: the level script (helpers `G` ground, `gap`, `FL` platform, `MV` mover, `SP` spikes, `EN` enemies, `GT` gates, `PT` pets, `SC` scrolls).

## Testing
`index.html#selftest` runs a headless smoke test (random play, every gate, boards, duel, catch, pets) and sets the page title to
`SELFTEST OK ...`:
`google-chrome --headless=new --no-sandbox --virtual-time-budget=60000 --dump-dom "file://$PWD/index.html#selftest" | grep -o "<title>.*</title>"`
(`#shot-title`, `#shot-duel`, etc. set up screens for screenshots.)

## Game plan for future levels
1. **Sky Temple (air)**: wind gusts, cloud platforms, bird enemies; Air bending puzzle; new pet: eagle (long-sight, reveals secrets); maths: fractions & times tables boss "Gale Master".
2. **Coral Kingdom (water)**: full swim level, currents, jellyfish hazards; octopus & sea turtle pets; science: oceans & food chains; spelling boss "Squid Sensei".
3. **Ember Mountain (fire)**: lava gaps, rolling boulders, fire-nation ninjas; red panda & salamander pets; science: volcanoes & states of matter.
4. **Earth Dojo (earth)**: caves, digging puzzles, pushable rocks; mole & tortoise pets; maths: area/perimeter, money.
5. **Rainbow Finale**: remix boss rush with a chosen-element duel, plus a free-roam "Pet Park" to train bonds and a story mode credits scene.
Cross-level ideas: tier `age4` letters/phonics/colours-to-words, a sticker book for scrolls, daily star missions, co-op two-player mode, voice-over reading of questions (speechSynthesis), pet outfits bought with stars.

## v2: Idol style, music & element powers
- **Audio** (100% WebAudio synthesis, no samples): chiptune loops for overworld / caves / boss duel (synth-pop hook), level-up & victory jingles, separate Music and SFX volume + mute (title and pause menu).
- **SFX**: boing jump, punch, kick, coin/star, pet bond, quiz right/wrong, hurt (original descending "oof-ish" blip), poof, plus element, shield, smash, douse sounds.
- **Ninja star**: synthesized girl battle cry ("hi-ya!" / "wee-ya!", formant oscillators + whoosh).
- **Idol style** (toggle on title/pause): neon outfit + glow stick, shadow imps, stage lights and idol pose on level-up, *Harmony* light-stick beam finisher, idol chant layer on the boss track.
- **Elements**: Fire = Flame Burst (burns thorns, lights caves); Water = Healing Wave (heal, bubble shield, speed, douses fire walls); Earth = Rock Pillar (platform, smashes crates, stuns); Air = Whirlwind (push, giant jump, glide).

## Stormi, the Level 1 guide (marker `stormi-guide-2026-10-11`)
* Stormi is the family's real dog, drawn in canvas as a cute blue-grey puppy (white chest patch,
  dark eyes, folded rose ears, stocky). No photos are embedded.
* Start of Level 1: she tells the quest in speech bubbles (tap / E / Enter to advance, **Skip** button). She then follows as a
  companion with contextual bubbles (element needed at obstacles, gate hints, side-path tips), Fact Scrolls (10 real dog facts,
  collected in the 🐾 book > Stormi tab), synthesized barks and a tail wag. Tap her or press E (nobody else near) for a pat.
* Bond meter (HUD chip + 🐾 > Stormi tab): grows with gates, scrolls, new pet friends, pats and 🍎 treats. Lv2 secret-path tips +
  2nd quiz clue, Lv3 crosses out a wrong answer + speed cheer, Lv4 helps at the start of each question, Lv5 cheer can give a shield.
  Cheer boost also adds damage in the boss duel. She reappears at the boss and in the end-of-level story.
* Dog name is editable (default Stormi): Choose Heroes screen, Pause menu, or the Stormi tab (`SV.dogName`).


## Puzzle rooms, rescue sprites and Stormi hints (Oct 2026)
* Level 1 now has 6 puzzle rooms: Lever Gate, Crate Steps, Heavy Plate Bridge (crate or Stormi on the plate), Sleepy Shadow Imps (hide in shadows / behind crates, sneak while they snooze), Rescue Bridge (timed bridge + leading sprites) and Echo Trail (crumb trail pattern). Failing a room just respawns you at its start.
* E = interact / grab-push crate / call sprites / pull levers. 💡 button (or H) = lantern hint. Each room ends with a fact scroll plus a gentle logic question. Rescue 2 / 5 / 8 sprites for bonuses.
* Stormi no longer follows you. She pops in from a screen corner only when you seem stuck (30s Few / 20s More, age-4 mode quicker) or near a secret (More mode), with a 60-90s cooldown and 3 (Few) / 6 (More) visits per level. Pause menu or title screen: Stormi hints Off / Few / More.
* Hero cards on the Choose Heroes screen have a Reset button. `#selftest`, `#roomtest` and `#shot-*` never write to localStorage.
* Headless tests: `google-chrome --headless=new --no-sandbox --virtual-time-budget=120000 --dump-dom "file://$PWD/index.html#roomtest" | grep -o "<title>.*</title>"`
