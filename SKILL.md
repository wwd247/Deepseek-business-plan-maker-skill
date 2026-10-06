---
name: business-plan-maker
description: Creates a complete business plan as a structured document. Use whenever the user asks to write, draft, create, or revise a business plan, biz plan, or wants help planning or launching a business and turning it into a formal document.
---

# Business Plan Maker

Interviews the user about their business, then builds a full business plan
following the structure and voice defined in `references/template-structure.md`.

## Output format

Produce the plan as a **Word (.docx) document** whenever the environment
supports file writing. Use whichever of these is available, in order of
preference:

1. A native `docx_create` / document-creation tool.
2. The bundled `scripts/build_docx.py` helper, called via the shell tool.
3. Structured Markdown with Word-ready headings (`#`, `##`, `###`), if no
   file-writing capability exists. Note to the user that they can paste this
   into their own Word template.

Do not claim a file was created unless you actually created one.

## Workflow

### 1. Interview the user in batched passes

Read `references/template-structure.md` first. Check what the user has already
told you in the conversation; never re-ask for something already given.

Ask in a small number of batched passes rather than one long form:

1. **Company basics** — business name, one-line description, legal structure
   (Limited Company/guaranteed by shares/Partnership/etc.), major shareholder(s),
   industry, target market/customer.
2. **Strategy** — mission/vision, unique selling proposition, key competitors,
   branding position, routes to market, pricing per revenue stream (ask
   separately for each if more than one), goals/objectives (short and long term).
3. **Funding path** — ask directly whether the business is pursuing outside
   investment/IPO, or staying an owner-operated LLC/privately held. This single
   answer decides whether to include or omit the IPO-specific language marked in
   the template's Profitability Projections, Break-Even Analysis, and closing
   sections. Include that language only if pursuing outside investment/IPO;
   omit it otherwise.
4. **Financials** — startup costs, pricing, revenue so far, projected sales. If
   the user has no real figures, say so plainly and build a clearly-labeled
   illustrative projection instead of inventing false precision. State the
   assumption inline (e.g., "Assumption: 20% gross margin, typical for this
   category").

If the user wants a fast draft and says so ("just make something up," "use
placeholders," "give me a template"), skip the interview and generate a labeled
placeholder draft they can fill in later.

### 2. Draft the content

Follow `references/template-structure.md` section by section and sub-section by
sub-section — same headings, same order. Where a sub-section poses a question or
example to the template's future user, answer it in prose using what the user
told you rather than leaving the question text in the output.

Apply the funding-path answer from step 1.3 to the bracketed sections. Write the
enclosed content only if it applies; omit both the bracket and its content
otherwise.

Keep it concrete and specific to the business, not generic boilerplate. Aim for
a working first draft unless the user asks for more depth.

**Executive Summary (section 1) is written last, by synthesis — never asked
for.** After drafting sections 2–9, pull the highlights — company description,
USP, target market, and the funding ask if pursuing one — into a short, one-page
summary, then place it at the top of the document.

### 3. Produce the document

Generate the plan as a Word document using the output-format rules above.

If using `scripts/build_docx.py`, compose the plan as a single JSON object
matching the schema below, then call the script via the shell:
