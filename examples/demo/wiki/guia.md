---
id: demo-guia
type: map
status: draft
created: "2026-09-30"
updated: "2026-09-30"
tags: [demostracio, navegacio]
sources: []
source_notes: []
---

# Llegir i visualitzar la demostració

Aquesta guia explica la informació sobre l'exemple: què s'ha inclòs, què
representa cada peça i què es pot veure a Obsidian. No és una font dels apunts.

## Les peces de la volta

| Peça | Què conté | Per què serveix |
|---|---|---|
| `raw/` | Vuit documents didàctics d'entrada | Tornar al passatge que sosté una afirmació |
| `wiki/fonts/` | Vuit fitxes de procedència i abast | Saber què s'ha llegit i de quin document prové |
| `wiki/conceptes/` | Funció, derivada, integral, velocitat i narrador | Reutilitzar idees sense duplicar tots els apunts |
| `wiki/exercicis/` | Càlculs resolts i comparació entre model i dades | Practicar i comprovar els resultats |
| `wiki/sintesis/` | Canvi/acumulació, càlcul/moviment i lectura revisada | Llegir relacions explicades amb evidència |
| `wiki/preguntes/` | Error de derivació i autoria de la carta | Conservar dubtes i límits del material |
| `wiki/mapes/` | Ruta matemàtica i mapa de matèries | Triar per on començar |
| `wiki/registre.md`, `wiki/pendents.md` | Lectures i límits | Distingir treball fet i possibles ampliacions |

Les propietats inicials de les notes inclouen `type`, `status`, `sources`
i `source_notes`. Descriuen tipus, estat editorial i dependències de fonts.
`status: draft` significa esborrany, no revisió humana. Les etiquetes `tags`
permeten agrupar les notes per matèria. No són un judici de qualitat.

## Una ruta per provar-ho

1. Entra a [[wiki/mapes/materies|matèries]] i tria una assignatura.
2. Obre [[wiki/conceptes/velocitat|velocitat]] i segueix l'enllaç a
   [[wiki/conceptes/derivada|derivada]]: el text explica per què es relacionen.
3. Torna a [[raw/moviment#2. Velocitat mitjana i instantània|la secció dels apunts]].
4. Explora [[wiki/conceptes/narrador|narrador]]: la seva branca no necessita
   una connexió amb càlcul per ser útil.

Un mapa és navegació editorial; estar connectat a l'índex no prova una relació
conceptual. Les línies del graf tampoc indiquen per si mateixes si la relació
és una aplicació, una contradicció o una referència. Cal llegir la nota.

## Recomanació opcional: graf amb colors

Al graf d'Obsidian, obre la configuració, entra a **Groups / Grups**, crea
un grup amb una consulta i tria el color del cercle. És una funció integrada.
Pots filtrar per `path:wiki/` per centrar-te en les notes. Les regles següents
són una proposta visual. La demostració ja inclou aquests grups i colors
a `.obsidian/graph.json`; les etiquetes són als fitxers.

| Consulta del grup | Color suggerit | Significat |
|---|---|---|
| `tag:materia/matematiques` | Blau | Notes de matemàtiques |
| `tag:materia/fisica` | Verd | Notes de física |
| `tag:materia/literatura` | Taronja | Notes de literatura |
| `tag:connexio-entre-materies` | Violeta | Síntesi entre matèries |
| `tag:navegacio` | Gris | Mapa general |

Obre també el graf local d'una nota per veure les connexions pròximes.
Els colors distingeixen grups; no certifiquen coneixement ni revisió.
[Documentació oficial del graf](https://obsidian.md/help/plugins/graph).
No cal instal·lar plugins. El paquet inclou només el perfil de graf creat
per a aquesta demostració, sense historial de finestres ni configuració personal.

### Veure els colors de la demostració

Obre la carpeta completa `examples/demo/` com a volta i després la vista de
graf global. No n'hi ha prou amb copiar només `wiki/`: la carpeta oculta
`.obsidian/` conté el perfil. Si ja tenies aquesta volta oberta quan s'ha
afegit el fitxer, tanca-la i torna-la a obrir. La demostració filtra el graf
per les notes de `wiki/`; pots canviar aquest filtre.

Els colors són opcionals i es poden modificar a Grups o restablir des de la
configuració del graf. No copiïs el perfil sobre les preferències d'una volta
personal sense revisar-lo. El graf local pot tenir opcions pròpies.
El format del perfil s'ha comprovat com a JSON; la visualització no s'ha
validat en una sessió gràfica d'Obsidian en aquesta revisió.

L’ampliació incorpora una continuació literària i una pràctica amb dades
sintètiques: [[wiki/sintesis/lectura-revisada|lectura revisada]] i
[[wiki/exercicis/model-i-dades|model i dades]].

[English reading guide](../../../docs/en/demo-guide.md) (documentació del projecte, fora de la volta).
