# AGENTS.md — vibecoding-fasttracker

> 🔴 **La mémoire de ce dépôt vit dans le vault**, pas ici :
> `~/Documents/Claude/ObsiClaud/dev/vibecoding-fasttracker/`
> Ce fichier ne porte que les règles de travail sur ce dépôt.

> ⚙️ Règles de travail communes : `~/Documents/Claude/CLAUDE.md`.

## Ce qu'est ce dépôt

Un gabarit pour **amener un débutant complet à l'autonomie en vibe coding**. Il produit un paquet de
passation : ce qu'il faut donner à l'IA du destinataire pour qu'elle prenne le relais du pilotage
d'un projet, et ce qu'il faut donner au destinataire pour qu'il installe tout ça sans rien
comprendre à la technique.

Premier cas réel : la passation d'une application de gestion à son dirigeant (`examples/`).

## Les deux bouts de la chaîne, à ne jamais confondre

| | Qui | Outil |
|---|---|---|
| **Celui qui prépare** la passation | l'accompagnant | la skill Claude de ce dépôt |
| **Celui qui reçoit** la passation | le débutant | son IA à lui — ChatGPT, Claude, autre |

La skill de ce dépôt est une **skill Claude**. Ce qu'elle produit peut viser n'importe quelle IA.
Une confusion entre les deux produit une skill qui parle au mauvais interlocuteur.

## 🔴 Les règles absolues

1. **La skill ne contient aucun texte de méthode.** Elle dit quel document remplir et ce qui le rend
   bon — jamais ce que le document dit. `templates/` est l'unique source du figé. C'est la même
   règle anti-divergence que dans `kickoff`, et pour la même raison : deux textes de méthode
   divergent toujours.
2. **Ce dépôt ne réécrit pas la méthode de `kickoff`.** DoR/DoD, spec → issues, jalons, board : ça
   vit dans `romain-nicod/kickoff`, on y renvoie. Une règle de méthode qui change, change là-bas.
3. **Aucun nom propre de client dans `templates/` ni dans `skill/`.** Un gabarit qui porte le métier
   d'un client n'est plus un gabarit. Les cas réels vivent dans `examples/`, et seulement en
   pointeur — jamais en copie.
4. **Le destinataire n'ouvre jamais un terminal.** Tout ce que les gabarits lui demandent se fait
   dans une interface web ou une application, avec la page, le bouton, et ce qu'il doit voir à la
   fin. Une commande shell dans un livrable destinataire est un bug.
5. **Un seul lot ouvert à la fois** est la règle que le dispositif protège. Tout gabarit qui laisse
   ouvrir deux chantiers en parallèle est à corriger.

## Structure

| Dossier | Contenu |
|---|---|
| `templates/` | les gabarits de livrables, avec leurs placeholders. La source du figé. |
| `skill/vibecoding-fasttracker/` | la skill Claude : le jugement, jamais le texte figé. Installée par copie dans `~/.claude/skills/` — **on l'édite ici, jamais là-bas**. |
| `examples/` | les cas réels, en pointeur vers leur dépôt. Jamais de copie. |

## Langue

Français pour tout : documentation, gabarits, commits. Les identifiants de fichiers et de dossiers
restent en `kebab-case` ASCII.
