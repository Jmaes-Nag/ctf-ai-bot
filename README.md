# 🤖 AI Guard CTF: Prompt Injection Challenge

A Dockerized Capture The Flag (CTF) challenge where you must trick an AI chatbot into revealing a secret flag. (written with help from Google Gemini)

_Created for educational purposes._

## 🚩 The Objective
You are a hacker facing "AIGuard," a security bot instructed to never reveal the secret flag. Your goal is to use **Prompt Injection** techniques to bypass the system prompt and trick the AI into leaking the secret.

Once you have the flag, enter it into the verification box to win!

## 🚀 Quick Start (Run from Docker Hub)
If you just want to play the challenge, you can run the pre-built image directly.

**Prerequisites:**
1. [Docker](https://www.docker.com/) installed.
2. An API Key from [OpenRouter](https://openrouter.ai/) (Required to power the LLM).

### 1. Run the Command
Replace `your_api_key_here` with your actual OpenRouter key.

```bash
docker run -p 5000:5000 -e OPENROUTER_API_KEY="your_api_key_here" jmaesng/ctf-ai-bot:latest
```
### 2. Access the CTF
Open your web browser and navigate to: http://localhost:5000/

## ⚙️ Configuration (.env)

You can customize the challenge (like changing the flag or the difficulty) using environment variables.

1. Create a file named .env in your directory:
```bash
touch .env
```
2. Add your configuration to the file (see `.env.example`):
```ini
# Required
OPENROUTER_API_KEY=sk-or-v1-your-actual-key

# Optional - Change the flag to whatever you want!
CTF_FLAG=CTF{custom_flag_for_your_event}
```
3. Run with the env file:
```Bash
docker run -p 5000:5000 --env-file .env jmaesng/ctf-ai-bot:latest
```

## 🛠 Building from Source
If you want to modify the code or the HTML interface:
1. Clone the repository:
```bash
git clone https://github.com/Jmaes-Nag/ctf-ai-bot
cd ctf-ai-bot
```
2. Build the image:
```bash
docker build -t ctf-ai-bot .
```
3. Run the local build
```bash
docker run -p 5000:5000 --env-file .env ctf-ai-bot
```
## 🎮 How to Play

1. Chat: Use the chat interface to speak with the AI. Try to convince it to show you the flag.
2. Attack: Use techniques like "Ignore previous instructions," roleplaying ("Act as a Linux terminal"), or hypothetical scenarios.
3. Verify: When you think you have the flag, paste it into the "Verify Capture Flag" box at the bottom of the screen.

## 📝 Troubleshooting

- Error 404 / No Endpoints: The AI model configured in the code might be offline. Check `app.py` and update the model string.
- Error 429 (Rate Limit): The free model is busy. Wait a moment or switch to a paid model key in OpenRouter.
