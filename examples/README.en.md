# Farcell: study notes across several subjects

[English](README.en.md) · [Català](README.md)

A demonstration with mathematics, physics and literature. The student and notes
are fictional; explanations and calculations are teaching material created for
the project. The short story is original and is not attributed to a published author.
The demo files remain in Catalan; these guides explain how to explore them.

## What is included and why

Eight input documents: four mathematics, two physics and two literature.
Each original has a source note; reusable ideas have concept notes. Exercises,
questions, syntheses and navigation maps include a comparison of model and data
and an answer that changes with new information.

Mathematics and physics share a connection supported by the notes: derivatives
for studying velocity and integrals for accumulation. Literature has its own
route. A vault can bring subjects together without forcing connections among
everything it contains.

## Explore the result

Open **`demo/`** as an Obsidian vault and start at `wiki/index.md`. The
[reading and visualization guide](../docs/en/demo-guide.md) explains the pieces,
metadata and navigation. It includes an optional legend and a prepared graph
colour profile. Do not open only `wiki/`: links need the originals in `raw/`.

## Try the skill

Copy only `demo/raw/` to a temporary folder and ask:

> Use $farcell with these notes from several subjects. Create a study vault
> with a learning profile, source notes and routes by subject. Connect concepts
> across subjects when supported and explain each relationship. Work without
> Python and record what you read and checked.

The included output is one possible organization, not a required template.
Add another literature fragment to the temporary copy and check whether it
extends that branch without rewriting physics or mathematics notes. A vault
for a single subject is also valid when that is the user's goal; the general
demonstration does not assume it.

## Remove the example

Delete `examples/` when you no longer need it. It is not part of the installed
skill and is not loaded automatically. To share a package without examples,
use `python3 scripts/distribute.py --without-examples`, or copy only
`skills/farcell/`. Keep the demo separate from your real corpus.

The hidden `demo/.obsidian/` folder distributed here contains only the demo
graph profile. Keep it when copying the example if you want the prepared
colours. This visual aid is optional and is not part of the skill.

[Practical walkthrough with prompts and expected results](WALKTHROUGH.en.md).
