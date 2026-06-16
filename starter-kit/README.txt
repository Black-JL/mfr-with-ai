AI-GENERATED ARMY MFR — STARTER KIT
===================================

This folder has everything you need to make AR 25-50 compliant Army memos
with AI. Start with the explainer (the web page or PDF). Quick contents:

  armymemo.cls ............. The rulebook. Encodes every AR 25-50 margin,
                            font, and spacing rule so you never format by hand.
                            (From github.com/glallen01/army-memorandum-class)
                            You UPLOAD this to Overleaf. You don't open it, and
                            you don't give it to the AI.

  DODb1.pdf ................ The DoD seal. You UPLOAD this to Overleaf too.
                            (The memo will not compile without it.)

  mfr-template.tex ......... A blank fill-in MFR, if you'd rather start from a
                            template by hand. You do NOT need to send this to
                            the AI — the format is already inside sample-prompt.md.

  mfr-template-EXAMPLE-output.pdf
                            What a finished memo looks like once compiled.

  sample-prompt.md ......... The prompt to paste into AskSage (or any AI). It
                            already contains the format, so no file uploads to
                            the AI are needed.

  digsig.sty ............... Optional digital-signature support. Ignore it unless
                            you go down the digital-signature path; it is not
                            needed for a normal memo.


THE ONE THING TO REMEMBER
-------------------------
There are always TWO steps:
  1. The AI writes the LaTeX SOURCE (plain text with formatting commands).
  2. A COMPILER turns that source into the finished PDF.

LaTeX (say "LAY-tek") is a typesetting system. The .cls "class" file holds
the formatting rules; you and the AI only supply the words.

FAST PATH (no install)
----------------------
  1. Paste sample-prompt.md into Ask Sage (or any chatbot -- ChatGPT, Claude,
     Gemini), fill in your facts, send. For sensitive/CUI memos use Ask Sage.
  2. Copy ONLY the LaTeX it returns (no ``` lines, no explanation -- it must
     start with \documentclass{armymemo}).
  3. On overleaf.com: New Project -> upload armymemo.cls + DODb1.pdf ->
     paste the LaTeX into the main file -> Menu -> Compiler -> LuaLaTeX ->
     Recompile -> Download PDF.

EXPECT SOME TRIAL AND ERROR
---------------------------
This is AI + LaTeX, not a one-click button. Sometimes the AI wraps its answer
in ``` marks or adds a sentence (delete those); sometimes it returns code that
won't compile (paste the error back into the chat and ask it to fix it); and
you'll tweak wording and fill blanks before it's right. Still far faster than
formatting by hand.

COMPILE LOCALLY (instead of Overleaf)
-------------------------------------
You must compile with LuaLaTeX (not pdfLaTeX), and run it twice:

  keep armymemo.cls + DODb1.pdf next to your .tex, then
  lualatex yourfile.tex && lualatex yourfile.tex

(Note: armymemo uses Times New Roman + Arial. Overleaf and Mac have these.
A bare Linux box may need the msttcorefonts package installed first.)

FILLING IN BLANKS
-----------------
Wherever the AI didn't have a fact, the PDF shows a blank underline. Find the
matching \rule{...}{...} in the source, replace it with your text, recompile.

NEVER let the AI invent a name, date, or number. If it doesn't know, the answer
is a blank line (\rule{}), not a guess. You sign it — you own every word.
