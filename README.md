# 🗞️ AI News Video Generator

An AI-powered Python application that automatically fetches trending news, generates short spoken scripts using Gemini, fetches relevant background images from Unsplash, adds text overlays, and compiles everything into a seamless narrated video using FFmpeg.

---

## 🚀 Features

- ✅ Fetches trending news from Google News RSS
- 🧠 Summarizes news into conversational speech using **Gemini 1.5 Flash**
- 🖼️ Fetches relevant background images from **Unsplash API**
- ✍️ Overlays text onto images
- 🎙️ Converts text to audio using **gTTS (Google Text-to-Speech)**
- 🎬 Generates final video using **FFmpeg**

---

## 📦 Tech Stack

- Python 3.8+
- [Gemini API (Google Generative AI)](https://ai.google.dev/)
- [Unsplash API](https://unsplash.com/developers)
- gTTS (Google Text-to-Speech)
- FFmpeg (installed system-wide)
- Pillow (PIL) for image manipulation
- BeautifulSoup for parsing RSS
- Requests for API calls

---

## 🔧 Installation

```bash
# Clone the repository
git clone https://github.com/aniket-mahakalkar/Task1-AI-News.git
cd ai-news-video-generator

# Install dependencies
pip install -r requirements.txt



## ⚙️ Working of the App

The AI News Video Generator follows a step-by-step pipeline to convert trending headlines into a complete news video:

---

### 🧾 Step 1: Fetch Trending News

- The app scrapes the top headlines from [Google News RSS feed](https://news.google.com/rss).
- It extracts and stores the first 4 news items to keep the video short and focused.

```python
url = "https://news.google.com/rss"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'xml')
items = soup.find_all('item')[:4]

## 🧠 Step 2: Generate Script Using Gemini

Once we have the trending news headlines, the next step is to convert each headline into a short, spoken-style script.

### ✅ What Happens in This Step?

- The app uses **Google Gemini 1.5 Flash**, a powerful generative AI model.
- It sends a custom prompt to Gemini for each headline.
- The prompt asks Gemini to:
  - Keep the script short (30–60 seconds)
  - Make it suitable for narration
  - Use a conversational tone (like a human news presenter)

### 🧾 Sample Prompt Sent to Gemini

```python
prompt = f"""
Generate a short news which contains only the sentences which have to speak (30-60 seconds) based on this topic:
"{topic}"

Keep it concise, conversational
"""
## 🧠 Step 2: Video Creation
