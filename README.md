uv : https://github.com/astral-sh/uv

wsl
uv init your-project-name
cd your-project-name
uv venv
source .venv/bin/activate

uv add google-genai==1.12.1
uv add python-dotenv==1.1.0

uv run main.py

Google AI Studio -> create api key
create .env file
echo GEMINI_API_KEY="your_api_key_here" > .env

Add the .env file to your .gitignore (We never want to commit API keys, passwords, or other sensitive information to git.)
