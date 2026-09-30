# Farcell: una volta d’apunts de diverses matèries

Demostració amb matemàtiques, física i literatura. L'estudiant i els apunts
són ficticis; les explicacions i els càlculs són material didàctic creat per
al projecte. El microrelat és original, sense atribució a un autor publicat.

## Què hi ha i per què

Sis documents d'entrada: quatre de matemàtiques, un de física i un de literatura.
Cada original té una fitxa; les idees reutilitzables tenen notes de concepte.
Hi ha exercicis, preguntes, dues síntesis i dos mapes de navegació.

Les matemàtiques i la física comparteixen una connexió sustentada pels apunts:
la derivada com a eina per estudiar velocitat i la integral com a acumulació.
La literatura conserva una ruta pròpia. La volta mostra que es poden reunir
matèries sense forçar una relació entre tots els seus continguts.

## Explorar el resultat

Obre **`demo/`** com a volta a Obsidian i entra a `wiki/index.md`.
La [guia de lectura i visualització](demo/wiki/guia.md) descriu les peces, les
metadades i la manera d'explorar-les. Inclou una llegenda opcional i un perfil de colors preparat per al graf.
No obris només `wiki/`: els enllaços necessiten els originals de `raw/`.

## Provar la skill

Copia només `demo/raw/` a una carpeta temporal i demana:

> Utilitza $farcell amb aquests apunts de diverses matèries. Crea una
> volta-apunts amb perfil d'aprenentatge, fitxes i rutes per
> assignatura. Connecta conceptes entre matèries quan hi hagi suport i explica
> la relació. Treballa sense Python i registra què has llegit i comprovat.

La sortida inclosa és una organització possible, no una plantilla obligatòria.
Pots afegir un altre fragment de literatura a la còpia temporal i comprovar
si amplia aquella branca sense reescriure els apunts de física o matemàtiques.
Una volta dedicada a una única assignatura també és una opció vàlida si aquest
és l'objectiu de l'usuari; no és el que s'assumeix a la demostració general.

## Retirar-lo

Elimina `examples/` quan ja no el necessitis. No forma part de la skill
instal·lada ni es carrega automàticament. Per compartir un paquet sense exemples,
usa `python3 scripts/distribute.py --without-examples`, o copia només
`skills/farcell/`. No barregis la demostració amb el corpus de la teva volta real.

La carpeta oculta `demo/.obsidian/` inclou únicament el perfil de graf de
la demostració. Conserva-la quan copiïs l'exemple si vols veure els colors
preparats. Aquesta ajuda visual és opcional i no forma part de la skill.
