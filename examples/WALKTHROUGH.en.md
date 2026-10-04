# Try Farcell with a realistic task

[English](WALKTHROUGH.en.md) · [Català](PASSEIG.md)

The included folder is a prepared result, not a certified record of autonomous
execution. This walkthrough helps you check whether your AI reaches supported
conclusions and maintains the vault carefully. Use a temporary copy.

## 1. Understand what it adds

Scenario: you have notes from three subjects and want to prepare a study session.
Open `demo/` in Obsidian and start at `wiki/index.md`. Try answering these questions
by following notes and originals, then ask the agent:

| Request | What the vault should provide | Where to check |
|---|---|---|
| “Why do we get 2.8 and 4 m/s? Is there an error?” | Distinguish a data interval from the model derivative; compare 2.8 with 3 m/s for the same interval | [Comparative exercise](demo/wiki/exercicis/model-i-dades.md) |
| “How are calculus and motion connected?” | Explain application, conditions and units with sources | [Cross-subject synthesis](demo/wiki/sintesis/matematiques-i-fisica.md) |
| “Who wrote the letter, and how do we know?” | Separate the initial answer from evidence in the continuation | [Revised reading](demo/wiki/sintesis/lectura-revisada.md) |
| “What can I not conclude yet?” | Note missing measurement uncertainties and the story's textual scope | [Model and data](demo/wiki/exercicis/model-i-dades.md), [literary source](demo/raw/relat-continuacio.md) |

The benefit is retrieving an answer with its reasoning and returning to the
notes without remembering which file held each idea. Literature can have its
own route without an artificial link to mathematics.

## 2. Generate an initial version

In a test folder, copy the originals from `demo/raw/` **except
`relat-continuacio.md`**. Keep that continuation outside the input folder. Ask:

> Use Farcell to organize these notes into a new vault. Create source notes,
> connect concepts that depend on each other across subjects, and prepare
> revision questions. Work only with these documents. Preserve originals.

Names and wording may vary. What matters is valid links and supported conclusions.
The letter question must remain unresolved: this initial input includes neither
the signature nor the statement. The eight source notes in the included result
represent the final state, after step 3.

## 3. Add a source and observe maintenance

Add `relat-continuacio.md` to the temporary copy's input and ask:

> Incorporate the new fragment. Review the answers that depend on it and explain
> what changed. Preserve the earlier interpretation with its context.

Expect a new source note, an updated question and affected notes, and an answer
supported by the second fragment. Calculus notes do not need rewriting for this
addition. The log should identify the sources and notes changed.

## 4. Check more than the graph

Follow at least one claim from synthesis to original passage. Check that
fictional data are labelled and no result is presented as a real measurement.
A careful answer preserves gaps; it does not add nonexistent measurement
uncertainty or external verification of authorship.

To try protection of edits, add your own annotation to a note in the temporary
copy and request a related update. The agent must preserve the annotation or
present a separate proposal if safe integration is uncertain. Python detects
hashes; manual mode must not promise the same automatic capability. Project
checks validate files and links, not perfect instruction-following by every model.
