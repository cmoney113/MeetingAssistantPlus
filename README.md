# MeetingAssistant+ v2.0.0

**A real-time meeting assistant powered by Otter.ai transcripts and the Groq API for lightning-fast AI analysis.**

---


---

## 📝 Overview

MeetingAssistant+ monitors an Otter.ai meeting transcript in real-time using Playwright for web scraping. It processes the transcript, optionally performs spell checking and name anonymization, and sends relevant chunks to the Groq API for analysis using selected LLMs (like Llama3, Mixtral, Gemma). The AI provides contextual insights, suggested responses, and topic summaries directly within the application's interface.

The application features a customizable PyQt5 GUI with multiple themes, configurable prompts, various export options, word cloud generation, and system tray integration.

## ✨ Key Features

* **🚀 Real-time Analysis:** Connects to an Otter.ai meeting URL and monitors the transcript live.
* **🧠 Groq Powered AI:** Leverages the speed of the Groq API for near-instant AI insights, summaries, and suggested responses during your meeting.
* **🤖 Configurable Models:** Choose from available Groq LLMs (Llama3-70b, Llama3-8b, Mixtral-8x7b, Gemma-7b).
* **✍️ Customizable Prompts:** Define and switch between multiple prompt templates to guide the AI's analysis based on the meeting type (e.g., Job Interview, Team Sync, Brainstorming).
* **🎨 Multiple Themes:** Includes Dark, Light, Navy, Dracula, macOS, and macOS Dark themes for visual customization.
* **⚙️ Flexible Settings:** Configure polling intervals, analysis frequency, fonts, keyboard shortcuts, code words, visual effects, and more via a dedicated settings dialog (`settings.json`).
* **⌨️ Trigger Analysis:** Generate AI insights on-demand using a configurable keyboard shortcut or a spoken code word.
* **📄 Multiple Export Formats:** Save the transcript and AI analysis as TXT, DOCX, PDF, SRT, HTML, or Markdown.
* **☁️ Word Cloud:** Generate and export a word cloud from the meeting transcript.
* **🔒 Optional Anonymization:** Automatically replace detected names with generic identifiers (Person-1, Person-2).
* **✔️ Optional Spell Check:** Corrects common spelling errors in the transcript automatically.
* **⏱️ Meeting Timer:** Tracks meeting duration with optional reminders.
* **🖥️ GUI Interface:** Built with PyQt5 for a native desktop experience.
* **🔄 Asynchronous Operations:** Uses `asyncio` and `qasync` for non-blocking web scraping and API calls.
* **🖱️ System Tray Integration:** Can run minimized in the system tray.

## 🔧 Requirements

* **Python:** 3.7+ (async/await support needed)
* **Groq API Key:** You need an API key from [GroqCloud](https://console.groq.com/keys).
* **Otter.ai Account:** Access to Otter.ai meetings (either your own or shared with you). The script needs to be able to view the transcript page.
* **Playwright Browsers:** Playwright needs browser binaries installed.
* **Python Libraries:**
    * `PyQt5`
    * `qasync`
    * `playwright`
    * `groq`
    * `python-docx`
    * `fpdf` (specifically `fpdf2` might be needed if installing fresh)
    * `wordcloud`
    * `Pillow`
    * `keyboard` (Note: may require root/admin privileges on Linux/macOS for global hotkeys)
    * `markdown`

## 🛠️ Installation

1.  **Clone the Repository (if applicable):**
    ```bash
    git clone <your-repo-url>
    cd <your-repo-directory>
    ```

2.  **Set up a Virtual Environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3.  **Install Python Libraries:**
    ```bash
    pip install PyQt5 qasync "playwright>=1.30" groq python-docx fpdf2 wordcloud Pillow keyboard markdown
    ```
    *(Note: Using `fpdf2` as it's the maintained fork)*

4.  **Install Playwright Browsers:**
    Run this command once to download the necessary browser binaries (like Chromium):
    ```bash
    playwright install
    ```

5.  **Set Groq API Key:**
    The application uses the `groq` library, which typically looks for the API key in an environment variable. Set it in your system or terminal session:
    ```bash
    export GROQ_API_KEY='your_actual_groq_api_key'
    ```
    *(On Windows, use `set GROQ_API_KEY=your_actual_groq_api_key` in Command Prompt or `$env:GROQ_API_KEY="your_actual_groq_api_key"` in PowerShell)*

## ⚙️ Configuration

* The application saves its settings in a `settings.json` file in the same directory.
* You can configure most options through the **Settings Dialog** within the app (click the gear icon ⚙️).
* Key settings include:
    * **Theme:** Choose your preferred look and feel.
    * **AI Model:** Select the Groq LLM for analysis.
    * **Prompts:** Add, edit, delete, and select the active prompt template.
    * **Analysis Frequency:** Control how often the AI analyzes based on lines or time.
    * **Keyboard Shortcut:** Set a global hotkey to trigger analysis.
    * **Code Word:** Set a word that, when detected in the transcript, triggers analysis.
    * **Font & Spacing:** Customize the appearance of text areas.
    * **Startup:** Choose whether to start minimized in the system tray.
    * **Advanced:** Configure polling interval, anonymization, spell check, timer options.

## ▶️ Usage

1.  **Run the Application:**
    ```bash
    python MeetingAssistantPlus_updated.py
    ```

2.  **Enter Meeting URL:** Paste the full URL of the Otter.ai meeting transcript page into the URL input field.

3.  **Start Monitoring:** Click the **Start** button.
    * A browser window managed by Playwright will open and navigate to the URL.
    * **Important:** You may need to manually handle logins or CAPTCHAs in the Playwright browser window if Otter.ai requires it. The script will wait, allowing you time to do this if necessary.
    * The application will start polling the transcript content.

4.  **Real-time Updates:**
    * The "Live Transcript" panel will populate with the meeting conversation.
    * The "Suggested Responses" and "Key Insights & Analysis" panels will update based on the AI's output according to your configured intervals or triggers.

5.  **Trigger Analysis Manually:**
    * Press the configured keyboard shortcut (default `Ctrl+I`).
    * Say the configured code word (default `blossom`) during the meeting (if detected in the transcript).
    * Click the **Generate AI Analysis Now** button (⚡ icon).

6.  **Stop Monitoring:** Click the **Stop** button. This will close the Playwright browser and stop polling.

7.  **Save Transcript:** Click the **Save** button and choose your desired format (TXT, DOCX, PDF, SRT, HTML, MD).

8.  **Word Cloud:** Click the **Word Cloud** button to generate and view a word cloud based on the current transcript. You can export it from the word cloud window.

9.  **Settings:** Click the **Settings** button (⚙️ icon) to open the configuration dialog.

10. **System Tray:** If not starting in the background, you can minimize the app to the system tray. Right-click the tray icon for options (Show, Hide, Quit). Double-click to toggle visibility.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an Issue.

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## 📄 License

Distributed under the MIT License. See `LICENSE` file for more information (if available).

## 🙏 Acknowledgements

* [PyQt5](https://riverbankcomputing.com/software/pyqt/)
* [Groq](https://groq.com/)
* [Playwright](https://playwright.dev/)
* [python-docx](https://python-docx.readthedocs.io/)
* [FPDF2](https://github.com/pyfpdf/fpdf2/)
* [WordCloud](https://github.com/amueller/word_cloud/)
* [Qasync](https://github.com/CabbageDevelopment/qasync)
* [Keyboard](https://github.com/boppreh/keyboard)
* [Markdown](https://python-markdown.github.io/)

---
