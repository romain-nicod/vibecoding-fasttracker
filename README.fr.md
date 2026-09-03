# Vibecoding Fasttracker

*[English version](README.md)*

Amener un débutant complet à l'**autonomie en vibe coding** — de façon que son IA prenne le relais du
**pilotage** d'un projet, pas seulement de l'écriture du code.

Ce dépôt n'est pas une application. C'est un gabarit : il produit un **paquet de passation** que l'on
remet à quelqu'un qui débute, et que son IA lira pour tenir le cadre à notre place.

---

## La présentation

Une page autonome qui présente le dispositif à quelqu'un qui pourrait l'adopter :
[`presentation.html`](presentation.html). Elle s'ouvre dans un navigateur, sans rien installer.

## Le problème

Un accompagnement au vibe coding échoue toujours au même endroit. On transmet le code, on oublie de
transmettre la méthode. L'IA du débutant se met alors à coder tout ce qu'on lui demande — sans cadre,
sans porte de sortie, sans périmètre fini. Le projet s'éparpille, puis s'arrête.

Le Fasttracker transmet les deux.

## Le principe

**Deux IA, deux rôles, jamais confondus.**

| | L'IA qui code | L'IA qui pilote |
|---|---|---|
| Fait | écrit et exécute le code, dans le dépôt | cadre, conçoit, relit, tient la méthode |
| Ne fait pas | ne décide pas de la méthode | ne touche jamais au code |

**Un format d'étape imposé.** Avant chaque étape, l'IA pilote rappelle, dans cet ordre : le cadre de
l'étape · les livrables · ce qui est attendu d'elle et du destinataire · les prérequis · ce que le
destinataire doit valider · les outils utilisés · l'étape suivante. **Aucune étape ne s'enchaîne sans
validation explicite de la précédente.**

**Un double rôle pour l'IA pilote.** Garante de la solution — architecte, QA, gardienne de la méthode
et des portes de sortie. Et mentor — elle fait monter le destinataire en compétence sur ce qu'il doit
comprendre pour rester aux commandes, sans jamais le noyer de jargon.

**Un seul lot ouvert à la fois.** C'est la règle qui protège le projet d'un chantier qui n'aboutit
jamais.

---

## Les deux bouts de la chaîne

🔴 Ne jamais les confondre — c'est l'erreur qui produit un gabarit qui parle au mauvais interlocuteur.

| | Qui | Avec quoi |
|---|---|---|
| **Celui qui prépare** la passation | l'accompagnant | la **skill Claude** de ce dépôt |
| **Celui qui reçoit** la passation | le débutant | **son IA à lui** — ChatGPT, Claude, autre |

## Ce que contient ce dépôt

| Dossier | Contenu |
|---|---|
| `templates/` | les gabarits de livrables, avec leurs placeholders — **la source du figé** |
| `skill/vibecoding-fasttracker/` | la skill Claude : le jugement (quoi remplir, ce qui rend un livrable bon), jamais le texte figé |
| `examples/` | les cas réels, en pointeur vers leur dépôt |

---

## Mise en route — côté accompagnant

1. Installe la skill dans ta configuration Claude Code :

```bash
cp -R skill/vibecoding-fasttracker ~/.claude/skills/
```

2. Ouvre une session Claude Code dans le dépôt du projet à passer, et invoque la skill :

```
/vibecoding-fasttracker
```

3. Elle te demande ce qu'elle ne peut pas deviner — qui reçoit, quel projet, quelle IA côté
   destinataire, quels outils — puis produit le paquet de passation dans `docs/refonte/` (ou le
   dossier que tu lui indiques).

4. Relis, complète ce qu'elle a marqué `⚠️ À TRANCHER`, committe, et donne au destinataire l'adresse
   du dépôt. Son point d'entrée est le `README.md` du paquet.

🔴 **La skill s'édite ici, jamais dans `~/.claude/skills/`.** Ce dossier-là est une installation ;
une modification faite là-bas est perdue à la prochaine copie.

## Mise en route — côté destinataire

Le destinataire n'ouvre **jamais** un terminal. Le paquet qu'il reçoit lui donne, pour chaque geste :
la page où aller, le bouton exact à cliquer, et ce qu'il doit voir à la fin pour savoir que c'est
réussi. Il commence par le `README.md` du paquet et ne lit rien d'autre tant qu'il n'a pas fini.

---

## Sa place face à `kickoff`

🔴 **Les deux ne se recouvrent pas.** Ne jamais appliquer les deux au même dépôt sans arbitrage
explicite : ils écriraient les mêmes sujets sous des noms de fichiers différents.

| | [`kickoff`](https://github.com/romain-nicod/kickoff) | Vibecoding Fasttracker |
|---|---|---|
| Pour qui | quelqu'un qui sait déjà mener un projet | quelqu'un qui débute complètement |
| Ce qu'il installe | la méthode dans un dépôt : DoR/DoD, spec → issues, jalons, board | la passation vers une IA tierce, et la montée en compétence de l'humain |
| Ce qu'il suppose acquis | terminal, Git, GitHub | rien |

Le Fasttracker **renvoie** à `kickoff` pour toute la méthode de projet. Il ne réécrit pas sa
Definition of Done et ne redéfinit pas ses jalons. Une règle de méthode qui change, change là-bas.

## Deux langues, côte à côte

Les gabarits de livrables existent dans les deux : `templates/en/` et `templates/fr/`. Choisissez la
langue du destinataire, c'est lui qui les lit.

Les deux jeux sont indépendants, placeholders compris (`{{DESTINATAIRE}}` contre `{{RECIPIENT}}`),
de sorte que chacun se lit comme s'il avait été écrit dans cette langue plutôt que traduit vers elle.
Ajouter une troisième langue, c'est ajouter un dossier, pas restructurer quoi que ce soit.

## Licence

[CC BY 4.0](LICENSE). Réutilisez, adaptez, vendez ce que vous en tirez. Gardez
le crédit visible, comme l'explique [`NOTICE`](NOTICE).
