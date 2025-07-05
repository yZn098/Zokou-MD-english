<p align="center">
  <img src="https://raw.githubusercontent.com/djalega8000/Zokou-MD/refs/heads/main/Ephoto360.com_164cb282992914.jpg" alt="Zokou Banner" width="600">
  <h1 align="center">Zokou-MD 3.0</h1>
  <p align="center">
    <img src="https://img.shields.io/badge/Multi_Devices-100%25-success?style=flat&logo=whatsapp" alt="Multi-devices">
    <img src="https://img.shields.io/badge/Version-3.0-blue?style=flat&logo=github" alt="Version">
    <img src="https://img.shields.io/badge/Licence-MIT-green?style=flat&logo=opensourceinitiative" alt="Licence">
  </p>
</p>

<div align="center">
  
✨ **A WhatsApp bot** combining power and entertainment  
🔥 **Modular** • 🌍 **Active community***

</div>

---

## 🌟 Why Choose Zokou-MD?

| Feature | Description |
|---------|-------------|
| 🎛️ **Multi-device** | Use the same bot on several devices simultaneously |
| ⚡ **Performance** | Optimized response time thanks to a lightweight architecture |
| 🧩 **Modular** | Enable/disable modules as needed |

---

## 🚀 Deployment

### 1. Cloud Hosting (Heroku)

Deploy instantly on Heroku:

[![Deploy on Heroku](https://www.herokucdn.com/deploy/button.svg)](https://dashboard.heroku.com/new?template=https://github.com/luffy8979/Zokou-MD-english)

---

### 2. Panel Hosting

#### a. Quick Method (Recommended)

1. Create a file named `index.js`.
2. Paste the following script inside and fill in the variables as needed.
3. Start your panel.

<details>
<summary>Click to view the script</summary>

```js
const fs = require("fs");
const { spawnSync, spawn } = require("child_process");

const zokouEnv = {
  // WhatsApp session ID (used to connect to your account)
  SESSION_ID: "",

  // Command prefix to trigger the bot
  PREFIX: ".",

  // If set to "yes", the bot will automatically view all WhatsApp statuses
  AUTO_READ_STATUS: "no",

  // If set to "yes", the bot will automatically download all WhatsApp statuses
  AUTO_DOWNLOAD_STATUS: "no",

  // Display name of your bot
  BOT_NAME: "Zokou-MD",

  // Visual theme for the bot menus (predefined name or media links)
  MENU_THEME: "LUFFY",

  // If "no", commands won't work in private for others
  PM_PERMIT: "no",

  // If "yes", the bot is available to everyone; if "no", only the owner can use it
  MODE_PUBLIC: "yes",

  // Controls the bot's visible activity: 1 = online, 2 = typing, 3 = recording, empty = real
  PRESENCE: "1",

  // Your display name (owner's name)
  OWNER_NAME: "Djalega++",

  // Your phone number in international format
  OWNER_NUMBER: "228 XX XX XX XX",

  // Number of warnings before a user is sanctioned
  WARN_COUNT: 3,

  // If "yes", the bot sends a welcome message on startup
  STARTING_BOT_MESSAGE: "yes",

  // If "yes", the bot automatically replies to private messages
  PM_CHATBOT: "no",

  // If "yes", adds a delay between commands to prevent spam
  ANTI_COMMAND_SPAM: "no",

  // If "yes", deleted messages by others will be sent to you privately
  ANTI_DELETE_MESSAGE: "no",

  // If "yes", the bot automatically reacts to incoming messages
  AUTO_REACT_MESSAGE: "no",

  // If "yes", the bot automatically reacts to statuses
  AUTO_REACT_STATUS: "no",

  // Time zone used by the bot
  TIME_ZONE: "Africa/Sao_Tome",

  // Server environment used (e.g. HEROKU, VPS, etc.)
  SERVER: "vps",

  // Sticker pack name used by the bot
  STICKER_PACKNAME: "made with ❤; Zokou-MD",
};

//////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////

function cloneRepository() {
  const cloneResult = spawnSync("git", [
    "clone",
    "https://github.com/luffy8979/Zokou-MD-english",
    "zokou",
  ]);

  if (cloneResult.error) {
    console.error("Error cloning repository:", cloneResult.error);
  }

  const envFile = "zokou/set.env";

  if (!fs.existsSync(envFile)) {
    for (const [key, value] of Object.entries(zokouEnv)) {
      value ? fs.appendFileSync(envFile, `${key}=${value}\n`) : null;
    }
  }

  installDependancies();
}

function installDependancies() {
  const result = spawnSync("npm", ["install"], {
    cwd: "zokou",
    stdio: "inherit",
    env: { ...process.env, CI: "true" },
  });

  if (result.error || result.status !== 0) {
    console.error("Error installing dependencies:", result.error);
    process.exit(1);
  }
}

function checkDependencies() {
  const result = spawnSync("npm", ["ls"], {
    cwd: "zokou",
    stdio: "inherit",
  });

  if (result.status !== 0) {
    console.log("Some dependencies are missing or invalid.");
    installDependancies();
  } else {
    console.log("All dependencies are installed properly.");
  }
}

function startPm2() {
  const pm2 = spawn(
    "npx",
    ["pm2", "start", "index.js", "--name", "zokou", "--attach"],
    {
      cwd: "zokou",
      stdio: "inherit",
    }
  );

  pm2.on("exit", (code) => {
    if (code !== 0) console.error(`PM2 exited with code ${code}`);
  });

  pm2.on("error", (err) => {
    console.error("PM2 encountered an error:", err);
  });

  pm2?.stderr?.on("data", (data) => {
    console.log(data.toString());
  });

  pm2?.stdout?.on("data", (data) => {
    console.log(data.toString());
  });
}

if (!fs.existsSync("zokou")) {
  cloneRepository();
}

checkDependencies();
startPm2();
```

</details>

#### b. Manual Method

For a classic installation on a panel or VPS:

[![Download ZIP](https://img.shields.io/badge/Download-ZIP-blue?style=for-the-badge&logo=github)](https://github.com/luffy8979/Zokou-MD-english/archive/refs/heads/main.zip)

### 3. VPS Hosting

```bash
git clone https://github.com/luffy8979/Zokou-MD-english # (or use the ZIP)
cd Zokou-MD-english
npm install
npm start
```

1. Configure the `.env` file as needed (see example below).

---

## 🧰 Essentials

### 🔑 Quick Access

| Service | Link | Status |
|---------|------|--------|
| **Session Scan** | [https://zokou-scan.onrender.com](https://zokou-scan.onrender.com) | ![Online](https://img.shields.io/badge/Status-Online-green) |
| **Session Scan 2** | [zokouscan-din3.onrender.com](https://zokouscan-din3.onrender.com) | ![Online](https://img.shields.io/badge/Status-Online-green) |
| **Backup Server** | [zokou-web.onrender.com](https://zokou-web.onrender.com/) | ![Online](https://img.shields.io/badge/Status-Online-green) |

### ⚙️ Minimal Configuration

```env
# .env file
SESSION_ID="your_session_here"    # Required
PREFIX="!"                        # Command character
OWNER_NUMBER="22891733300"        # Your WhatsApp number
```

## 💜 Acknowledgements

### 🏆 Key Contributors

| Member | Contribution | Link |
|--------|--------------|------|
| **Fatao** | GPT/DALL-E Commands • APK Modules | [GitHub](https://github.com/fatao) |
| **CrazyPrince** | Hosting a session service | site closed |

### 🌟 Special Thanks

- **The Zokou community** for testing and feedback  
- **Contributors** on GitHub ([See all](https://github.com/luffy8979/Zokou-MD-english/graphs/contributors))  
- **Beta Testers** for their patience with unstable versions 😅

### 📚 Libraries Used

```bash
@WhiskeySocket/baileys
```
