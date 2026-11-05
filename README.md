# PromptGuard-RedLLM

PromptGuard-RedLLM is a security testing and defense project for LLM agents. The goal of the project is to test how LLM applications handle prompt injection attacks and to block unsafe behaviors at runtime before the model leaks sensitive data or executes unauthorized database/tool queries.

## Video Presentation

[Watch the 5-Minute Project Walkthrough](VIDEO_LINK_HERE)

## My Contributions

For this project, I worked on both the chat frontend interface and the backend Python security guardrails:

1. **Chat Layout & UI (`chat.js`):** Created the main chat interface layout with placeholder messages for interacting with the agent.
2. **Chat API Integration (`chat.js` -> `/api/agent/chat`):** Added the Send button `fetch` logic in `chat.js` to send user prompts to the `/api/agent/chat` backend endpoint and render responses.
3. **Tool Execution Badge Cards (`chat.js`):** Built visual badge cards in the chat UI to clearly display when tools and guardrails are triggered during a conversation.
4. **PII Redaction Guard (`guards/pii_redaction.py`):** Implemented filtering to detect and redact sensitive personal data (such as emails, phone numbers, and credentials) so private data is never leaked in responses.
5. **Strict Tool Parameter Enforcer (`guards/sql_policy_guard.py`):** Built parameter validation that checks tool and SQL queries against strict policy rules before execution, blocking unauthorized queries or injection attempts.
6. **Multi-Token Canary Leakage Protection (`guards/canary_guard.py` & `promptguard/output_guards.py`):** Implemented multi-token canary tracking and output checks to detect and block attacks trying to extract hidden system prompts.

## Running the Project

1. Install the required dependencies: `pip install -r requirements.txt`
2. Copy `.env.example` to `.env` and add your API key to `OPENAI_CHAT_KEY`.
3. Start the server: `python run_server.py`
4. Run the guardrail verification tests: `python test_all_guards.py`
