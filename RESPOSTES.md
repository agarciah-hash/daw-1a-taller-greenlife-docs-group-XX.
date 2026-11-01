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
---

## Exercici 3
> Per què s'ha produït el conflicte?

Perquè l'Anna i en Bernat han modificat el mateix fitxer (README.md) alhora partint d'una base comuna. Quan l'Anna ha pujat els seus canvis a main, la branca del Bernat s'ha quedat desactualitzada i Git no sap quina de les dues versions noves ha de prevaler.

> Com es podria haver evitat?

Actualitzant la branca de treball amb git pull origin main (o fent un git rebase) just abans de fer el merge. També evitant que dues persones toquin el mateix fitxer alhora (per exemple, creant fitxers separats).

> Què passaria si haguessin modificat la mateixa línia exactament?

Passaria el mateix (conflicte), però en lloc de veure les dues seccions senceres, el conflicte estaria dins de la mateixa línia. A l'hora de resoldre'l, no podries mantenir les dues opcions per separat; hauries d'escollir-ne una o inventar-te una línia nova que combini el text
---

## Exercici 4

> Diferència entre git revert i git reset?

git revert: no reescriu l'historial, crea un nou commit que desfà els canvis. Segur en branques públiques.

git reset: reescriu l'historial movent el punter enrere i descartant commits. Perillós si ja s'ha publicat.

> Quan és segur fer git push --force?
Només quan ningú altre ha estirat ni treballat en aquesta branca. En equips, millor usar --force-with-lease o evitar-ho.

> Com recuperaries un canvi revertit?
Fent git revert del commit de reversió (o git cherry-pick del commit original)
---

## Exercici 5
> Per què és útil tenir branques de release?

Permeten estabilitzar una versió (proves finals, correccions d'última hora, ajustos de versió) sense afectar el desenvolupament continu de main. Així l'equip pot seguir afegint funcionalitats noves mentre es prepara el llançament, i un cop llesta, es fusiona a main i s'etiqueta.

> Què és un tag i per què és important?

Un tag és una referència fixa i immutable a un commit concret (per exemple v1.0). És important perquè marca de manera permanent un punt de llançament, facilita la traçabilitat de versions, permet revertir o consultar exactament què es va publicar, i no es mou com les branques.

> Com veus tots els tags del repositori?

git tag
---

## Exercici 6

> Per què és útil vincular commits amb issues (`Fixes #1`)?

Vincular els commits amb les issues utilitzant paraules clau com `Fixes #1`, `Closes #1` o `Resolves #1` millora el flux de treball:

* **Tancament automàtic:** En fer el *merge* de la branca a la branca principal (`main`), GitHub tanca la issue automàticament sense haver de fer-ho manualment.
* **Traçabilitat:** Permet saber quin codi exacte (quins commits) ha resolt un problema o implementat una funcionalitat concreta.
* **Historial clar:** La pàgina de la issue mostra tot el registre de canvis relacionats, facilitant la consulta futura.

> Com es veuen els issues tancats a GitHub?

Els issues tancats es distingeixen pels següents elements a la interfície de GitHub:

* **Icona i color:** L'estat canvia de verd (obert) a un **color lila/violeta** amb la icona de tancat o *completed*.
* **Filtres de llista:** Es traslladen de la pestanya **Open** a la pestanya **Closed** en el llistat d'issues del repositori.
* **Historial i referència:** Al final de la conversa de la issue apareix una línia de temps que indica quin *commit* o *Pull Request* va provocar el seu tancament i qui ho va executar.

> Què passaria si dos desenvolupadors treballen en el mateix issue?

Si dos membres de l'equip treballen en el mateix issue de manera independent:

* **Duplicitat d'esforç:** Ambdós estaran resolent el mateix problema, la qual cosa suposa una pèrdua de temps per al projecte.
* **Conflictes de fusió (*Merge Conflicts*):** En intentar fusionar les dues branques a `main`, Git detectarà canvis coincidents en els mateixos fitxers i bloquejarà el merge fins que es resolguin els conflictes manualment.
* **Coordinació necessària:** Per evitar-ho, és una bona pràctica assignar la issue a un sol desenvolupador (*Assignee*) abans de començar a escriure codi.