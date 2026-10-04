# Reading and visualizing the Farcell demonstration

[English](demo-guide.md) · [Català](../../examples/demo/wiki/guia.md)

This guide describes the example’s organization, not a source for its subject matter. The vault notes and original documents are in Catalan.

## The pieces

| Piece | Contents | Purpose |
|---|---|---|
| `raw/` | Eight teaching documents | Return to the passage supporting a claim |
| `wiki/fonts/` | Eight provenance and scope notes | Identify what was read and where it came from |
| `wiki/conceptes/` | Function, derivative, integral, velocity and narrator | Reuse ideas without duplicating notes |
| `wiki/exercicis/` | Worked calculations and model/data comparison | Practise and check results |
| `wiki/sintesis/` | Change/accumulation, calculus/motion and revised reading | Read evidence-supported relationships |
| `wiki/preguntes/` | Differentiation error and letter authorship | Preserve questions and limits |
| `wiki/mapes/` | Mathematics route and subject map | Choose a starting point |
| `wiki/registre.md`, `wiki/pendents.md` | Reading log and limitations | Distinguish completed work from possible extensions |

## A route to try

1. Open [subjects](../../examples/demo/wiki/mapes/materies.md) and choose one.
2. Open [velocity](../../examples/demo/wiki/conceptes/velocitat.md) and follow
   its link to derivative; the text explains why they are connected.
3. Return to the [motion notes](../../examples/demo/raw/moviment.md), section 2.
4. Explore [narrator](../../examples/demo/wiki/conceptes/narrador.md): its branch
   does not need a connection to calculus to be useful.

The extension adds a literary continuation and synthetic data exercise:
[revised reading](../../examples/demo/wiki/sintesis/lectura-revisada.md) and
[model and data](../../examples/demo/wiki/exercicis/model-i-dades.md).

## Reading the metadata

`sources` and `source_notes` record dependencies. `status: draft` means a draft,
not human review. Tags can group notes; they do not score quality. Graph edges
show links, but reading each note explains whether a relation is an application,
comparison, reference or something else. An index link does not prove a
conceptual relationship.

## Optional graph colours

In Obsidian's graph settings, open **Groups**, add a query and choose its colour.
These groups are included in `examples/demo/.obsidian/graph.json`:

| Group query | Colour | Meaning |
|---|---|---|
| `tag:materia/matematiques` | Blue | Mathematics |
| `tag:materia/fisica` | Green | Physics |
| `tag:materia/literatura` | Orange | Literature |
| `tag:connexio-entre-materies` | Purple | Connections across subjects |
| `tag:navegacio` | Grey | General navigation |

Open the complete `examples/demo/` folder as a vault and then the global graph.
Copying only `wiki/` is insufficient: the hidden `.obsidian/` folder holds the
profile. If you had the vault open when the profile was added, close and reopen
it. The demo filters the graph to `wiki/` notes; you can change this filter.

Colours are optional. Change them under Groups or reset them in graph settings.
Do not copy this profile over a personal vault's preferences without reviewing
it. Local graphs can have their own options. No plugins need to be installed.
Only the authored demo profile is distributed, not personal window history or
configuration. Its JSON format has been checked; visual rendering has not been
validated in an Obsidian graphical session for this revision.
[Official graph documentation](https://obsidian.md/help/plugins/graph).
