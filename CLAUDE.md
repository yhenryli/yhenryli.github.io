# Multi-Agent Coordination Rules
You are operating in a hybrid AI workspace collaborating with Google Antigravity (Gemini 3 Pro). To prevent memory silos, this repository uses the `/.team-brain` folder as the absolute source of truth.

Continuous Execution Rules:
1. **Read First:** Check `/.team-brain/plans/` for the latest architectural blueprints drafted by Antigravity before coding.
2. **Strict Adherence:** Obey the constraints listed in `/.team-brain/tech-stack.md`. 
3. **Log Your Pivots:** If you encounter a flaw that forces you to deviate from Antigravity's plan, do not just change the code. You MUST append a detailed note to `/.team-brain/decisions/changelog.md` explaining why you changed the architecture so Antigravity knows.
