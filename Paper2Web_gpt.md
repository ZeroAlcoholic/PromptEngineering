# ROLE
You are an expert Research Technologist & Creative Frontend Developer (20y) who turns arXiv papers into immersive interactive “Explorables”.

# OUTPUT (HARD)
Generate ONE single, self-contained HTML file (HTML+CSS+JS) that opens directly in Chrome.
No local assets. Libraries only via CDN.
Allowed (choose minimal set): Three.js, GSAP (optional), Chart.js (optional), anime.js (optional), d3 (optional), Matter (optional).
Prefer the lightest stack that can fulfill the visuals (vanilla JS + Canvas/SVG first).

# AUTHORITATIVE SOURCE
Target paper: PromptWizard: Task-Aware Prompt Optimization Framework (Agarwal et al., 2024, arXiv:2405.18369).
You MUST parse the paper’s text + figures (provided to you) and treat them as ground truth.
If any number/parameter is unclear, label it in UI: 「待從 paper 內文確認」. Never fabricate.
Do NOT assume a PDF parser exists in the browser: you (the AI) are the parser; hardcode paper-derived content into the page.

# VISUAL DESIGN SYSTEM — “Matrix Glassmorphism” (STRICT TOKENS)
MUST use these CSS variables exactly:
:root{
  --bg-deep:#010402;
  --glass-bg:rgba(6,15,10,.75);
  --glass-border:rgba(20,150,80,.3);
  --text-primary:#E6F2EC;
  --text-secondary:#94A8A0;
  --text-dim:#5C6E66;
  --green-dim:#0E7A46;
  --green-mid:#129A55;
  --green-neon:#00FF66;
  --font-mono:'JetBrains Mono',monospace;
  --font-sans:'Noto Sans TC',sans-serif;
}

# LAYOUT (STRICT)
- Layer 0: full-screen <canvas> “Matrix Digital Rain” (subtle, low opacity).
- Layer 1: centered glass UI frame, max-width 1200px, backdrop-filter blur(4px), border using --glass-border.
- Navigation tabs: [INSIGHTS] | [PLAYBOOK] | [SIMULATOR] | [METRICS].
- Floating UI must never obstruct primary visuals.

# PERFORMANCE (STRICT)
Matrix Rain must be CPU-safe:
- throttle to ~24–30 FPS, reduce density on small devices
- pause on tab hidden (visibilitychange)
- avoid per-frame allocations
Use --green-neon sparingly (highlights only).

# LANGUAGE (STRICT)
- All UI + narrative: Traditional Chinese (Taiwan).
- All technical terms MUST keep original English forms inline (e.g., Task-Aware, Instruction, In-Context Examples, Critique, Refinement, Synthetic Examples, CoT, performance profile, p(τ), τ).
- No beginner ML primers. Tone: professional high-tech briefing.

# NON-OVERLAP RULES (STRICT)
- Tooltips/labels/panels must not cover key visuals.
- Use fixed side panel(s) at safe margins.
- Tooltips: smart reposition (flip/offset if near edges or covering objects).

# CONTENT GOAL
Explain PromptWizard as a mechanism + workflow, not a text summary.
Must connect: principle → mechanism → workflow → measurable outcome.
Include a small “Paper Mapping” panel mapping each view to paper sections/figures (e.g., “Sec X / Fig Y”).

# REQUIRED TABS (PAPER-GROUNDED)
A) INSIGHTS (Why/What)
- Interactive block diagram:
  Task Description → Base Instruction → [PromptWizard Optimization Loop] → Final Optimized Prompt
- Click blocks → side panel explanation (paper-grounded).
- Emphasize “Task-Aware” + dual optimization of Instruction & In-Context Examples.

B) PLAYBOOK (How)
Flow 1: Stage 1 Instruction Mutation Loop
- Animate: Base Instruction → LLM Mutation → Evaluation → Feedback/Critique → Refinement
- Show branching candidates and convergence to best.
Flow 2: Stage 2 Example Co-Optimization
- “Pool of Examples”
- Split Positive (green) vs Negative (red)
- Show Synthetic Examples generated to fix failures
- Click nodes → explain Critique / Refinement / Synthetic Examples (paper-grounded).

C) SIMULATOR (Hands-on)
- Terminal-like panel (use --font-mono).
- Scenario toggles:
  1) Zero-shot (no training data)
  2) With Synthetic Examples
  3) With real training data
- Simulated evolution log (only concepts described in paper):
  >> Analyzing feedback...
  >> Generating CoT reasoning for stability...
  >> Optimizing instruction constraint...

D) METRICS (Evidence)
- Recreate at least ONE key result chart from paper (preferred):
  performance profile curve p(τ) vs τ and/or dataset accuracy bars (GSM8K/SVAMP/AQUARAT/BBII as shown).
- Hover shows deltas vs baselines ONLY if paper provides exact numbers; otherwise show 「待從 paper 內文確認」.
Use Chart.js or lightweight SVG (choose minimal).

# INTERACTION (MINIMUM)
- Tab switching with smooth transitions (GSAP or CSS transitions).
- Hover tooltips (instant, glass style).
- Click to open side panel detail.
- A timeline/slider for at least one animated process replay (evolution loop playback).

# ENGINEERING STRUCTURE
- <style>: embed theme tokens + glass UI styles + tooltip styles.
- <script>: modular vanilla JS or ES6 classes (App/State/Renderer).
- Keep code readable and self-contained.

# DELIVERABLE (STRICT)
Return ONLY the final HTML code in ONE code block.
No extra commentary outside the code block.
Generate index.html now.
