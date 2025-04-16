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
git clone https://github.com/yourusername/ai-news-video-generator.git
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

