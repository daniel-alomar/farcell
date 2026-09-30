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

## Començar

Copia `skills/farcell/` al directori de skills del teu agent, o demana-li que
llegeixi `skills/farcell/SKILL.md`. Necessites un agent capaç de llegir les
fonts i escriure fitxers. La skill s'invoca com a `$farcell`; la lectura i
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

## Ús amb Python o sense

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
no ho és, aplica el procediment manual. `tooling: python` demana explícitament
les comprovacions automàtiques. [Detall dels modes](skills/farcell/references/tooling.md).

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

## Recomanació opcional: graf de colors

Els colors són una ajuda de navegació d'Obsidian. La skill pot treballar sense
ells i no configura automàticament el graf de les voltes personals.
La demostració inclou un perfil de colors preparat; la seva guia explica
com obrir el graf, interpretar la llegenda i canviar-la o retirar-la.

## Carpetes

- `skills/farcell/`: instruccions, referències i comprovador opcional.
- `agents/`: rols opcionals de coordinació i revisió; no s'activen sols.
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
