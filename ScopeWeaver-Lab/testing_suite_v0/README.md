# 🧪 ChristmasWeaver Testing Suite

A barebones, Python-based testing harness for evaluating LLM agent performance against specific test cases. This suite is designed to iterate on system prompts and measure reliability metrics (JSON validity, hallucination rate, logic accuracy).

---

## 📂 File Structure

Ensure your directory looks like this:

```text
ChristmasWeaver-Tests/
├── main.py                  # The main test runner
├── check_models.py          # Utility to find available Gemini/Gemma models
├── config.py                # Configuration loader
├── utils.py                 # Helper functions
├── validator.py             # Logic validation engine
├── stats.py                 # Statistics generator
├── .env                     # Your API Key (Create this file, and of course a .gitignore mentioning the .env is you plan to push the entire directory)
├── requirements.txt         # Dependencies
├── prompts/
│   └── v1_system_prompt.md  # The system prompt being tested
└── tests/
    └── v1_test_cases.json   # The dataset of test inputs/expected outputs
```

---

## 🛠️ Setup & Installation

1. **Install Dependencies:**
```bash
pip install -r requirements.txt

```


2. **Configure Environment:**
Create a file named `.env` in the root folder and add your Google AI Studio API key and model name:
```ini
GEMINI_API_KEY=your_api_key_here
GEMINI_MODEL=gemma-3-27b-it

```

> **Recommended Model:** `gemma-3-27b-it` (or similar Gemma variants). These models have high daily limits (~14k/day) as of 31/12/2025 and are robust enough for testing.


---

## 🏃 How to Run

1. **Check Available Models (Optional):**
If you aren't sure which model string to use or if your key works, run:

```bash
python check_models.py

```


*This will list all models your API key has access to.*
2. **Run the Test Suite:**
```bash
python main.py

```


* **Note:** The script has a hard-coded 2-second delay between requests to respect the Gemma rate limit (30 RPM). It should run smoothly without hitting quotas.
* **Output:** Results are saved to `final_stratified_results.csv` (summary) and `results_deep_dive.json` (the detailed logs used for the dashboard).



---

## ⚠️ Disclaimer

This is a **barebones testing suite** primarily used to verify how metrics and results were obtained during development. While you can use it to iterate on the `v1_system_prompt.md`, it is provided "as-is" for transparency and reproducibility.

If you encounter quota issues, verify your usage on the [Google AI Studio Dashboard](https://aistudio.google.com/).

Very little to no documentation inside, if we plan to build off this that's an urgent TODO.

```
