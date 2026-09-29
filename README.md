<div align="center">

<img width="100%" alt="header" src="https://capsule-render.vercel.app/api?type=waving&height=210&text=Yuurigram%20Tools&fontAlign=50&fontAlignY=36&fontSize=56&desc=Telegram%20Multi-Account%20Toolkit%20%7C%2019%20Features%20%7C%20Session%20Manager&descAlign=50&descAlignY=58"/>

<img alt="typing" src="https://readme-typing-svg.demolab.com?font=Inter&size=18&duration=3000&pause=650&center=true&vCenter=true&width=900&lines=Session+Manager+%7C+Create+%2F+Rename+%2F+Check+Status;Extract+InitData+%7C+Raw+%2F+User-First+%2F+Full+URL;Auto+Join+%2F+Leave+%2F+Mute+%2F+Archive+Groups;Auto+Reaction+%7C+Single+or+Random+Emoji;Auto+Math+Quiz+%7C+Inline+Click+%7C+Vote+Poll;TData+to+Session+%7C+Session+to+TData+Converter"/>

<p>
  <img alt="platform" src="https://img.shields.io/badge/Platform-Telegram%20Multi--Account-111111"/>
  <img alt="sessions" src="https://img.shields.io/badge/Sessions-Multi--Account-111111"/>
  <img alt="author" src="https://img.shields.io/badge/by-Yuurisandesu-111111"/>
</p>

<p>
  <b>Yuurigram Tools</b> is a multi-account Telegram toolkit that runs on session files.<br/>
  It provides 19 features across session management, initData extraction, group and channel automation, account management, inline bot interactions, giveaway scanning, poll voting, and TData conversion, all accessible from a single interactive menu.<br/>
  Built and distributed by <b>Yuurisandesu</b>.
</p>

</div>

---

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Setup](#setup)
- [Running the Bot](#running-the-bot)
- [Features](#features)
- [File Structure](#file-structure)
- [Disclaimer](#disclaimer)

---

## Requirements

- Ruby `3.2+` (only needed to run the downloader script)
- Telegram API ID and API Hash
- `.session` files for each account

---

## Installation

### Step 1 - Get the Binary

**Using the downloader script:**

```bash
ruby bot.rb
```

The script shows a numbered menu:

```
1. Yuurigram Linux ARM64
2. Yuurigram Linux AMD64
3. Windows (PowerShell / CMD)
```

Enter the number for your platform. The binary downloads with a live progress bar and is set to executable automatically on Linux.

Or download manually from the Releases page:
https://github.com/Yuurisan-N1/Yuurigram-Tools/releases/latest

| File | Platform |
|---|---|
| `Yuurigram.exe` | Windows x86_64 |
| `yuurigram-linux-amd64` | Linux x86_64 |
| `yuurigram-linux-arm64` | Linux ARM64 |

**Linux after manual download:**

```bash
chmod +x yuurigram-linux-amd64
```

### Step 2 - Get Your Telegram API Credentials

Go to https://my.telegram.org, log in, and open **API Development Tools**. Create an app and copy the `api_id` and `api_hash`.

### Step 3 - Prepare Session Files

Place all `.session` files in the `session/` folder. If you do not have session files yet, run the binary and use option 1 (Create New Session) to log in and generate one.

---

## Setup

Create a `.env` file in the same folder as the binary with your Telegram API credentials:

```env
APP_ID=your_api_id
APP_HASH=your_api_hash
```

If `.env` is not found, the binary will prompt you to enter these values interactively on startup.

---

## Running the Bot

**Linux AMD64:**

```bash
./yuurigram-linux-amd64
```

**Linux ARM64:**

```bash
./yuurigram-linux-arm64
```

**Windows:**

```bash
.\Yuurigram.exe
```

The binary launches an interactive menu with all 19 features. Select a number and follow the prompts. Press Enter after each feature completes to return to the main menu.

---

## Features

### 01. Create New Session
Enter a phone number with country code. The bot sends a verification code via Telegram, prompts for it, and handles 2FA if enabled. The session is saved to `session/` named after the account username or user ID.

### 02. Auto Extract InitData
Enter a Web App URL and bot username. The bot opens the mini app for each session and extracts the `tgWebAppData`. Output format is selectable: raw initData saved to `query.txt`, user-first reordered initData saved to `user.txt`, full Web App URL with initData embedded saved to `url.txt`, or all three at once. Multiple referral codes can be entered separated by commas to rotate across sessions.

### 03. Auto Join Groups and Channels
Enter one or more group or channel links. All session files join each one in sequence. Optionally mute and archive joined groups automatically.

### 04. Auto Leave Groups and Channels
Enter one or more group or channel identifiers (links, usernames, or numeric IDs). All session files leave each one.

### 05. Auto Referral Bot
Enter a bot username and an optional referral code. All session files send `/start` or `/start ref_code` to the bot, then mute and archive the chat.

### 06. Auto Edit Name
Choose a name edit mode: replace first name, append to first name, replace last name, append to last name, or delete last name entirely. The change is applied to all session files.

### 07. Auto Reaction
Enter a message link and select one or more emojis from a list of 35 common reactions. All session files react to the message with the selected emoji, or a random one if multiple are chosen.

### 08. Check Account or Session Status
Checks each session file and prints the account name, username, phone number, user ID, premium status, scam flag, and restriction status. Optionally extracts phone numbers to `number.txt` and user IDs to `userid.txt`.

### 09. Chat Settings
Four modes: mute all unmuted chats across all sessions, unmute all muted chats, archive selected groups or channels, or block and delete chat history with selected users.

### 10. Auto Set 2FA
Enter a new 2FA password and optional hint. All session files that do not already have 2FA enabled will have it set. Accounts with 2FA already enabled are skipped.

### 11. Get Latest Telegram Login Message
Enter a session name. The bot reads the last two messages from the Telegram service account (777000) for that session to retrieve the most recent login code.

### 12. Auto Solve Inline Math Questions
Enter a bot username. Three solving modes are available: click the inline button first then answer the math from the resulting message, answer the math first then click any inline confirmation that appears within 5 seconds, or answer the math directly from the last message without inline handling. Math expressions using `+`, `-`, `*`, `/`, and `x` are detected and solved automatically.

### 13. Auto Click Inline Button
Enter a bot username. The last message from that bot is scanned for an inline keyboard. You pick which button number to click and that button is clicked on all session files.

### 14. Auto Chat
Enter a bot username and choose from 16 message types to send: random X profile link, random X tweet link, random Facebook profile or post link, random TikTok profile or video link, random Instagram profile, story, post, or reels link, random YouTube channel, video, or shorts link, a username (random or the session's real Telegram username), custom text, or a freshly generated crypto wallet address for EVM, Solana, or TRX. When crypto addresses are sent, the generated private keys are saved to `privatekey/privatekey.json`.

### 15. Auto Search and Join Giveaway Channels
The first session scans configured giveaway feed channels for active giveaway messages and joins all referenced channels. All remaining sessions then mirror the same joined channels. Joined channels are muted and archived automatically.

### 16. Vote on Telegram Poll
Enter a poll message link. The poll options are displayed and you select which one to vote for. All session files that can access the poll message cast the selected vote.

### 17. Rename Sessions Automatically
Each session file is renamed to match the account's Telegram username, or its first and last name if no username is set. Duplicate names are resolved with a numeric suffix.

### 18. Convert Saved InitData to URLs
Select an existing initData file (query.txt, user.txt, or another file) and a Web App base URL. Each initData line is converted to a full Web App URL with theme parameters and saved to `url.txt`.

### 19. Convert TData or Session
Two conversion modes: TData folder to session file using opentele, or session file to TData folder. 2FA is handled interactively if required. Output is saved to the `tdata/` or `session/` folder accordingly.

---

## File Structure

```text
Yuurigram-Tools/
├── Yuurigram.exe              # Windows binary
├── yuurigram-linux-amd64      # Linux x86_64 binary
├── yuurigram-linux-arm64      # Linux ARM64 binary
├── bot.rb                     # Interactive downloader script
├── .env                       # API credentials (APP_ID and APP_HASH)
├── session/                   # Telegram session files (.session)
├── tdata/                     # TData folders for conversion
├── privatekey/
│   └── privatekey.json        # Generated crypto private keys (auto-created)
└── utils/
    └── banner.rb              # Banner using yuurisan module
```

---

## Disclaimer

This tool is built for educational and technical exploration purposes. Use it wisely and at your own responsibility.

---

<div align="center">
<img width="100%" alt="footer" src="https://capsule-render.vercel.app/api?type=waving&height=120&section=footer"/>
</div>