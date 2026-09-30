# Farcell: apunts d'un estudiant de matemàtiques

Demostració creada per al projecte. L'estudiant i els seus apunts són ficticis;
els conceptes matemàtics i les solucions es poden comprovar amb els càlculs.
No és una reproducció d'un curs ni una bibliografia acadèmica.

## Explorar el resultat

Obre **`demo/`** com a volta a Obsidian i entra a `wiki/index.md`. Mantén `raw/`
i `wiki/` dins la mateixa volta perquè funcionin els enllaços als originals.

Hi ha quatre documents d'entrada, quatre fitxes, tres conceptes, una nota
amb solucions, un mapa d'estudi, una síntesi i una pregunta de repàs. Comença
pel mapa; segueix funció → derivada → integral i torna als apunts amb els
localitzadors. La síntesi mostra com relacionar canvi local i acumulació.
La pregunta conserva un error freqüent per orientar el repàs.

## Provar la skill

Copia només `demo/raw/` a una carpeta temporal i demana:

> Utilitza $farcell amb aquests apunts. Crea una volta nova en català amb
> perfil d'aprenentatge. Connecta definicions i exercicis, explica les
> relacions i conserva els errors com a preguntes de repàs. Treballa sense
> Python i registra què has llegit i comprovat.

La volta inclosa mostra un possible resultat, no un text que l'agent hagi
de reproduir. Pots afegir un exercici a la còpia temporal i comprovar si
s'actualitzen la fitxa, les solucions i el mapa sense reescriure notes alienes.
No utilitzis l'exemple com a font de la teva biblioteca personal.

## Retirar-lo

Pots eliminar `examples/`. No s'inclou dins la skill instal·lada i no es
carrega automàticament. Per compartir un paquet sense demostració, utilitza
`python3 scripts/distribute.py --without-examples` des de l'arrel del projecte.
Aquest comandament és opcional: també pots compartir només `skills/farcell/`.
