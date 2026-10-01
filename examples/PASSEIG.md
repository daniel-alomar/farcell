# Prova Farcell amb una tasca realista

La carpeta inclosa mostra un resultat preparat, no un registre d'una execució
autònoma certificada. Aquest recorregut permet comprovar si la teva IA arriba
a conclusions sustentades i manté la volta amb cura. Utilitza una còpia temporal.

## 1. Comprendre què aporta

Situació: tens apunts de tres assignatures i vols preparar una sessió d'estudi.
Obre `demo/` a Obsidian i comença per `wiki/index.md`. Prova de respondre aquestes
preguntes seguint les notes i els originals; després fes-les a l'agent:

| Petició | Què hauria d'aportar la volta | On comprovar-ho |
|---|---|---|
| «Per què obtenim 2.8 i 4 m/s? Hi ha un error?» | Distingir interval de dades i derivada del model; comparar 2.8 amb 3 m/s quan l'interval és el mateix | [Exercici comparatiu](demo/wiki/exercicis/model-i-dades.md) |
| «Quina connexió hi ha entre càlcul i moviment?» | Explicar aplicació, condicions i unitats amb fonts | [Síntesi entre matèries](demo/wiki/sintesis/matematiques-i-fisica.md) |
| «Qui ha escrit la carta i com ho sabem?» | Distingir resposta inicial i evidència de la continuació | [Lectura revisada](demo/wiki/sintesis/lectura-revisada.md) |
| «Què encara no puc concloure?» | Indicar que falten incerteses de mesura i que la lectura del relat té abast textual | [Model i dades](demo/wiki/exercicis/model-i-dades.md), [font literària](demo/raw/relat-continuacio.md) |

L'avantatge és recuperar una resposta amb el seu raonament i tornar als apunts
sense recordar quin fitxer contenia cada idea. La literatura pot tenir la seva
ruta sense una relació artificial amb les matemàtiques.

## 2. Generar una primera versió

En una carpeta de prova, copia els originals de `demo/raw/` **excepte
`relat-continuacio.md`**. Mantén aquesta continuació fora de la carpeta d'entrada.
Demana a l'agent:

> Utilitza Farcell per organitzar aquests apunts en una volta nova. Crea fitxes,
> connecta els conceptes que es necessiten entre matèries i prepara preguntes
> de repàs. Treballa només amb aquests documents. Conserva les fonts originals.

L'agent pot variar noms i redacció. El que importa és que els enllaços siguin
vàlids i les conclusions sustentades. La pregunta de la carta ha de quedar
indeterminada: la primera entrada no conté ni la signatura ni la declaració.
Les vuit fitxes del resultat inclòs corresponen a l'estat final, després del pas 3.

## 3. Afegir una font i observar el manteniment

Afegeix `relat-continuacio.md` a l'entrada de la còpia temporal i demana:

> Incorpora el nou fragment. Revisa les respostes que en depenen i explica
> què ha canviat. Conserva la interpretació anterior amb el seu context.

El resultat esperat és una fitxa nova, actualització de la pregunta i de les
notes afectades, i una resposta sustentada pel segon fragment. Les notes de
càlcul no necessiten reescriure's per aquesta incorporació. El registre ha
d'explicar les fonts i les notes modificades.

## 4. Comprovar el resultat sense jutjar només el graf

Segueix almenys una afirmació des de la síntesi fins al passatge original.
Comprova que les dades fictícies estan identificades i que cap resultat es
presenta com a mesura real. Una resposta prudent conserva els buits del corpus;
no afegeix una incertesa de mesura ni una verificació d'autoria inexistents.

Per provar la protecció d'edicions, afegeix una anotació pròpia a una nota de
la còpia temporal i demana una actualització relacionada. L'agent ha de conservar
l'anotació o presentar una proposta separada si no pot integrar-la amb seguretat.
Amb Python es detecten empremtes; en manual no s'ha de prometre la mateixa
capacitat automàtica. Les comprovacions del projecte validen fitxers i enllaços,
no garanteixen que qualsevol model segueixi sempre bé aquestes instruccions.
