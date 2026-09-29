# Projecte Farcell

Per modificar la skill, conserva'n l'abast general i l'autonomia del paquet.
L'entrada és `skills/farcell/SKILL.md`; context a `context/product.md`.
No afegeixis dependències de Garbell ni documents d'una volta particular.
Els rols de `agents/` són opcionals i no autoritzen delegació automàtica.
No desis converses a memory/ sense petició de l'usuari. En distribuir, exclou
memòria, originals i notes personals. Usa exemples ficticis identificats.

Proves: python3 -B -m unittest discover -s tests. Paquet: python3 scripts/distribute.py.
Els exemples són opcionals; no els utilitzis com a fonts reals.
