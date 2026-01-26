## Goal
**Write production-grade Python code** (readable, testable, debuggable).

## Cadence
- **1 shipped script / tool / API client per week**
	- ✅ Tests included
	- ✅ Logged, typed, structured
	- ✅ README written

## Learning Strategy
🧑‍🏫 **Use LLM as your 1:1 mentor** (in *study mode*) and simply go through the curriculum. 

### How to use LLMs to learn Python?
**💡Treat LLM as:****
- **Explainer** - ask specific questions when docs are too abstract or you need clarity to understand something; make them contextual.
	- Prompt style: *“Explain X in the context of what I’m building.”
	- Anti-pattern: *“Teach me Python from scratch”* or other non-specific questions
* **Pair programmer** - use LLM to sketch functions, refactor ugly code, or suggest structure - **but you type the final code, never paste full solutions blindly**
	* *If you didn’t write it, you don’t own it. And you didn't learn it.*
	* Anti-pattern: *“Build the whole app for me”*
* **Debugger (rubber duck 🦆)** - use it to interpret errors, stack traces, reason about edge cases, or to explain why something fails
	* Prompt style: *“Given this error and this code, what’s the most likely root cause?”*
	* Anti-pattern: progressing further without deep understanding why something fails
* **Reviewer** - ask: “What’s wrong with this structure?”, “Where will this break in prod?”; try to deepen your understanding at all cost
	* This replaces mediocre code reviews early on and gives you tight feedback loop
* **High-level architect:** you can ask about how specific stuff *can* be built, before you start writing a single line of code
	* Err on the side of understanding the problem first with LLM, then talk through ideas and possible solutions

### What to avoid when learning with LLM?
- ⚠️ **LLM doing job for you,** without (again) understanding what's going on
- **Passive learning**: only reading LLM answers, watching YouTube, or any kind of beginner tutorials


**📄 Reference docs/resources tactically**
* Map specific resource to actual learning phase
* Feed them to LLM, especially when concerned
	* Ask narrow questions
		* Bad: *“How does async work in Python?”*
		* Good: *“Why does `asyncio.gather` block here in my code?”*
* Always force justification
	* Ask: “Why is this better than X?”, “What are the failure modes?”
	* This turns the LLM into a thinking partner, not a shortcut.
* Always cross-check with docs: docs are law, If LLM output ≠ docs → docs win
	* If something contradicts official docs (LLM hallucinations) → ignore it
	* Anti-pattern: blindly trusting generated code
	* Treat LLMs as **accelerators, not authorities**


> [!tip] Important tip
> **You can create specific Project (Claude/ChatGPT) or Gem (Gemini) with those rules implemented, it will be less redundant then writing them every time in new chat**. Consider adding this prompt to its system instruction:
> 
> *"When I ask for a code review, always check for: 1. Missing type hints, 2. Lack of Pydantic validation for external data, 3. Hardcoded secrets, and 4. Opportunities to use pathlib instead of os.path. Be pedantic; I want to write code that passes MyPy strict mode."*

## Roadmap (reference only)
==Python roadmap==


## Curriculum (~8 weeks)

1. **Environment & workflow (2-3 days)**
	* **Python versions (3.10+)**
	- **Virtual environments**
	    - `venv`, `uv venv`
	- **Dependency management**
	    - `pip`, **`uv`** (preferred)
	    - `pyproject.toml`
	- **Project structure**
	    `project/   src/   tests/   pyproject.toml   README.md`
	- **Editors & tooling**
	    - Cursor (recommended) or VS Code
	    - Ruff (Linter + Formatter)
	    - MyPy (Strict mode)
	    - pre-commit hooks (Ruff only)
	- **Environment variables**
		- `.env` files
		- `python-dotenv`
		- never hardcode secrets
	- **Git basics**
		* `init`, `add`, `commit`, `push`, `branch`, `merge`,  `.gitignore`
	**Outcome:** You can start any project cleanly in <5 minutes and you cannot commit dirty code.

2. **Core Python (~7 days)**
	- **Syntax & control flow**
		- Variables, types
		- `if / for / while`
		- List/dict/set comprehensions
	- **Data structures**
		- `list`, `tuple`
		- `dict`
		- `set`
		- When to use which (performance + semantics)
	- **Functions**
		- Pure vs impure
		- Arguments (`*args`, `**kwargs`)
		- Type hints
		- Docstrings
	**Outcome:** You can express logic clearly and idiomatically and read other people’s Python without friction.

3. **Errors, files, data (~7 days)**
	- **Error handling**
		- `try / except / else / finally`
		- Custom exceptions
		- Fail fast vs fail soft
	- **Files & serialization**
		- `pathlib`
		- Read/write files
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
    **Outcome:** Bad data cannot silently enter your system and failures are observable.

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
	- `os`, `sys`
	- `pathlib`
	- `datetime`
	- `itertools`, `functools`
	**Outcome:** You can structure non-trivial codebases without overengineering.

5. **Production Python (~3 weeks)**
	 - **APIs & networking**
		 - `requests` (sync, baseline)
		 - `httpx` (async)
		 - Status codes
		 - Retries & timeouts (`tenacity`)
		 - Auth (tokens, headers)
	- **Async Python**
		- `async / await`
		- `asyncio.gather`
		- When async is worth it (parallel I/O)
	- **FastAPI (basics, late in phase)**
		- app structure
		- routes
		- request / response models (reuse Pydantic)
		- simple inference-style endpoint
		- local run only
	- **Testing** 
		- `pytest`
		- Unit vs integration tests
		- Fixtures
		- Testing error paths
	- **Debugging**
		- Reading stack traces
		- `pdb`
		- IDE debugger
	**Outcome:** You can build, test, and run a small API service that talks to external APIs and doesn’t fall over.

6. **Advanced Python (~5 days total, spread opportunistically)**
	- Decorators (very important)
	- Generators
	- Context managers
- **Outcome**: You can read, use, and write simple decorators, generators, and context managers when they add clear value.

## Capstone Project Example

#### The "News Intelligence CLI"

**Goal:** Build a command-line tool that aggregates news from an external API, validates the data, handles network instability gracefully, and provides clear visibility into its internal operations.

* **Environment & Secure Workflow**
	* **Tooling:** Initialize the project using `uv init`.
	* **Secrets Management:** * Create a `.env` file for your `NEWS_API_KEY`.
		* Add `.env` to your `.gitignore` immediately.
		* Use `python-dotenv` to load the key: `load_dotenv()` + `os.getenv("NEWS_API_KEY")`.
	- **Standards:** Set up `pre-commit` to run `Ruff` and `MyPy` (strict mode) on every commit.
 - **Robust Data Handling**
	- **Pydantic Models:** Define a `NewsArticle` schema. Use it to parse the raw JSON from the API.
	- **Structured Logging:** Replace all `print()` statements with the `logging` module or `structlog`.
		- **Implementation:** Configure a JSON formatter so logs can be parsed by machines.
		- **Failures:** If Pydantic validation fails, log the specific fields that caused the error (the "context") instead of a generic "Data error."
- **Resilient Networking & FastAPI**
	- **Parallelism:** Use `httpx.AsyncClient` and `asyncio.gather` to fetch news from multiple categories (e.g., Tech, Finance, Science) simultaneously.
	- **The "Tenacity" Shield:** Decorate your fetch function to handle the inevitable "429 Too Many Requests" or "504 Gateway Timeout":
	- **Integration:** Wrap the logic in a simple **FastAPI** endpoint (`/news/{category}`) so the tool can serve data over HTTP as well as the CLI.
- Advanced Performance Tracking
	- **Timing Decorator:** Write a custom decorator to measure the execution time of your API calls.
	- **Standard Library:** Use `time.perf_counter()` inside the decorator for high-precision timing.
	- **Output:** Log the timing data at the `DEBUG` level so you can monitor performance without cluttering production logs.

### 🏆 Success Criteria
- **Observable:** Can I see a "retry attempt" in my logs?
- **Secure:** Is my API key missing from my GitHub history?
- **Typed:** Does `MyPy` return zero errors when I run it? 
- **Resilient:** If I turn off my Wi-Fi, does the app retry and then exit with a helpful error message instead of a messy stack trace?

## Resources (latest python, production focused)

✅ **GTO approach:** Start with Python Docs + Real Python for Phases 1-4. Switch to FastAPI/Pydantic docs for Phase 5. Reference other docs as you need them. 

* [Python docs](https://docs.python.org/3/)
	* **Use for:**
		* language reference
		* standard library (`pathlib`, `logging`, `itertools`)
		* exact semantics  
* [Real Python](https://realpython.com)
	* **Use selectively for:**
		* async
		* logging
		* packaging
		* typing  
	* **Avoid beginner fluff**
* [FastAPI docs](https://fastapi.tiangolo.com)
	* **Use for:**
		- async usage
	    - Pydantic in practice
	    - dependency injection patterns
* [Pydantic docs](https://docs.pydantic.dev/latest/)
	* **Use for:**
		* model validation
		* error surfaces
		* settings management
* [HTTPX Docs](https://www.python-httpx.org)
* [uv docs](https://docs.astral.sh/uv/)
- [Ruff docs](https://docs.astral.sh/ruff/)
- [Tenacity docs](https://tenacity.readthedocs.io/en/latest/)
* [pytest docs](https://docs.pytest.org/en/stable/)
* [Python Packaging Authority Docs](https://www.pypa.io/en/latest/)

⚠️ **Avoid**
- Udemy/Coursera beginner courses (slow, outdated, hand-holding)
- "Automate the Boring Stuff" (good book, wrong focus for you — it's scripting, not production)
- YouTube tutorials longer than 20 min (usually padded)
- Any resource using Python <3.10

## Stay up to date
- [The New Stack (Python Category)](https://thenewstack.io/category/python/)
- [Hacker News (Python Threads)](https://news.ycombinator.com)

## Deep dive (leading, opinionated, credible)
- Fluent Python (2nd edition)
- [Effective Python](https://effectivepython.com)
- Architecture Patterns with Python