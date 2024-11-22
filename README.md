# 🛠️ ONlineJS - Zenova Bot Status Checker

ONlineJS is a simple JavaScript-based project to monitor the health and uptime of Telegram bots. It performs regular status checks and updates a Telegram channel with the results in real-time.

---

## Features
- 🚀 **Automated Bot Monitoring**: Regularly checks the status of configured bots.
- 📡 **Telegram Channel Updates**: Sends or edits a message in a Telegram channel with the current bot statuses.
- 💡 **Customizable**: Easily add or modify bots to monitor.

---

## Setup

### 1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Zenova-Prime/ONlineJS.git
   cd ONlineJS
   ```

### 2. **Configure the Settings**:
   Open the `workers.js` file and update the following constants:
   - `TELEGRAM_TOKEN`: Your Telegram bot's API token.
   - `CHANNEL_ID`: The Telegram channel ID where updates will be posted.
   - `MESSAGE_ID`: The message ID for editing (if updating an existing message).
   - `bots`: List of bots to monitor. Use the format:
     ```javascript
     const bots = [
       { name: 'BOT_NAME', url: 'STATUS_CHECK_URL', turl: 'TELEGRAM_LINK' },
       // Add more bots here
     ];
     ```

### 3. **Deploy on Cloudflare Workers**:
#### A. **Create a Cloudflare Worker**:
1. Log in to your Cloudflare account.
2. Navigate to the **Workers** section.
3. Click **Create a Worker**.
4. Replace the default code with the script from `workers.js`.
5. Click **Save and Deploy**.

#### B. **Set Up Cron Triggers**:
1. In the Worker settings, go to **Triggers** > **Cron Triggers**.
2. Add a new trigger by specifying the desired time interval (e.g., every 5 minutes, hourly).
3. Save the trigger. The Worker will now run at the specified intervals.

---

## Add or Remove Bots

To manage the list of bots to monitor, edit the `bots` array in the `workers.js` file. Use the following format for each bot:

```javascript
const bots = [
  { name: 'BOT_NAME', url: 'STATUS_CHECK_URL', turl: 'TELEGRAM_LINK' },
];
```

### Example:
```javascript
const bots = [
  { name: 'QUIZORA', url: 'https://outside-gert-jsru-e3ccb0f1.koyeb.app/', turl: 'https://t.me/Quizorabot' },
  { name: 'LECTURES BOT', url: 'https://judicial-kathye-jsroop-295764f8.koyeb.app/', turl: 'https://t.me/JEe_lecture_boT' },
  { name: 'COMPANION BOT', url: 'https://judicial-kathye-jsroop-295764f8.koyeb.app/', turl: 'https://t.me/the_lectures_bot' }
];
```

### Steps to Add a Bot:
1. Add a new object to the `bots` array.
2. Provide:
   - **`name`**: The bot's name.
   - **`url`**: The HTTP URL to check the bot's status (e.g., a health check endpoint).
   - **`turl`**: The bot's Telegram link.

### Steps to Remove a Bot:
1. Locate the bot entry in the `bots` array.
2. Remove the corresponding object.

---

## Usage

- The script automatically runs on scheduled events or via HTTP fetch.
- When triggered, it:
  1. Checks each bot's status via HTTP requests.
  2. Formats a detailed status message.
  3. Sends or edits the status message in the configured Telegram channel.

---

## Example Output

```
✨ 𝗭𝗲𝗻𝗼𝘃𝗮 𝗕𝗼𝘁𝘀 𝗦𝘁𝗮𝘁𝘂𝘀 ✨

━━━━━━━━━━━━━━━━━━━━━━━━

➤ QUIZORA
✦ Status: Alive ⚡
   [Click to visit](https://t.me/Quizorabot)

━━━━━━━━━━━━━━━━━━━━━━━━

➤ LECTURES BOT
✦ Status: Offline ⛔
   [Click to visit](https://t.me/JEe_lecture_boT)

━━━━━━━━━━━━━━━━━━━━━━━━

📅 Last Check:
   Date: 17/11/2024
   Time: 11:45 PM
```

---

## Dependencies
- **Cloudflare Workers** (or any serverless JavaScript runtime).

---

## License
[MIT License](./LICENSE). Feel free to use, modify, and share this project.

---

## Contribution
Found a bug? Want to add new features? Fork the repo and create a pull request.

---


<p align="center">
  Made with ❤️ by <a href="https://zenovas.in">Zenova Team</a>
</p>
