## Exercici 1
> Quantes branques hi ha ara al repositori?

**Branques locals:**
main (la branca principal)
feature/faq (d'Anna) Alex
feature/api-reference (de Bernat) Airald
→ 3 branques locals (suposant que parteixen de main).
**Branques remotes (al servidor, origin):**
origin/main
origin/feature/faq
origin/feature/api-reference
→ 3 branques remotes.

> Com veus les branques remotes?

Amb la comanda de git branch -r

> Si vols veure els canvis de l'Anna sense canviar de branca, quina comanda faries servir?

git diff Anna

---

## Exercici 2
> Què passa amb les branques feature/faq i feature/api-reference després del merge?

Un cop fusionades a main, les branques continuen existint tant en local com al remot. El merge no les esborra automàticament. GitHub ofereix un botó opcional per esborrar-les just després de fer el merge, però si no el cliques, es queden al repositori com a branques antigues que ja no tenen canvis respecte a main.

> Com elimines una branca remota que ja no necessites?

Amb el comandament de Git:
git push origin --delete nom-branca
(Per exemple: git push origin --delete feature/faq).
També es pot fer directament des de la pàgina web de GitHub a la secció de "Branches" del repositori, fent clic a la icona de la paperera.

> Per què és important esborrar les branques després de fusionar-les?

Neteja i claredat: Evita tenir un llistat de branques ple de noms de feines ja acabades, cosa que dificulta trobar les branques actives.

Evita confusions: Impedeix que algú pensi que encara hi ha feina pendent en aquella branca i faci canvis per error.

Bones pràctiques: És l'estàndard en fluxos de treball com Git Flow. Un cop la feina està a main, la branca temporal ja no serveix per a res.

