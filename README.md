# Farcell

Farcell ajuda a convertir documents, apunts i informació dispersa en una
volta d'Obsidian que es pugui explorar i consultar. L'agent crea fitxes de
les fonts, identifica conceptes compartits i explica les connexions entre
ells, amb enllaços que permeten tornar al passatge original. Serveix per
estudiar, documentar un projecte o comprendre un arxiu personal; cada volta
pot tenir el seu objectiu, idioma i manera d'organitzar el coneixement.

Un **farcell** és un embolcall de roba que aplega allò que ens enduem o anem
recollint pel camí. El nom evoca documents de procedències diverses que
acaben formant un recull útil. Aquí, reunir-los és el primer pas: les notes
connectades ajuden a entendre què contenen, què tenen en comú i quines
preguntes deixen obertes.

[Repositori Farcell](https://github.com/daniel-alomar/farcell).

## Com està plantejat

Farcell conté una skill que utilitza l'agent d'IA amb què treballes.
En l'ús habitual, un únic agent llegeix les fonts, crea notes, les connecta
i revisa el resultat seguint passos. No cal executar dos agents.

- `agents/` conté guies de rols opcionals: coordinador i revisor.
- `skills/farcell/agents/openai.yaml` conté metadades de presentació per a Codex;
  no és un altre agent.
- `AGENTS.md` conté instruccions contextuals per treballar al projecte.

[Funcionament, operacions i procés pas a pas](docs/ca/funcionament.md).

## Començar

Copia `skills/farcell/` al directori de skills del teu agent, o demana-li que
llegeixi `skills/farcell/SKILL.md`. Necessites un agent capaç de llegir les
fonts i escriure fitxers. En Codex, la skill s'invoca com a `$farcell`; la lectura i
síntesi les fa l'agent. Obsidian permet navegar i editar el resultat.

Exemple de petició (substitueix les rutes per les teves):

> Utilitza $farcell. Organitza els apunts de `/ruta/apunts` en una volta a
> `/ruta/volta-apunts`. Conserva els originals, relaciona
> els conceptes i prepara rutes d’estudi per matèria amb referències als
> passatges dels apunts. Connecta assignatures només quan les fonts ho justifiquin.

Obre la carpeta de la volta a Obsidian: contindrà `raw/` i `wiki/`.
El punt d'entrada és `wiki/index.md`. Obrir només `wiki/` deixa fora les fonts
que necessiten els enllaços de la demostració. La skill treballa sota demanda;
una execució periòdica requereix acordar el calendari i les carpetes.

## Ús amb altres agents d'IA

El nucli és portable: instruccions Markdown, referències i scripts locals,
sense crides a una API d'OpenAI ni dependència del seu SDK. Requereix un agent
amb accés de lectura i escriptura a les fonts i a la volta; un xat sense
accés als fitxers no pot mantenir directament aquesta carpeta.

Claude Code admet el mateix format de skill. Copia tota la carpeta
`skills/farcell/` a `~/.claude/skills/farcell/` i invoca `/farcell`.
La sintaxi `$farcell` dels exemples correspon a Codex. Consulta la
[documentació de Claude Code](https://code.claude.com/docs/en/skills).

`agents/openai.yaml`, dins de la skill, és metadada específica de Codex i
no forma part del procediment necessari per a Claude. Els rols de `agents/`
continuen sent guies opcionals, no subagents instal·lats de Claude.
Per carregar les instruccions contextuals del projecte a Claude Code, demana
que llegeixi `AGENTS.md` o referencia'l des del `CLAUDE.md` existent, sense
substituir-lo. [Context de projecte a Claude Code](https://code.claude.com/docs/en/memory).

La compatibilitat de format està documentada; encara no s'ha fet una prova
completa d'aquests projectes amb Claude Code. Altres entorns de Claude o
d'altres proveïdors poden requerir una instal·lació i permisos diferents.

## Auxiliar amb Python

**Python és opcional.** Pots crear, consultar i mantenir la volta amb l'agent
i Obsidian, sempre que l'agent disposi de les eines necessàries per llegir
els formats aportats. Per prescindir de Python, afegeix a la petició:

> Treballa sense Python i desa `tooling: manual` a `knowledge.yaml`.

La configuració la interpreta l'agent. En aquest mode comprova fonts i
enllaços amb els lectors disponibles i documenta les lectures al registre.
Es conserven les fitxes, les cites i les connexions. Es perd la detecció
automàtica per empremtes de duplicats, modificacions de notes i canvis de
fonts durant el procés; el manteniment pot requerir més relectures. Si no
pot llegir un format sense Python, el deixa pendent i explica el motiu.

**Qui executa Python?** L'agent, si disposa d'una eina per executar
comandaments i accés als fitxers. L'usuari demana la tasca en llenguatge natural;
no ha de copiar comandaments durant l'ús habitual. Tenir Python instal·lat
no és suficient si l'entorn de l'agent no permet executar-lo. Els comandaments
de més avall són documentació per al manteniment i la diagnosi.

| Mode | Avantatges | Costos i limitacions |
|---|---|---|
| Amb Python | Comprovacions repetibles d'enllaços; detecció per empremtes de canvis i duplicats; protecció davant canvis de la font entre lectura i acceptació | Requereix Python 3.10+, `fcntl` i execució de comandaments; llegir fitxers per calcular empremtes consumeix temps en corpus grans; cal mantenir l'estat local |
| Sense Python | Menys requisits d'execució; útil en entorns amb lectors i edició de fitxers però sense intèrpret | Més relectura i revisió per l'agent; menys detecció automàtica de canvis i duplicats; alguns formats poden quedar pendents |

En tots dos modes, l'agent fa la síntesi i revisa les evidències. Python
no valida la veritat dels continguts ni substitueix la revisió humana.
Recomanació: `auto` per a l'ús habitual; `manual` quan no vulguis executar
Python o l'entorn no ho permeti. «Manual» vol dir que l'agent fa les
comprovacions amb les altres eines, no que l'usuari hagi de fer-les totes.

Per defecte `tooling: auto` utilitza el comprovador quan és disponible; si
no ho és, l’agent explica el motiu i et proposa preparar l’entorn o
continuar sense Python. Espera la teva tria abans de canviar el mode. `tooling: python` demana explícitament
les comprovacions automàtiques. [Detall dels modes](skills/farcell/references/tooling.md).

### Si Python no està disponible

L'agent t'explica el problema amb paraules entenedores i et proposa:

1. **Rebre ajuda per instal·lar o preparar Python**, amb instruccions per al
   teu sistema i l'entorn de l'agent. La instal·lació no es fa automàticament.
2. **Continuar sense Python**, conservant notes, cites, connexions i consultes,
   amb menys detecció automàtica de canvis i duplicats i més revisió per l'agent.

No canvia de mode sense la teva decisió. Si ja has triat el mode manual,
no repeteix aquesta pregunta en cada execució. També distingeix entre Python
absent i un agent que no pot executar comandaments: instal·lar-lo al teu
ordinador no resol necessàriament una limitació de l'entorn remot.

### Requisits i llibreries

No cal instal·lar paquets amb `pip`: les utilitats del projecte utilitzen
exclusivament la biblioteca estàndard de **Python 3.10 o superior**.

| Component | Mòduls utilitzats | Requisit particular |
|---|---|---|
| Inventari, enllaços i acceptació | `argparse`, `collections`, `datetime`, `fcntl`, `hashlib`, `json`, `os`, `pathlib`, `re`, `tempfile` | `fcntl` és propi d'entorns Unix: Linux/macOS; el comprovador no funciona amb Python natiu de Windows |
| Empaquetament | `argparse`, `json`, `pathlib`, `zipfile` | La compressió ZIP necessita `zlib`, habitualment inclòs amb Python |
| Proves | `unittest`, `importlib.util` i mòduls estàndard de fitxers/empremtes | Importen el comprovador i, per tant, també requereixen `fcntl` |

En Windows es pot utilitzar un entorn Linux com WSL amb Python, o triar
el mode manual. `fcntl` no és un paquet que s'hagi d'instal·lar amb `pip`.
Els lectors de PDF/DOCX, l'OCR i la transcripció no estan inclosos en aquestes
utilitats: poden requerir altres eines segons l'entorn de l'agent. No hi ha
una llibreria d'IA obligatòria dins dels scripts del projecte.

## Exemples opcionals

[Guia de la demostració](examples/README.md): apunts didàctics de matemàtiques, física
i literatura. Inclou fitxes, conceptes, rutes per matèria, exercicis i una
connexió justificada entre càlcul i moviment. Una [guia de lectura i visualització](examples/demo/wiki/guia.md)
explica què representa cada part i proposa una visualització opcional del graf. El context
d’estudiant és fictici; els càlculs estan desenvolupats i es poden comprovar.

Obre **`examples/demo/`** com a volta a Obsidian i entra a `wiki/index.md`.
Els exemples estan identificats, no es carreguen automàticament i no formen
part de la skill instal·lada. Pots eliminar `examples/` sense afectar l'ús;
la prova de la demostració s'omet si s'ha eliminat. No els barregis amb les
fonts de la teva volta real. La demostració és una possibilitat d'organització,
no una plantilla obligatòria.

El [recorregut pràctic](examples/PASSEIG.md) inclou peticions, respostes
esperades i una incorporació en dues etapes per veure com evoluciona la volta.

## Recomanació opcional: graf de colors

Els colors són una ajuda de navegació d'Obsidian. La skill pot treballar sense
ells i no configura automàticament el graf de les voltes personals.
La demostració inclou un perfil de colors preparat; la seva guia explica
com obrir el graf, interpretar la llegenda i canviar-la o retirar-la.

## Carpetes

- `skills/farcell/`: instruccions, referències i comprovador opcional.
- `agents/`: guies de rols opcionals, no agents executables.
- `docs/ca/`: guies de funcionament del projecte.
- `context/`: objectiu i decisions del producte.
- `memory/`: resums locals opcionals, exclosos de la distribució.
- `examples/`: demostració eliminable.
- `scripts/` i `tests/`: eines de distribució i proves del projecte.

## Comprovacions auxiliars de la volta

L'eina `skills/farcell/scripts/vault_state.py` requereix Python 3.10 o superior
en Linux/macOS (`fcntl`) i només biblioteca estàndard. Aquests comandaments
s'executen des de `skills/farcell/`, habitualment per l'agent:

| Funció | Objectiu | Efecte |
|---|---|---|
| `scan` | Comparar fonts i notes amb l'estat desat; assenyalar canvis, absències i duplicats | Només lectura |
| `links` | Detectar destins de wikilinks inexistents o ambigus | Només lectura |
| `accept` | Registrar la font revisada i les empremtes de les notes dependents | Escriu `.wiki/state.json` |

```sh
python3 scripts/vault_state.py scan /ruta/volta
python3 scripts/vault_state.py links /ruta/volta
```

La sintaxi d'`accept` i els criteris previs són a [l'esquema](skills/farcell/references/schema.md).
L'eina no resumeix documents, no valida cites ni coneixement i no comprova
àncores, enllaços Markdown o metadades. La revisió de contingut continua
sent necessària. L'OCR i la transcripció depenen dels lectors disponibles.

## Provar el projecte i preparar-ne una distribució

Aquest apartat és per a qui modifica o comparteix el projecte. **No cal
executar-lo per utilitzar la skill ni per obrir una volta a Obsidian.**
Amb Python, des de l'arrel del projecte:

```sh
python3 -B -m unittest discover -s tests
python3 scripts/distribute.py
python3 scripts/distribute.py --without-examples
```

El primer comandament comprova les utilitats, la protecció d'edicions humanes
i els enllaços de la demostració. El segon genera un ZIP i un manifest de
fitxers distribuïbles a `dist/`. El tercer prepara una versió sense exemples;
**no és una opció per desactivar Python**. Sense Python, pots copiar la carpeta
`skills/farcell/` directament i compartir els fitxers seleccionats sense generar
el paquet automàtic. Memòria local, voltes personals, converses i secrets
queden fora de la distribució automàtica. La llicència continua pendent de decisió.

## Projecte relacionat

[Garbell](https://github.com/daniel-alomar/garbell) s’especialitza en lectura crítica, evidència
i síntesi bibliogràfica per a recerca i doctorat.
