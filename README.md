Notes: Google AI Studio -> create api key
https://googleapis.github.io/python-genai/#generate-content

messages = [
    types.Content(role="user", parts=[types.Part(text=prompt)]),
    ]

    available_functions = types.Tool(
    function_declarations=[
        schema_get_files_info,
        schema_get_file_content,
        schema_run_python_file,
        schema_write_file],
    )

    config=types.GenerateContentConfig(
        tools=[available_functions], system_instruction=system_prompt
    )
response = client.models.generate_content(
            model='gemini-2.0-flash-001', 
            contents=messages,
            config=config,
        )
Specify user prompts (--verbose optional to see prompt and response tokens), system prompts (define behaviour), tools (function declarations).

system_prompt = """
    You are a helpful AI coding agent.

    When a user asks a question or makes a request, make a function call plan. You can perform the following operations:

    - List files and directories
    - Read the content of a file
    - Write to a file (create or update)
    - Run a python file with optional arguments

    When the user asks about the code project - they are referring to the working directory. 
    So, you should typically start by looking at the project's files and figuing out how to run the project 
    and how to run its tests, you'll always want to test the tests and the actual project to verify that behaviour is working.
    All paths you provide should be relative to the working directory. 
    You do not need to specify the working directory in your function calls as it is automatically injected for security reasons.
    """


uv : https://github.com/astral-sh/uv


wsl

uv init your-project-name

cd your-project-name

uv venv

source .venv/bin/activate


uv add google-genai==1.12.1

uv add python-dotenv==1.1.0

uv run main.py
create .env file
echo GEMINI_API_KEY="your_api_key_here" > .env

Add the .env file to your .gitignore (We never want to commit API keys, passwords, or other sensitive information to git.)


