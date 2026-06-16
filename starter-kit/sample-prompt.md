# Sample prompt — paste this whole thing into AskSage (or any AI)

Copy everything between the lines below, fill in the one bracketed section with your
situation, and send it. You do **not** need to attach any files — the format the AI
needs is built into the prompt. (Some tools, including AskSage, reject `.tex`/`.cls`
uploads, so pasting is the reliable way.)

---

You are a military correspondence specialist. Write an Army Memorandum for Record
that strictly complies with AR 25-50.

Output it as **LaTeX source** using the `armymemo` document class, matching this
exact structure (keep these commands, fill in the values):

    \documentclass{armymemo}
    \address{<organization name>}
    \address{<street address>}
    \address{<city, state  ZIP+4>}
    \officesymbol{<office symbol>}
    \signaturedate{<day Month year>}
    \memoline{MEMORANDUM FOR RECORD}
    \subject{<subject line, 10 words or fewer>}
    \author{<FULL NAME IN CAPS>}\rank{<rank spelled out>}\branch{<branch abbrev>}
    \title{<duty title>}
    \begin{document}
    \begin{enumerate}
    \item References.  <authorities, or omit if none>
    \item Purpose.  <bottom line up front, 1-2 sentences>
    \item <body paragraph(s); use nested \begin{enumerate} for subparagraphs>
    \item The point of contact is the undersigned at <phone> or <email>.
    \end{enumerate}
    \end{document}

Writing rules:
- Active voice throughout. Bottom line up front in paragraph 2 (Purpose).
- References in paragraph 1, point of contact in the last paragraph.
- Subject line: 10 words or fewer. Two spaces after each period.

CRITICAL — do not invent any fact. If you do not have a name, date, unit, phone
number, or statistic, leave a blank exactly like this: \rule{1.5in}{0.4pt} — never
make one up.

OUTPUT FORMAT — return ONLY the raw LaTeX, starting with \documentclass{armymemo}.
Do NOT wrap it in markdown code fences (no triple backticks) and do NOT add any
explanation before or after it.

Here is what the memo is about:
[ Brain-dump everything you know here — topic, your name/rank/unit if you want it
  filled in, the policy or event, key dates, who it's for. Messy is fine. ]

---

## What to do with the AI's reply

The AI gives you back a block of LaTeX. It **cannot turn that into a PDF by itself** —
you compile it on Overleaf (free, in your browser):

1. Go to overleaf.com → New Project → Blank Project.
2. Upload `armymemo.cls` and `DODb1.pdf` (from this kit) into the project.
3. Paste the AI's LaTeX into the main `.tex` file, replacing what's there.
   - Paste ONLY the LaTeX. It must start with `\documentclass{armymemo}`. If the AI
     added ``` lines at the top/bottom, or any sentences, delete them.
4. Menu (top-left) → **Compiler → LuaLaTeX** → Recompile.
5. Download the PDF.

### Filling in the blanks
Wherever the AI didn't have a fact, your PDF will show a blank underline. To fill one
in: find the matching `\rule{...}{...}` in the source, replace the whole `\rule{...}{...}`
with your text (e.g. replace it with `Madigan Army Medical Center`), and Recompile.

(See the explainer for the full walkthrough and the other two methods.)
