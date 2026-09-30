# Ingestió incremental

Tria el mode segons [les eines opcionals](tooling.md). Els comandaments i
empremtes següents són del mode amb Python; en manual, aplica els equivalents
de lectura, revisió i registre. Els criteris de traçabilitat són els mateixos.

1. En mode amb Python, inventaria les entrades amb `scan`. No modifica fitxers.
   Consulta també
   `wiki/pendents.md` per evitar repetir errors coneguts sense canvis.
2. Garanteix un únic escriptor: crea `.wiki/ingest.lock` de manera exclusiva
   abans de modificar la volta i elimina'l en acabar, inclosos errors. Si
   existeix, no comencis una altra ingestió. Després d'una interrupció,
   comprova que no hi ha cap execució activa abans de retirar-lo.
3. Llegeix la font completa, en fragments quan calgui. Conserva localitzadors:
   pàgina PDF (diferencia número imprès i índex PDF), secció, línia, paràgraf,
   temps o cel·la. Si falta OCR, transcripció o un lector compatible, registra
   el motiu i l'abast llegit a pendents. No acceptis una font parcial com a
   completa. Revisa figures i taules decisives amb les eines adequades.
4. Crea una fitxa per font coherent a `wiki/fonts/`. Si una font té diversos
   fitxers, enumera tots els originals. Si un document molt gran s'ha de
   dividir en notes, registra'n l'abast i conserva una fitxa principal.
   Cerca abans per identificador, procedència, títol i empremta. Una còpia
   exacta pot compartir fitxa, però versions diferents s'han de distingir.
5. Crea o amplia notes temàtiques segons el perfil. Declara totes les fonts
   directes a `sources` i les fitxes a `source_notes`. Per una font modificada
   o desapareguda, cerca dependències a tota la wiki i revisa les afirmacions
   afectades; no et limitis a la fitxa. Marca les conclusions pendents com a
   `needs-review` i explica el motiu, sense esborrar la història.
6. Amb Python revisa `locally_modified_notes` i `missing_notes` de l'inventari abans
   d'editar; en manual, consulta còpies i revisions disponibles. Una nota
   existent sense empremta coneguda també pot ser humana:
   no l'assumeixis propietat de l'agent. Preserva-la i posa una proposta a
   `wiki/propostes/` si no pots integrar el canvi amb seguretat. No acceptis
   una font si encara té dependències en conflicte. Les notes personals són
   de lectura durant aquesta operació.
7. Desa còpies dels fitxers que modificaràs a `.wiki/backups/<execucio>/`.
   Actualitza índex, mapes i registre amb fonts, empremtes disponibles, canvis i pendents.
   No reescriguis tota la volta per una entrada nova.
8. Comprova enllaços amb `links` si uses Python, o obre els destins en manual.
   Verifica metadades, fidelitat i relacions.
   Corregeix destins; no inventis contingut per omplir notes inexistents.
9. En mode amb Python, només després de completar la revisió, executa `accept` per cada fitxer
   font, amb l'empremta capturada abans de llegir-lo i les notes que en
   depenen. Si l'original ha canviat, torna'l a llegir. Un procés interromput
   deixa feina pendent, no una ingestió completada. En manual, documenta
   la lectura, notes dependents i revisió al registre, sense acceptació per empremtes.

`scan` mostra canvis de nom com a baixa i alta i suggereix correspondències
per contingut. Verifica-les, reutilitza la identitat de la font i actualitza
els camins. Les baixes es resolen explícitament; no eliminen res per si soles.
L'inventari no avalua el contingut i el bloqueig de l'eina només protegeix
l'escriptura de l'estat: el bloqueig d'ingestió cobreix tota l'operació.
