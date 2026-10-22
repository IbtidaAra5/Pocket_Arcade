<div align="center">

# 🕹️ Pocket Arcade

**Six tiny games, one tiny page.**

<a href="https://ibtidaara5.github.io/Pocket-Arcade/"><img src="https://img.shields.io/badge/▶_Play_now-7fb7ae?style=for-the-badge&labelColor=2f4858" alt="Play now"></a>

![HTML5](https://img.shields.io/badge/HTML5_Canvas-6b9ac4?style=flat-square&logo=html5&logoColor=white)
![Vanilla JS](https://img.shields.io/badge/Vanilla_JS-7fb7ae?style=flat-square&logo=javascript&logoColor=white)
![No dependencies](https://img.shields.io/badge/dependencies-none-b7a8e0?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-6b9ac4?style=flat-square)

<img width="644" height="402" alt="Game interface dark theme" src="https://github.com/user-attachments/assets/871ea2e9-cd11-48a3-b910-342f1b31c57c" />


</div>

---

## About

Pocket Arcade is a collection of six small games that run in your browser. It is a single HTML file with no libraries, no build step, and nothing to install, so it works on phones, tablets, and computers.

Every game opens with a start screen and a big **▶ Play** button. Your best scores are saved in your browser, and beating one gets you a little confetti.

## The games

| | Game | Goal | Controls |
|---|---|---|---|
| 🐍 | **Snake** | Eat food to grow without hitting the walls or yourself | Arrow keys, `W` `A` `S` `D`, swipe, or on-screen buttons |
| ❌ | **Tic Tac Toe** | Get three in a row. Play the computer or switch to 2 Players | Tap or click a cell |
| 🃏 | **Memory Match** | Find all 8 pairs in as few moves as possible (lower is better) | Tap or click cards |
| 🐹 | **Whack-a-Hamster** | Tap as many hamsters as you can in 20 seconds | Tap or click |
| 🚗 | **Traffic Dodge** | Dodge cars and grab coins on a 3-lane road. +1 per car passed, +3 per coin | `←` `→`, `A` `D`, or tap the left or right side |
| 🔵 | **Bubble Shot** | Aim and shoot. Match 3 or more to pop; bubbles left hanging fall too | Move mouse or finger to aim, click or tap to shoot (or `←` `→` and `Space`) |

**Bubble Shot details:** after 5 shots that pop nothing, a new row drops from the top. If bubbles cross the red dashed line, the game is over. Clear the whole board for a 500-point bonus.

**Tic Tac Toe details:** the computer plays smart but makes a random move about 1 time in 4, so you can win.

## Features

- A start screen with a **▶ Play** button and how-to text for every game
- Best scores for each game, saved in your browser (`localStorage`)
- "New best!" toast with confetti when you beat your record
- Light and dark theme toggle (follows your device by default)
- Sound effects with an on/off switch (generated with the Web Audio API, no audio files)
- Keyboard shortcuts: `1` to `6` open a game from the menu, `Esc` goes back
- Respects the "reduce motion" setting on your device
- Touch, mouse, and keyboard friendly, with sharp rendering on high-DPI screens


## Themes
-Dark Theme     -Light Theme

## Run it

**Easiest:** open `index.html` in any modern browser.

**Or serve it locally:**

```bash
git clone https://github.com/IbtidaAra5/Pocket-Arcade.git
cd Pocket-Arcade
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Play online with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then **Save**.
4. After a minute the arcade is live at `https://<your-username>.github.io/Pocket-Arcade/`.

## How it is built

- **One file:** HTML, CSS, and JavaScript all live in `index.html`.
- **The hub:** a `games` list describes each game (id, name, emoji, description, and a `run` function). The menu and start screens are built from that list.
- **Each game is a function:** it receives a container and a small `api` (`show` for the score, `msg` for the status line, `final` for saving a best score), draws itself, and returns a cleanup function that stops its timers and key listeners when you go back to the menu.
- **Canvas games** (Snake, Traffic Dodge, Bubble Shot) use a fixed-step loop with `setInterval`. The others are built from regular buttons and CSS grids.
- **Tic Tac Toe AI** uses minimax with a small chance of a random move.

## Add your own game

1. Write a function `myGame(container, api)` that builds its UI inside `container`, calls `api.show(score)` as the score changes, calls `api.final(score)` when the game ends, and returns a cleanup function.
2. Add an entry to the `games` array, for example `{id:"mine",name:"My Game",emoji:"🎲",desc:"Short tagline.",run:myGame}`.
3. Add a one-line how-to for it in the `how` object and an accent colour in the `acc` object.

## Project structure

```text
Pocket-Arcade/
├── index.html          # the whole arcade (HTML, CSS, JavaScript)
├── assets/
│   └── preview.svg     # animated preview used in this README
├── LICENSE
└── README.md
```

## Ideas for later

- Pause button and a "difficulty" setting for each game
- different sounds for each game
- More games, such as 2048 or a sliding puzzle
- A shared daily challenge
- Installable as a PWA so it works offline from the home screen

## License

MIT, see [LICENSE](LICENSE). Made by [Ibtida Ara](https://github.com/IbtidaAra5).
