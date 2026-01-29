
## Goal
**Learn to write production-grade Python code** (readable, testable, debuggable) — build foundations for AI engineering.


## Cadence
- **1 shipped script / tool / API client per week**
  - ✅ Tests included  
  - ✅ Logged, typed, structured  
  - ✅ README written


## Learning Strategy
🧑‍🏫 **Use an LLM as your 1:1 mentor** (in *study mode*) while you go through the curriculum.

### How to use LLMs to learn Python
**💡 Treat the LLM as:**

- **Explainer** — ask specific, contextual questions when docs are too abstract.
  - Prompt style: *“Explain X in the context of what I’m building.”*
  - Anti-pattern: *“Teach me Python from scratch.”*

- **Pair programmer** — use it to sketch functions, refactor messy code, or suggest structure — **but type the final code yourself; never paste full solutions blindly.**
  - *If you didn’t write it, you don’t own it — and you didn’t learn it.*
  - Anti-pattern: *“Build the whole app for me.”*
  - Tools like Cursor or Claude Code have **Plan Mode** — use it.

- **Debugger (rubber duck 🦆)** — use it to interpret errors, stack traces, and edge cases, and to explain why something fails.
  - Prompt style: *“Given this error and this code, what’s the most likely root cause?”*
  - Anti-pattern: moving forward without understanding the failure.

- **Reviewer** — replace mediocre code reviews and get a tight feedback loop.
  - Ask: *“What’s wrong with this structure?”* / *“Where will this break in prod?”*
  - Err on the side of understanding: talk through trade-offs and alternative approaches.

### What to avoid while learning?
- ⚠️ **Letting an LLM do all the work** — copy-pasting without understanding or writing the code yourself
- **Passive consumption** — watching YouTube, video tutorials, or beginner-oriented courses with in-browser IDEs. **It is not learning, without typing.**
- **"I’ll learn this properly later”**  — no, you don't. At each step of the curriculum strive for understanding before you move on.

> **For an optimized learning curve**, spend about 80% of your time writing code and breaking things (even intentionally) in Cursor or VS Code. Experiment, reason about why things work or fail, and stay curious about what you’re building. Use the remaining 20% for reading documentation and other resources.

### How to use docs and resources tactically
- **Map each resource to a specific learning phase in the curriculum**  
  *(guidance on which resources matter at which stage comes later)*

- **Feed relevant docs to the LLM**
  - **Ask narrow, concrete questions**  
    - Bad: *“How does async work in Python?”*  
    - Good: *“Why does `asyncio.gather` block here in my code?”*

- **Force justification and explanation**
  - Ask: *“Why is this better than X?”*, *“What are the failure modes?”*
  - This turns the LLM into a sparring partner, not a shortcut

- **Always cross-check against official docs — docs are law**
  - If LLM output ≠ docs → docs win
  - That’s why you feed the LLM links to specific doc pages or ask it to search the web around those docs
  - Ask for citations or references to exact sections
  - If something contradicts official docs (hallucinations) → ignore it
  - Anti-pattern: blindly trusting AI-generated code

### Pro Tip
> **You can create a dedicated Project (Claude / ChatGPT) or Gem (Gemini) with these rules built in.** This is less redundant than restating them in every new chat.  
> 
> Consider adding the following to its system instructions:
>
> *“When I ask for a code review, always check for: (1) missing type hints, (2) lack of Pydantic validation for external data, (3) hardcoded secrets, and (4) opportunities to use `pathlib` instead of `os.path`. Be pedantic — I want code that passes MyPy in strict mode.”*


## Roadmap (reference only — visual check)
[Python Roadmap](https://roadmap.sh/python)

## Curriculum (~8 weeks)

1. **Environment & workflow (2–3 days)**
   - **Python versions** (3.10+)
   - **Virtual environments**
     - `venv`, `uv venv`
   - **Dependency management**
     - `pip`, **`uv`** (preferred)
     - `pyproject.toml`
   - **Project structure**
     ```
     project/
       src/
       tests/
       pyproject.toml
       README.md
     ```
   - **Editors & tooling**
     - Cursor (recommended) or VS Code
     - Ruff (linter + formatter)
     - MyPy (strict mode)
     - pre-commit hooks (Ruff only)
   - **Environment variables**
     - `.env` files
     - `python-dotenv`
     - never hardcode secrets
   - **Git basics**
     - `init`, `add`, `commit`, `push`, `branch`, `merge`, `.gitignore`

   **Outcome:** You can start any project cleanly in under 5 minutes, install dependencies, set up the environment and create repo.


2. **Core Python (~7 days)**
   - **Syntax & control flow**
     - Variables and types
     - `if`, `for`, `while`
     - List / dict / set comprehensions
   - **Data structures**
     - `list`, `tuple`
     - `dict`
     - `set`
     - When to use which (performance + semantics)
   - **Functions**
     - Pure vs impure
     - Arguments (`*args`, `**kwargs`)
     - Type hints
     - Docstrings

   **Outcome:** You can express logic clearly and idiomatically, run small scripts and read other people’s Python without friction.


3. **Errors, files, and data (~7 days)**
   - **Error handling**
     - `try / except / else / finally`
     - Custom exceptions
     - Fail fast vs fail soft
   - **Files & serialization**
     - `pathlib`
     - Reading and writing files
     - JSON (`json`)
     - CSV basics
   - **Data validation**
     - `pydantic.BaseModel`
     - Parsing external JSON → typed objects
     - Validation errors vs runtime errors
   - **Logging**
     - `logging`
     - Log levels
     - Structured logs

   **Outcome:** Bad data can’t silently enter your system, logs tell you what broke, and errors don’t scare you.


4. **Object model & structure (~7 days)**
   - **Classes vs functions**
     - `__init__`
     - Composition > inheritance
     - Dataclasses
   - **Modules & packages**
     - Imports (absolute vs relative)
     - Package layout
     - `__init__.py`
   - **Standard library**
     - `os`, `sys`
     - `pathlib`
     - `datetime`
     - `itertools`, `functools`

   **Outcome:** You can structure non-trivial codebases without overengineering and know _when not to use classes_. Do **not** chase OOP purity. 


5. **Production Python (~3 weeks)**
   - **APIs & networking**
     - `requests` (sync, baseline)
     - `httpx` (async)
     - HTTP status codes
     - Retries and timeouts (`tenacity`)
     - Auth (tokens, headers)
   - **Async Python**
     - `async / await`
     - `asyncio.gather`
     - When async is worth it (parallel I/O)
   - **FastAPI** (basics, late in phase)
     - App structure
     - Routes
     - Request / response models (reuse Pydantic)
     - Simple inference-style endpoint
     - Local run only
   - **Testing**
     - `pytest`
     - Unit vs integration tests
     - Fixtures
     - Testing error paths
   - **Debugging**
     - Reading stack traces
     - `pdb`
     - IDE debugger

   **Outcome:** You can build, test, and run a small API service that talks to external APIs and doesn’t fall over.


6. **Advanced Python (~5 days total, spread opportunistically)**
   - Decorators (very important)
   - Generators
   - Context managers

   **Outcome:** You can read, use, and write simple decorators, generators, and context managers when they add clear value.


## Capstone Project Example

### The "News Intelligence CLI"

**Goal:** Build a command-line tool that aggregates news from an external API, validates the data, handles network instability gracefully, and provides clear visibility into its internal operations.

- **Environment & secure workflow**
  - **Tooling:** Initialize the project using `uv init`.
  - **Secrets management:**
    - Create a `.env` file for your `NEWS_API_KEY`.
    - Add `.env` to your `.gitignore` immediately.
    - Use `python-dotenv` to load the key: `load_dotenv()` + `os.getenv("NEWS_API_KEY")`.
  - **Standards:** Set up `pre-commit` to run Ruff and MyPy (strict mode) on every commit.

- **Robust data handling**
  - **Pydantic models:** Define a `NewsArticle` schema and use it to parse raw JSON from the API.
  - **Structured logging:** Replace all `print()` statements with `logging` or `structlog`.
    - **Implementation:** Configure a JSON formatter so logs are machine-parsable.
    - **Failures:** If Pydantic validation fails, log the specific fields that caused the error (context), not a generic “data error”.

- **Resilient networking & FastAPI**
  - **Parallelism:** Use `httpx.AsyncClient` and `asyncio.gather` to fetch multiple categories (e.g. Tech, Finance, Science) concurrently.
  - **Tenacity shield:** Decorate the fetch function to handle `429 Too Many Requests` and `504 Gateway Timeout`.
  - **Integration:** Wrap the logic in a simple **FastAPI** endpoint (`/news/{category}`) so the tool works over HTTP as well as via CLI.

- **Advanced performance tracking**
  - **Timing decorator:** Write a custom decorator to measure execution time of API calls.
  - **Standard library:** Use `time.perf_counter()` for high-precision timing.
  - **Output:** Log timing data at the `DEBUG` level to observe performance without polluting production logs.


### 🏆 Success Criteria
- **Observable:** Can I see retry attempts in my logs?
- **Secure:** Is my API key absent from my GitHub history?
- **Typed:** Does MyPy return zero errors when run in strict mode?
- **Resilient:** If I turn off Wi-Fi, does the app retry and then exit with a clear error message instead of a messy stack trace?


## Resources (latest Python, production-focused)

✅ **GTO approach:** Start with the Python docs and Real Python for Phases 1–4. Switch to FastAPI and Pydantic docs for Phase 5. Reference other docs as needed.

- [Python docs](https://docs.python.org/3/)
  - **Use for:**
    - Language reference
    - Standard library (`pathlib`, `logging`, `itertools`)
    - Exact semantics

- [Real Python](https://realpython.com)
  - **Use selectively for:**
    - Async
    - Logging
    - Packaging
    - Typing
  - **Avoid beginner fluff**

- [FastAPI docs](https://fastapi.tiangolo.com)
  - **Use for:**
    - Async usage
    - Pydantic in practice
    - Dependency injection patterns

- [Pydantic docs](https://docs.pydantic.dev/latest/)
  - **Use for:**
    - Model validation
    - Settings management

- [HTTPX docs](https://www.python-httpx.org)
- [uv docs](https://docs.astral.sh/uv/)
- [Ruff docs](https://docs.astral.sh/ruff/)
- [Tenacity docs](https://tenacity.readthedocs.io/en/latest/)
- [pytest docs](https://docs.pytest.org/en/stable/)
- [Python Packaging Authority docs](https://www.pypa.io/en/latest/)