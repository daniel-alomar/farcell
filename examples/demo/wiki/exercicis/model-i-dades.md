---
id: "demo-exercicis-model-i-dades"
type: "procedure"
status: "draft"
created: "2026-10-01"
updated: "2026-10-01"
tags: ["demostracio", "connexio-entre-materies"]
sources: ["raw/moviment.md", "raw/mesures-moviment.md"]
source_notes: ["wiki/fonts/moviment", "wiki/fonts/mesures-moviment"]
---

# Per què 2.8 m/s no substitueix 4 m/s?

**Problema:** el model dona 4 m/s en t=2 s, però la taula dona 2.8 m/s
entre 1 i 2 s. S'ha comès un error?

1. Identifica què es calcula: instantània en el model davant mitjana en un
   interval de dades ([[raw/moviment#2. Velocitat mitjana i instantània|model]];
   [[raw/mesures-moviment#2. Velocitats mitjanes|taula]]).
2. Calcula una magnitud comparable: en el model, la mitjana en [1,2] és
   (4-1)/(2-1)=3 m/s. En la taula, és 2.8 m/s. Aquest càlcul intermedi
   és una deducció aritmètica de les posicions originals.
3. La diferència comparable és -0.2 m/s. Sense incerteses, no la converteixis
   en prova concloent contra el model ([[raw/mesures-moviment#3. Comparació amb el model|secció 3]]).

**Resposta:** els dos primers nombres representen magnituds diferents.
La [[wiki/conceptes/velocitat|velocitat]] connecta amb la
[[wiki/conceptes/derivada|derivada]], però derivar un model continu no equival
a calcular diferències finites sobre qualsevol taula.

**Pregunta oberta:** quina informació de mesura caldria per valorar l'ajust?
Els apunts no aporten aquesta informació.
