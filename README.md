# `kdzxy`

<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KDZXY LCD</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background: #050807;
        font-family: monospace;
    }

    .lcd {
        width: min(900px, 94vw);
        padding: 35px;
        border: 2px solid #18352a;
        border-radius: 14px;
        background:
            radial-gradient(circle at center, #0b1712 0%, #050807 75%);
        box-shadow:
            0 0 30px rgba(0, 255, 120, 0.05),
            inset 0 0 30px rgba(0, 255, 120, 0.03);
        overflow: hidden;
    }

    .screen {
        display: grid;
        grid-template-columns: repeat(45, 1fr);
        grid-template-rows: repeat(18, 1fr);
        gap: 5px;
        aspect-ratio: 45 / 18;
    }

    .pixel {
        aspect-ratio: 1;
        border-radius: 3px;
        background: #0c1914;
        border: 1px solid #142b22;
        box-shadow: inset 0 0 3px rgba(0, 255, 120, 0.04);
        transition:
            background 0.12s ease,
            box-shadow 0.12s ease,
            transform 0.12s ease;
    }

    .pixel.active {
        background: #21e879;
        border-color: #42ff91;
        box-shadow:
            0 0 7px rgba(33, 232, 121, 0.7),
            0 0 16px rgba(33, 232, 121, 0.25),
            inset 0 0 5px rgba(255, 255, 255, 0.25);
        transform: scale(1.04);
    }

    .pixel.fade {
        background: #123b29;
        border-color: #1b7047;
        box-shadow: 0 0 5px rgba(33, 232, 121, 0.2);
    }

    .label {
        margin-top: 18px;
        text-align: center;
        color: #42ff91;
        font-size: 13px;
        letter-spacing: 4px;
        opacity: 0.7;
    }

    @media (max-width: 600px) {
        .lcd {
            padding: 15px;
        }

        .screen {
            gap: 2px;
        }

        .pixel {
            border-radius: 1px;
        }
    }
</style>
</head>

<body>

<div class="lcd">

    <div class="screen" id="screen"></div>

    <div class="label">
        LCD // KDZXY
    </div>

</div>

<script>
const screen = document.getElementById("screen");

const COLS = 45;
const ROWS = 18;

const pixels = [];

for (let i = 0; i < COLS * ROWS; i++) {
    const pixel = document.createElement("div");
    pixel.className = "pixel";

    screen.appendChild(pixel);
    pixels.push(pixel);
}

const font = {
    K: [
        "10001",
        "10010",
        "10100",
        "11000",
        "10100",
        "10010",
        "10001"
    ],

    D: [
        "11110",
        "10001",
        "10001",
        "10001",
        "10001",
        "10001",
        "11110"
    ],

    Z: [
        "11111",
        "00001",
        "00010",
        "00100",
        "01000",
        "10000",
        "11111"
    ],

    X: [
        "10001",
        "10001",
        "01010",
        "00100",
        "01010",
        "10001",
        "10001"
    ],

    Y: [
        "10001",
        "10001",
        "01010",
        "00100",
        "00100",
        "00100",
        "00100"
    ]
};

const word = "KDZXY";

const startRow = 5;
const startCol = 8;

const activePixels = [];

word.split("").forEach((letter, letterIndex) => {

    const pattern = font[letter];

    const letterStartCol = startCol + letterIndex * 7;

    pattern.forEach((row, r) => {

        [...row].forEach((value, c) => {

            if (value === "1") {

                const gridRow = startRow + r;
                const gridCol = letterStartCol + c;

                const index =
                    gridRow * COLS + gridCol;

                activePixels.push(index);
            }

        });

    });

});

function clearScreen() {
    pixels.forEach(pixel => {
        pixel.classList.remove("active");
        pixel.classList.remove("fade");
    });
}

async function sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function animate() {

    while (true) {

        clearScreen();

        await sleep(500);

        /*
         * Kotak hijau muncul satu per satu
         */
        for (const index of activePixels) {

            pixels[index].classList.add("active");

            await sleep(28);
        }

        /*
         * Tulisan KDZXY bertahan sebentar
         */
        await sleep(1400);

        /*
         * Efek redup sebelum menghilang
         */
        activePixels.forEach(index => {
            pixels[index].classList.remove("active");
            pixels[index].classList.add("fade");
        });

        await sleep(350);

        clearScreen();

        await sleep(500);
    }
}

animate();
</script>

</body>
</html>

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&duration=3000&pause=1000&color=58A6FF&center=true&vCenter=true&width=700&lines=Bot+Developer;Security+Researcher;Bug+Hunter;Node.js+Developer;Linux+Enthusiast" alt="Typing SVG" />

<br>

```text
╔══════════════════════════════════════════════════════════════╗
║                                                              ║
║                  K D Z X Y  //  D E V                        ║
║                                                              ║
║        BOT DEVELOPER  •  SECURITY  •  AUTOMATION             ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Building bots, tools, APIs and experiments.**

[![GitHub](https://img.shields.io/badge/GitHub-kdzxy-181717?style=for-the-badge\&logo=github)](https://github.com/kdzxy)
[![Profile Views](https://komarev.com/ghpvc/?username=kdzxy\&style=for-the-badge\&color=58A6FF)](https://github.com/kdzxy)

</div>

---

## `whoami`

```bash
$ whoami

kdzxy

$ cat about.txt

Bot Developer
Bug Hunter
Linux User
Open Source Explorer
```

I'm a developer interested in **automation, bots, web development, APIs, Linux and application security**.

I enjoy building things, breaking things in controlled environments, understanding how systems work, and turning experiments into useful projects.

---

## `focus`

```text
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  >  BOT DEVELOPMENT                                         │
│      WhatsApp bots • Automation • APIs                      │
│                                                             │
│  >  SECURITY                                                │
│      Bug hunting • Web security • Research                  │
│                                                             │
│  >  WEB DEVELOPMENT                                         │
│      Frontend • Backend • REST APIs                         │
│                                                             │
│  >  LINUX                                                   │
│      CLI • Servers • Development environments               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## `tech stack`

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge\&logo=javascript\&logoColor=000)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge\&logo=node.js\&logoColor=fff)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge\&logo=python\&logoColor=fff)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge\&logo=html5\&logoColor=fff)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge\&logo=css3\&logoColor=fff)

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge\&logo=git\&logoColor=fff)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge\&logo=github\&logoColor=fff)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge\&logo=linux\&logoColor=000)
![VS Code](https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge\&logo=visual-studio-code\&logoColor=fff)

</div>

---

## `projects`

###  WhatsApp Bot

Developing WhatsApp automation projects using Node.js.

**Areas:**

* Command systems
* Plugin architecture
* API integration
* Media processing
* Database systems
* Group management
* Automation

---

###  Security Research

Learning and experimenting with application security in authorized environments.

**Areas:**

* Web security
* API security
* Authentication
* Input validation
* Vulnerability research
* Secure coding

> Security research should always be performed on systems you own or have explicit permission to test.

---

###  Automation

Building small tools that automate repetitive tasks and simplify development workflows.

```text
INPUT
  │
  ▼
PROCESS
  │
  ├── API
  ├── BOT
  ├── DATABASE
  └── AUTOMATION
  │
  ▼
OUTPUT
```

---



---

## `github stats`

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=kdzxy&show_icons=true&theme=github_dark&hide_border=true&count_private=true" height="170"/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=kdzxy&layout=compact&theme=github_dark&hide_border=true" height="170"/>

</div>

---

## `activity`

<div align="center">

<img src="https://github-readme-activity-graph.vercel.app/graph?username=kdzxy&theme=github-compact&hide_border=true" width="95%"/>

</div>

---

## `contribution`

<div align="center">

![GitHub Streak](https://streak-stats.demolab.com?user=kdzxy\&theme=github-dark-blue\&hide_border=true)

</div>

---

## `terminal`

```bash
┌──(kdzxy㉿github)-[~/projects]
└─$ ls

bots/
security/
web/
automation/
experiments/

┌──(kdzxy㉿github)-[~/projects]
└─$ echo "keep learning"

keep learning
```

---

## `current status`

```text
[██████████████████░░] 90% Learning
[████████████████░░░░] 80% Building
[██████████████░░░░░░] 70% Security
[█████████████████░░░] 85% Experimenting
```

---

## `goals`

* [x] Learn JavaScript
* [x] Build Node.js projects
* [x] Work with APIs
* [x] Learn Linux
* [x] Build automation tools
* [ ] Improve backend development
* [ ] Learn deeper web security
* [ ] Build larger open-source projects
* [ ] Contribute to security research
* [ ] Keep learning

---

## `connect`

<div align="center">

<a href="https://github.com/kdzxy">
<img src="https://img.shields.io/badge/GitHub-kdzxy-181717?style=for-the-badge&logo=github"/>
</a>

</div>

---

<div align="center">

```text
╔════════════════════════════════════════════════════╗
║                                                    ║
║   "Code. Break. Understand. Build it better."      ║
║                                                    ║
╚════════════════════════════════════════════════════╝
```

**Thanks for visiting my profile.**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,100:58a6ff&height=100&section=footer"/>

</div>
