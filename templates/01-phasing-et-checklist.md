# Gabarit — Phasing et checklist (livrable n° 3)

> **Ce gabarit devient `01-phasing-et-checklist.md` dans `{{DOSSIER_PAQUET}}`.**
> Il a **deux lecteurs** : l'IA qui pilote, qui s'en sert de carte pour cadrer chaque étape, et le
> destinataire, qui s'en sert pour se repérer — où on en est, ce qui reste, ce qu'on ne fait **pas**
> maintenant.
>
> 🔴 **Une étape sans porte de sortie n'est pas une étape.** Une liste d'étapes sans critère de passage
> n'est pas un plan, c'est une intention. Chaque porte de sortie se formule comme un **geste que le
> destinataire fait lui-même et dont il constate le résultat à l'écran** — jamais comme une relecture
> de code, jamais comme un « c'est bon ».
>
> 🔴 **Aucune commande de terminal ici.** Le destinataire n'en ouvre jamais. Tout ce qu'on lui demande
> se fait dans une page web ou une application, avec le bouton et ce qu'il doit voir à la fin.
>
> 🔴 **Ne réécris pas la méthode de projet** — « prêt à démarrer » / « fini », spécification qui génère
> le backlog, jalons, board vivent dans `{{DEPOT_METHODE}}`. On y **renvoie**, on ne les recopie pas.

## Placeholders de ce gabarit

🔴 **Cette section se retire du livrable produit.**

| Placeholder | À quoi il correspond | Exemple |
|---|---|---|
| `{{PROJET}}` | le nom du projet ou de l'application | `Facturation Atelier` |
| `{{ORGANISATION}}` | l'entreprise ou la structure du destinataire | `l'atelier` |
| `{{DESTINATAIRE}}` | le prénom de celui qui reçoit la passation et qui pilotera | `Camille` |
| `{{ACCOMPAGNANT}}` | le prénom de celui qui passe la main | `Alex` |
| `{{NOM_COPILOTE}}` | le nom donné à l'IA qui pilote | `Copilote Atelier` |
| `{{IA_QUI_PILOTE}}` | la forme de cette IA — assistant configuré, espace de projet, prompt | `un assistant configuré` |
| `{{IA_QUI_CODE}}` | l'outil qui écrit et exécute le code | `Codex` |
| `{{ABONNEMENT_IA}}` | le plan payant qui donne accès aux deux IA | `ChatGPT Pro` |
| `{{DEPOT}}` | le chemin court du dépôt | `mon-orga/facturation-atelier` |
| `{{URL_DEPOT}}` | l'adresse web complète du dépôt | `https://github.com/mon-orga/facturation-atelier` |
| `{{PLATEFORME_DEPOT}}` | l'hébergeur du dépôt | `GitHub` |
| `{{DOSSIER_PAQUET}}` | le dossier du dépôt qui porte ce paquet de passation | `docs/refonte/` |
| `{{DOSSIER_DOC_METIER}}` | le ou les dossiers du dépôt qui portent déjà la doc métier | `docs/product/` et `docs/specs/` |
| `{{DOSSIER_SPEC}}` | le dossier où atterrissent spécification et stories — **celui qui fait foi** | `docs/specs/` |
| `{{TABLEAU_SUIVI}}` | l'outil qui porte l'avancement, une carte par story | `le tableau Projects du dépôt` |
| `{{WIKI}}` | l'espace où un humain vient lire décisions et procédures, hors du code | `le wiki du dépôt` |
| `{{DEPOT_METHODE}}` | le dépôt gabarit de méthode auquel on renvoie | `mon-orga/kickoff` |
| `{{HEBERGEUR}}` | où l'application est mise en ligne — sur le compte de l'accompagnant | `Fly.io` |
| `{{COUT_HEBERGEUR}}` | ce que l'hébergement coûte par mois, une fois en ligne | `~8 $/mois` |
| `{{DEVISE_LOCALE}}` | la devise dans laquelle le destinataire raisonne au quotidien | `euros` |
| `{{STACK}}` | la stack cible, en une expression courte | `Laravel + MySQL` |
| `{{STACK_ACTUELLE}}` | ce qui fait tourner l'application aujourd'hui | `un générateur no-code et sa base hébergée` |
| `{{OUTIL_SCHEMA}}` | l'outil de croquis et de maquette que le destinataire manipule | `Excalidraw` |
| `{{LISTE_MODULES}}` | les modules fonctionnels, **dans l'ordre de valeur**, séparés par des virgules | `dossiers, intervenants, interventions, planning, tableau de bord` |
| `{{MODULE_PIVOT}}` | celui des modules qui porte le cœur du métier et pèse le plus lourd | `interventions` |
| `{{ROLE_ADMIN}}` | le rôle qui voit et peut tout | `administrateur` |
| `{{ROLE_RESTREINT}}` | le rôle limité, celui sur qui porte le contrôle de non-régression | `intervenant` |
| `{{DONNEE_SENSIBLE}}` | ce que `{{ROLE_RESTREINT}}` ne doit voir **nulle part** | `les données de rémunération` |
| `{{APPAREIL_CIBLE}}` | l'appareil sur lequel la validation réelle se fait | `ton téléphone` |
| `{{VOLUME_DONNEES}}` | ce qu'il y a à migrer, en volume réel | `environ 200 dossiers, 40 intervenants et trois ans d'historique` |
| `{{DUREE_SECOURS}}` | combien de temps l'ancienne application reste accessible en secours | `2 mois` |
| `{{PREMIERE_FONCTIONNALITE_APRES}}` | la première fonctionnalité neuve, nommée d'avance | `l'envoi automatique du récapitulatif hebdomadaire` |
| `{{VERSION}}` | la version du document | `v01` |
| `{{DATE}}` | la date de dernière modification | `25/08/2026` |

---
---

# {{PROJET}} — le plan de vol

*Ce chapeau dit à qui sert le document et comment on s'en sert. Il doit tenir en un écran : un
destinataire qui ouvre ce fichier pour la première fois ne doit pas avoir l'impression d'un pavé à
lire d'un bout à l'autre.*

Ce document est le **plan de vol** : les étapes dans l'ordre, ce que chacune produit, et la **porte de
sortie** que tu franchis explicitement avant de passer à la suivante. Il ne remplace pas
{{NOM_COPILOTE}} — il lui sert de carte : à chaque nouvelle conversation, tu peux lui dire « on est à
l'étape 5, ouvre-la » et il saura exactement quoi cadrer. Toi, tu t'en sers pour te repérer : où on en
est, ce qui reste, et ce qu'on ne fera **pas** maintenant.

Tu n'as pas à le lire d'un bout à l'autre aujourd'hui. Lis le chapeau, regarde le schéma ci-dessous,
puis ouvre seulement la section de l'étape en cours. La checklist en fin de document te donne ta
progression d'un coup d'œil.

> **Prérequis** : la mise en route décrite dans le `README.md` de `{{DOSSIER_PAQUET}}` est faite —
> accès au dépôt, {{IA_QUI_CODE}} synchronisé, {{NOM_COPILOTE}} créé, {{OUTIL_SCHEMA}} prêt. C'est
> l'étape 1 ci-dessous, et ce document reprend juste après.

---

## Les règles non négociables

*Trois règles, jamais plus. Ce sont elles qui tiennent tout le reste du document : chaque étape n'est
que leur application à un moment précis. Si tu en ajoutes une quatrième, vérifie qu'elle n'est pas la
conséquence d'une des trois — une liste de règles qu'on ne retient pas ne protège rien.*

**1. Un seul lot ouvert à la fois.** Jamais deux chantiers en parallèle. Si une bonne idée surgit au
milieu d'une étape, {{NOM_COPILOTE}} la note dans une liste « plus tard » et on n'y touche pas. C'est
la règle qui empêche un projet de s'étaler indéfiniment.

**2. On termine à iso-fonctionnel avant d'ajouter quoi que ce soit de neuf.** *Iso-fonctionnel* veut
dire : la nouvelle application fait **exactement** ce que fait l'actuelle, ni plus ni moins. Aucune
fonctionnalité nouvelle n'entre avant l'étape 11. La première d'entre elles est déjà connue :
{{PREMIERE_FONCTIONNALITE_APRES}}. Elle attend son tour.

**3. Une étape ne s'ouvre pas tant que la précédente n'est pas validée par toi, explicitement.** Pas
« ça a l'air bon » — un « je valide l'étape N » écrit dans la conversation avec {{NOM_COPILOTE}}.
C'est ce qui te garde aux commandes.

---

## Vue d'ensemble

*Le schéma ci-dessous est un **squelette générique** : remplace les libellés entre chevrons par ceux
du projet, et rien d'autre.*

🔴 **Trois règles pour ne pas le casser :**

1. **Largeur fixe.** Chaque libellé doit tenir dans sa cellule sans la déborder ni la raccourcir. Si
   un nom de module est trop long, abrège-le dans le schéma — le nom complet vit dans la section de
   l'étape.
2. **Aucun caractère double-chasse.** Pas d'emoji, pas d'idéogramme, pas de symbole exotique à
   l'intérieur du bloc : ils occupent deux colonnes à l'affichage et décalent tout le cadre. Les
   accents latins, eux, ne posent aucun problème.
3. **Un schéma qui ment est pire que pas de schéma.** Si tu ajoutes ou retires une étape, le bloc se
   refait — il ne se laisse pas dériver.

```text
 ┌────────────────────────┐    ┌────────────────────────┐    ┌────────────────────────┐
 │ 1  Mise en route       │    │ 5  Socle technique     │    │ 8  Les écrans          │
 │    outils, accès,      │    │    + une page VIDE     │    │    a. <module 1>       │
 │    IA pilote créée     │    │      déjà EN LIGNE     │    │    b. <module 2>       │
 ├────────────────────────┤    ├────────────────────────┤    │    c. <MODULE PIVOT>   │
 │ 2  Cadrage             │    │ 6  Structure des       │    │    d. <module 4>       │
 │    périmètre gelé      │──► │    données             │──► │    e. <module 5>       │
 │    budget annoncé      │    │    pièges repris       │    │    f. <module 6>       │
 ├────────────────────────┤    ├────────────────────────┤    ├────────────────────────┤
 │ 3  Dépôt & méthode     │    │ 7  Connexion & droits  │    │ 9  Migration des       │
 │    besoins recueillis  │    │    ce que l'ancien     │    │    données réelles     │
 │    backlog dérivé      │    │    socle assurait      │    │    aucune perte        │
 ├────────────────────────┤    └────────────────────────┘    └────────────┬───────────┘
 │ 4  Accès hébergement   │                                               │
 │    donné une fois par  │                                               │
 │    l'accompagnant      │                                               │
 └────────────────────────┘                                               │
                              ┌───────────────────────────────────────────┘
                              ▼
             ┌────────────────┴────────────────┐
             │ 10 Recette et bascule           │
             │    l'ancien reste en secours    │
             │    <durée de secours>           │
             └────────────────┬────────────────┘
                              │
             ═══════ FIN DE LA REFONTE ═══════
                              │
                              ▼
             ┌────────────────┴────────────────┐
             │ 11 <1re fonctionnalité neuve>   │
             │    nommée d'avance              │
             │    — jamais avant               │
             └─────────────────────────────────┘

 ORDRE CONTRAINT — on ne peut pas l'inverser      ORDRE LIBRE — tu choisis
 ───────────────────────────────────────────      ───────────────────────────
 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10 → 11      · l'ordre des modules de
 Chaque étape a besoin du résultat de la            l'étape 8, après le module
 précédente. Sauter, c'est refaire plus tard.       pivot
 Seule exception : l'étape 4, purement            · le rythme : une étape par
 administrative, peut avancer pendant la 3.         semaine ou par mois — ça ne
                                                    change rien à la méthode
```

**Ce que tu lis dans ce schéma** : rien de ce qui produit de la valeur visible (colonne de droite)
n'arrive avant que le socle tienne (colonne du milieu). C'est volontaire. Une application qui affiche
de beaux écrans mais qu'on ne sait pas remettre en ligne après une panne n'est pas livrable.

Et un repère de durée : dans l'étape 8, le module **{{MODULE_PIVOT}}** pèse à lui seul autant que tous
les autres réunis. Si tu as l'impression que le projet piétine à ce moment-là, c'est normal — c'est le
cœur du métier qui se reconstruit.

---

## Étape 1 — Mise en route

*Cette étape existe pour une seule raison : sans elle, toutes les suivantes attendent. Elle ne produit
rien de visible, et c'est exactement pour ça qu'on la traite comme une étape à part entière avec sa
porte de sortie — sinon on la croit faite alors qu'il manque un accès. Son détail pas-à-pas vit dans
le `README.md` de `{{DOSSIER_PAQUET}}` ; ici on ne garde que le rappel et la porte.*

**Objectif** : que {{DESTINATAIRE}} ait ses outils en main et {{NOM_COPILOTE}} en place, avant qu'une
seule décision de projet soit prise.

### Livrables

| Livrable | Ce que c'est |
|---|---|
| **Accès au dépôt {{DEPOT}}** | L'invitation acceptée, le dépôt visible dans son compte {{PLATEFORME_DEPOT}} |
| **{{IA_QUI_CODE}} synchronisé** | Il voit le dépôt et sait y écrire |
| **{{NOM_COPILOTE}} créé** | {{IA_QUI_PILOTE}}, configuré avec le texte du fichier `00-methode-et-roles.md` |
| **{{OUTIL_SCHEMA}} ouvert** | Le compte créé, un croquis d'essai fait et retrouvé |

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{ACCOMPAGNANT}}** | Invite {{DESTINATAIRE}} sur {{DEPOT}} et lui transmet le paquet |
| **{{NOM_COPILOTE}}** | N'existe pas encore — c'est le produit de l'étape |
| **{{IA_QUI_CODE}}** | Se connecte au dépôt |
| **Toi** | Tu suis le `README.md` du dossier, écran par écran |

### 🚪 Porte de sortie

Tu ouvres une conversation avec {{NOM_COPILOTE}}, tu lui écris « on démarre {{PROJET}}, cadre-moi
l'étape 2 », et **il te répond en respectant le format d'étape** — le cadre, les livrables, qui fait
quoi, ce que tu devras valider. S'il répond autre chose, sa configuration n'est pas complète :
reprends le `README.md`.

### Pièges connus

- **Un accès accepté n'est pas un accès vérifié.** Ouvre le dépôt dans ton navigateur et vois-le de
  tes yeux avant de cocher.
- {{NOM_COPILOTE}} ne se resynchronise pas seul avec le dépôt. Chaque fois qu'un fichier de
  `{{DOSSIER_PAQUET}}` change, il faut lui redonner la version à jour — sinon il travaille sur du
  périmé sans te prévenir.

---

## Étape 2 — Cadrage

*C'est l'étape qui décide de la longueur de tout le projet. On y fige trois choses : ce qu'on fait, ce
qu'on ne fait pas, et ce que ça coûte. La section « ce qu'on ne fait pas » est celle qu'on saute
toujours, et c'est celle qui sert le plus : sans liste « plus tard » écrite, chaque bonne idée
rediscute le périmètre.*

**Objectif** : figer noir sur blanc ce qu'on refait, ce qu'on ne refait pas, et ce que ça va coûter en
abonnements — avant qu'une seule ligne de code soit écrite.

### Livrables

| Livrable | Ce que c'est | Où il vit |
|---|---|---|
| **Note de cadrage** | 2 pages : le périmètre, ce qui est explicitement exclu, la date visée | {{NOM_COPILOTE}} la produit ; sa version finale va dans `{{DOSSIER_SPEC}}` |
| **Budget outils** | Un tableau : chaque outil, son coût mensuel, son équivalent annuel en {{DEVISE_LOCALE}} | Dans la note de cadrage |
| **Liste « plus tard »** | Tout ce qui est refusé maintenant, pour ne pas le réinventer trois fois | Dans la note de cadrage, section dédiée |

### Ce qui est déjà tranché — ne le rediscute pas

*Renvoie ici au livrable de contexte, et nomme-le. Le but est qu'une décision déjà prise ne soit
jamais reposée en question par l'IA — c'est ce qui use un débutant plus vite que tout le reste.*

Le fichier `02-contexte.md` de ce dossier contient tout le métier déjà arbitré : structure des
données, règles de gestion, droits de chaque rôle, définitions des chiffres. **Ces décisions font
foi.** {{NOM_COPILOTE}} ne doit pas te les redemander ; si tu le vois le faire, renvoie-le au document
— il a probablement perdu le fil.

Le périmètre est donc simple à énoncer : **tout ce que fait l'application actuelle de
{{ORGANISATION}}, rien de plus.** Ce qui était déjà repoussé le reste.

### Le budget à annoncer

*Le coût s'annonce **avant** l'engagement, et **même quand ce n'est pas le destinataire qui paie** :
ce n'est pas son portefeuille qui est en jeu, c'est sa décision. Donne un ordre de grandeur daté et
dis qu'il est à revérifier — un chiffre non daté sera cité comme une promesse dans six mois.*

🔴 **L'hébergement {{HEBERGEUR}} est sur le compte de {{ACCOMPAGNANT}}, pas sur le tien.** Tu n'ouvres
aucun compte, tu ne donnes aucune carte, et on ne te le demandera jamais. Le tableau ci-dessous te dit
quand même ce que ça coûte : un coût qu'on ne t'annonce pas est un coût qui te surprendra un jour.

| Outil | Ce qu'il fait | Coût | Qui paie |
|---|---|---|---|
| **{{HEBERGEUR}}** | Fait tourner l'application et stocke les données | {{COUT_HEBERGEUR}} | **{{ACCOMPAGNANT}}** — son compte, sa facture |
| **{{ABONNEMENT_IA}}** | {{IA_QUI_CODE}} et {{NOM_COPILOTE}} | déjà payé | toi, déjà en cours |
| {{PLATEFORME_DEPOT}} | Héberge le code | gratuit sur cet usage | — |
| {{OUTIL_SCHEMA}} | Les croquis et maquettes | gratuit | — |
| **Total nouveau** | | **{{COUT_HEBERGEUR}}** | **rien de neuf à ta charge** |

⚠️ Que ce soit la facture de {{ACCOMPAGNANT}} ne veut pas dire qu'on la laisse filer. Le piège
classique est d'oublier un environnement de test allumé pendant deux mois. On n'en créera qu'un seul,
et l'étape 4 te montre où voir la consommation.

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Rédige la note de cadrage, chiffre le budget, ouvre la liste « plus tard » |
| **{{IA_QUI_CODE}}** | Rien. On ne touche pas au code à cette étape |
| **Toi** | Tu lis, tu contestes ce qui te semble faux, tu valides |

### 🚪 Porte de sortie

Tu écris à {{NOM_COPILOTE}} que **tu valides la note de cadrage**, en confirmant trois choses :

1. Le périmètre est bien « tout ce que fait l'application actuelle, rien de plus ».
2. Tu as vu ce que l'hébergement coûte — {{COUT_HEBERGEUR}}, sur le compte de {{ACCOMPAGNANT}} — et tu
   sais que rien de neuf n'est à ta charge.
3. Tu as vu la liste « plus tard » et tu es d'accord pour que rien n'en sorte avant l'étape 11.

### Pièges connus

- **Le piège n° 1 de tout le projet** : « tant qu'on y est, on pourrait aussi… ». Chaque ajout à ce
  stade paraît minuscule et coûte trois semaines. Tout ce qui arrive va dans la liste « plus tard »,
  sans exception, y compris tes propres idées.
- Une refonte dont personne ne sait dire **pourquoi** on refond plutôt que faire évoluer se rediscute
  à chaque difficulté. Si la raison n'est écrite nulle part, c'est un `⚠️ À TRANCHER` — pas une
  justification que {{NOM_COPILOTE}} invente.

---

## Étape 3 — Préparation du dépôt et de la méthode

*L'étape la plus dense du plan, et celle qu'on est le plus tenté de survoler. Elle pose trois choses
d'un coup : **qui recueille les besoins**, **les trois destinations du travail**, et **le fait que le
dépôt est privé par défaut**. Les trois sont des règles de fonctionnement, pas des tâches : une fois
posées, elles gouvernent tout le reste du projet.*

**Objectif** : donner au projet sa colonne vertébrale — les documents de méthode, et une liste de
tâches dérivée d'une spécification écrite, pas réinventée en réunion.

### Qui recueille les besoins — et comment ça se passe

*C'est la responsabilité qu'on oublie le plus souvent d'écrire, et son absence transforme
l'accompagnement en atelier de prise de commande. Écris-la ici même si elle te paraît évidente.*

🔴 **C'est {{NOM_COPILOTE}} qui extrait la spécification, jamais toi qui la rédiges.** Tu connais ton
métier ; la manière d'en faire des fiches de travail, c'est son affaire. Concrètement, il doit :

1. Te faire parler de **ton métier**, pas de l'écran que tu imagines : qui fait quoi, quand, avec quoi
   aujourd'hui, et ce qui coince réellement.
2. Poser des questions **simples, une à la fois**, en langue courante. Un questionnaire de dix points
   d'un coup, tu décroches — et personne ne le saura.
3. **Reformuler et te faire confirmer avant d'écrire** quoi que ce soit.
4. Rédiger ensuite au format story — rôle, action, bénéfice — avec des critères **vérifiables à
   l'écran**, un identifiant et une priorité.
5. Te faire **valider chaque story dans tes mots à toi**. Si tu ne sais pas la redire, elle n'est pas
   comprise : on reprend au point 3.

### Trois endroits, trois usages — à ne jamais mélanger

*C'est la règle qui évite le pire travers de ce genre de projet : la même information à deux endroits,
qui finit par dire deux choses différentes sans que personne s'en aperçoive. Nomme les trois
emplacements et dis lequel fait foi.*

| Emplacement | Ce qu'il porte | Fait foi |
|---|---|---|
| **Le dépôt** — `{{DOSSIER_SPEC}}` | la spécification et les stories, en fichiers | 🔴 **oui** |
| **{{TABLEAU_SUIVI}}** | l'avancement : une carte par story, **dérivée** des fichiers | non — se régénère |
| **{{WIKI}}** | décisions et leur raison, procédures, mode d'emploi | pour son sujet seul |

- Une carte de {{TABLEAU_SUIVI}} ne se saisit **jamais à la main en premier**. Si une carte contredit
  un fichier, **le fichier gagne** et la carte se régénère.
- **Jamais de spécification en double dans {{WIKI}}.** Il porte le pourquoi et le comment-faire, pas
  le quoi.
- 🔴 **Le dépôt {{DEPOT}} est privé par défaut.** Son passage en public est une décision de
  {{ACCOMPAGNANT}}, jamais un effet de bord : un débutant qui découvre les réglages d'un dépôt peut le
  publier sans mesurer ce qu'il expose.

⚠️ **À TRANCHER si ce n'est pas déjà fait — qui exécute concrètement** la création des cartes et des
pages de {{WIKI}} ? {{NOM_COPILOTE}} n'a pas d'accès, {{IA_QUI_CODE}} ne peut pas toujours appeler une
API, et tu n'as pas toujours les droits. Nomme qui fait le geste, outil par outil.

### Livrables

| Livrable | Ce que c'est |
|---|---|
| **Documents de méthode** dans le dépôt | Importés de `{{DEPOT_METHODE}}`, **pas réécrits** |
| **Note de cadrage mise au format du projet** | Celle de l'étape 2, rangée dans `{{DOSSIER_SPEC}}` |
| **Backlog généré** | Les fiches de travail, dérivées de `{{DOSSIER_DOC_METIER}}` |
| **{{TABLEAU_SUIVI}}** | Le tableau d'avancement, une carte par story |
| **{{WIKI}} activé** | Vide au départ. Il se remplira de décisions et de procédures |
| **Jalons** | Un jalon par étape 5 à 10 de ce document, pour voir la progression |

### Les deux portes de la méthode

*Ne les réécris pas ici.* « Prêt à démarrer » et « fini » sont définis dans `{{DEPOT_METHODE}}`, qui
fait foi. Le rôle de {{NOM_COPILOTE}} à cette étape est de te les **expliquer en langue courante**,
une fois, avec un exemple tiré de ton propre métier — puis de les tenir. Ton rôle est de lui demander
« c'est fini selon la définition ? » chaque fois qu'il te dit qu'une tâche est terminée.

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Mène le recueil des besoins, rédige les stories, prépare le contenu des documents, relit le backlog généré et te signale les trous |
| **{{IA_QUI_CODE}}** | Importe les documents de méthode et exécute la génération des fiches |
| **{{ACCOMPAGNANT}}** | Donne les accès ; crée {{TABLEAU_SUIVI}} et active {{WIKI}} tant que tu n'as pas les droits. Le dépôt reste **privé** |
| **Toi** | Tu réponds aux questions sur ton métier, tu valides chaque story dans tes mots, tu relis la liste des fiches |

### 🚪 Porte de sortie

Deux choses, ensemble :

1. Tu ouvres [{{URL_DEPOT}}]({{URL_DEPOT}}) dans ton navigateur et tu y vois **une liste de fiches
   étiquetées, regroupées par module**. Tu la parcours et tu dis à {{NOM_COPILOTE}} : « je valide le
   backlog », ou tu lui signales ce qui manque.
2. Tu sais dire, **sans relire ce document**, où vivent la spécification, l'avancement et les
   décisions — les trois endroits, et lequel fait foi.

### Pièges connus

- **Le backlog ne se saisit pas dans {{TABLEAU_SUIVI}}.** Il se rédige dans `{{DOSSIER_SPEC}}`, et le
  tableau en découle. Une carte créée à la main est une information qui n'existe nulle part ailleurs :
  elle sera perdue à la première régénération.
- **{{WIKI}} n'est pas un deuxième cahier des charges.** Dès que tu vois une spécification recopiée
  dedans, dis-le : il y a maintenant deux vérités, et l'une des deux est déjà fausse.
- Le dépôt contient déjà l'application actuelle. **On ne l'efface pas** : elle reste en ligne et sert
  de référence jusqu'à l'étape 10. Où ranger le nouveau code sans écraser l'existant est une décision
  à prendre explicitement ici, pas à improviser.

---

## Étape 4 — Accès à l'hébergement

*L'étape la plus administrative, la seule qui dépende d'une action de l'accompagnant, et celle où se
joue l'autonomie de tout le dispositif. Écris-la comme un **octroi unique**, jamais comme un rituel de
demande : si chaque mise en ligne repasse par l'accompagnant, le projet s'arrête au premier délai de
réponse.*

**Objectif** : que {{IA_QUI_CODE}} puisse mettre en ligne, et que **tu** aies accès à l'application
qui la recevra — sans repasser par {{ACCOMPAGNANT}} pour le travail courant.

🔴 **L'application vit sur le compte {{HEBERGEUR}} de {{ACCOMPAGNANT}}, pas sur le tien.** Tu n'ouvres
aucun compte, tu ne donnes aucune carte bancaire, et **personne ne doit te le demander** — ni
{{NOM_COPILOTE}}, ni {{IA_QUI_CODE}}, ni {{ACCOMPAGNANT}}. Si on te le demande un jour, c'est une
erreur : signale-la.

Ce que {{ACCOMPAGNANT}} fait, **une fois** : il crée l'application sur son compte et **t'ajoute comme
collaborateur**. À partir de là, **tu es autonome** — tu mets en ligne, tu consultes les journaux, tu
vois le tableau de bord.

### Livrables

| Livrable | Ce que c'est |
|---|---|
| **Environnement de {{IA_QUI_CODE}} opérationnel** | La stack {{STACK}} installée là où il travaille |
| **Application {{HEBERGEUR}} créée** — vide | Créée par {{ACCOMPAGNANT}} **sur son compte**, avec son nom exact noté |
| **Ton accès collaborateur** | L'invitation acceptée : l'application apparaît dans ton tableau de bord |
| **Accès de mise en ligne pour {{IA_QUI_CODE}}** | La clé branchée dans sa configuration |

### Ce que tu fais toi, pas à pas

**Aucune commande de terminal ne t'est demandée** — ni ici, ni nulle part dans ce document.
{{IA_QUI_CODE}} exécute ; toi, tu cliques dans des pages web.

**A. Envoyer la demande à {{ACCOMPAGNANT}}** — tu n'écris pas ce message toi-même : **{{NOM_COPILOTE}}
te le rédige, prêt à envoyer**, avec ses quatre points (ce qui est demandé · pourquoi maintenant · ce
qui est bloqué en attendant · ce que tu dois recevoir en retour). Il doit y ajouter, dans la foulée,
**ce que tu peux avancer pendant l'attente**. Une demande envoyée ne met jamais tout le projet à
l'arrêt.

**B. Accepter l'invitation** — tu reçois un e-mail de {{HEBERGEUR}} (regarde tes spams, il y atterrit
souvent). Le lien te demandera de créer un identifiant **gratuit**, sans carte bancaire : la carte est
déjà celle de {{ACCOMPAGNANT}}. **Ce que tu dois voir à la fin** : l'application apparaît dans ton
tableau de bord, avec la mention « collaborateur ». Elle est vide, c'est normal.

**C. Repérer les trois écrans dont tu te serviras vraiment** — l'état de l'application, l'historique
des mises en ligne (c'est là que tu verras arriver le travail de {{IA_QUI_CODE}}), et les journaux
(c'est ce qu'on te demandera de regarder le jour où quelque chose ne répond plus).

**D. Donner l'accès de mise en ligne à {{IA_QUI_CODE}}** — {{NOM_COPILOTE}} te guidera le moment venu.
Cette clé est un secret : elle se colle dans la configuration de {{IA_QUI_CODE}}, **jamais dans une
conversation**, jamais dans un fichier du dépôt.

### Ce qui reste chez {{ACCOMPAGNANT}}, même après

| Ce qui reste chez lui | Pourquoi |
|---|---|
| L'octroi des accès ({{HEBERGEUR}}, {{PLATEFORME_DEPOT}}) | ce sont ses comptes |
| Tout ce qui touche au **plan payant** | c'est sa carte |
| Toute bascule d'un **dépôt en public** | le dépôt est privé par défaut |

Tout le reste — mettre en ligne, lire les journaux, redémarrer, regarder le tableau de bord — est à
toi.

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{ACCOMPAGNANT}}** | Crée l'application sur **son** compte, t'ajoute comme collaborateur, renvoie le nom exact |
| **{{NOM_COPILOTE}}** | Rédige la demande prête à envoyer, te guide écran par écran, te dit quoi avancer pendant l'attente |
| **{{IA_QUI_CODE}}** | Installe son environnement ; branche la clé de mise en ligne |
| **Toi** | Tu envoies la demande, tu acceptes l'invitation, tu vérifies que tu vois l'application |

### 🚪 Porte de sortie

Trois choses, ensemble :

1. **Tu vois l'application dans ton tableau de bord {{HEBERGEUR}}** (elle est vide, c'est normal), et
   tu sais où sont les journaux.
2. Tu connais **le nom exact de l'application** et il est noté ailleurs que dans un e-mail.
3. {{IA_QUI_CODE}} confirme à {{NOM_COPILOTE}} qu'il peut lancer l'application chez lui.

### Pièges connus

- **Le rituel de demande permanent.** Si tu vois écrit quelque part « demande à {{ACCOMPAGNANT}} avant
  chaque mise en ligne », c'est un bug du dispositif : vérifie que ce n'est pas déjà un accès donné une
  fois pour toutes.
- Un environnement de test oublié allumé coûte tous les mois sans rien produire. On n'en crée qu'un.
- Une clé d'accès collée dans une conversation est une clé compromise. On la révoque et on en refait
  une — on ne « fait pas attention pour la prochaine fois ».

---

## Étape 5 — Le socle technique et une première mise en ligne à vide

*L'étape qui inverse l'ordre intuitif, et c'est tout son intérêt : **« ça déploie » avant « ça
marche »**. Explique le pourquoi, sinon elle passe pour une perte de temps — un projet qui met en
ligne pour la première fois au bout de trois mois découvre au pire moment tout ce qui ne marche que
sur la machine du développeur.*

**Objectif** : qu'une page vide, mais **vraiment en ligne**, soit accessible depuis ton navigateur.
Rien de métier. Juste la preuve que la chaîne complète fonctionne.

### Pourquoi une page vide en ligne, avant tout le reste

Parce que la mise en ligne est l'endroit où l'on découvre les mauvaises surprises, et qu'on veut les
découvrir **maintenant**, quand il n'y a rien à perdre. Une fois cette page en ligne, chaque module de
l'étape 8 part en ligne dès qu'il est fini — jamais accumulé.

### Livrables

| Livrable | Ce que c'est |
|---|---|
| **Le squelette {{STACK}}** | Le projet créé, dans le dépôt |
| **Une page d'accueil vide en ligne** | Une adresse web que tu peux ouvrir depuis {{APPAREIL_CIBLE}} |
| **Le `README.md` du dépôt à jour** | L'adresse en ligne dans ses **premières lignes** |
| **La mise en ligne automatisée** | Un changement accepté part en ligne sans geste manuel |

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Fixe les choix de socle à partir de `03-stack-et-decisions-techniques.md`, relit ce que produit {{IA_QUI_CODE}} |
| **{{IA_QUI_CODE}}** | Crée le projet, le met en ligne, branche l'automatisation |
| **Toi** | Tu ouvres l'adresse et tu confirmes que tu vois la page |

### 🚪 Porte de sortie

Tu ouvres l'adresse de l'application **sur {{APPAREIL_CIBLE}}**, et une page s'affiche — vide, mais
elle s'affiche, et elle s'affiche tout de suite. Tu la recharges cinq minutes plus tard : elle répond
aussi vite.

### Pièges connus

- **« Ça marche chez moi » ne compte pas.** Tant que ce n'est pas ouvert depuis ton propre appareil, à
  ton adresse publique, ce n'est pas en ligne.
- Les décisions de socle listées dans `03-stack-et-decisions-techniques.md` se posent **maintenant**.
  Chacune coûte cher à changer une fois que des données existent.
- Le `README.md` porte l'adresse en ligne dès ses premières lignes, dans **le même changement** que la
  mise en ligne — pas dans une passe de fin.

---

## Étape 6 — La structure de données

*L'étape où l'on reprend l'existant sans le réinventer. Sa valeur tient dans une seule chose : la
liste des **pièges du système actuel traduits en règles vérifiables** dans le nouveau. Un piège connu
qui n'est pas écrit ici sera réintroduit — c'est mécanique.*

**Objectif** : porter la structure de données de l'application actuelle dans {{STACK}}, à
l'identique, sans réintroduire les pièges qu'on a mis des mois à comprendre.

### Livrables

| Livrable | Ce que c'est |
|---|---|
| **La structure créée** | Les tables et leurs liens, dans la nouvelle base |
| **Les garde-fous** | Les contrôles que la base refuse de laisser passer, repris un par un |
| **Le document de structure** dans `{{DOSSIER_DOC_METIER}}` | À jour, relu par toi |
| **Un jeu de données d'essai** | De quoi remplir les écrans de l'étape 8 sans toucher aux vraies données |

### Les pièges à ne pas réintroduire

*Reprends ici, en une ligne chacun, les pièges listés dans `03-stack-et-decisions-techniques.md`.
Numérote-les : la porte de sortie consiste à les cocher un par un, et une liste non numérotée ne se
coche pas.*

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Traduit chaque piège en règle vérifiable, relit la structure produite |
| **{{IA_QUI_CODE}}** | Écrit la structure et les garde-fous |
| **Toi** | Tu relis le document de structure en langue courante et tu dis si un cas de ton métier manque |

### 🚪 Porte de sortie

{{NOM_COPILOTE}} te présente la liste numérotée des pièges et **coche chacun devant toi**, en disant
quelle règle l'empêche de revenir. Tu confirmes que la structure décrit bien ton métier — y compris
les cas tordus que tu es seul à connaître.

### Pièges connus

- **Une structure « améliorée » au passage** est une structure qui ne correspond plus aux données
  réelles qu'on migrera à l'étape 9. On porte, on n'améliore pas.
- Un garde-fou qui vit seulement dans le code, et pas dans la base, saute au premier import de
  données.

---

## Étape 7 — Connexion et droits

*🔴 **L'étape la plus sous-estimée du plan, et le risque de régression n° 1.** L'ancien socle assurait
gratuitement des choses que personne n'a jamais écrites dans un cahier des charges : qui voit quoi,
qui peut faire quoi, ce qui est refusé côté serveur et pas seulement caché à l'écran. Ces garanties
disparaissent avec lui. Cette étape sert à les **réimplémenter nommément** — et la porte de sortie
doit se formuler comme un refus constaté, jamais comme un lien absent.*

**Objectif** : que chacun se connecte, et que ce que l'ancien socle interdisait tout seul soit
maintenant interdit **explicitement**, par du code écrit exprès.

### Ce qu'on installe

| Brique | À quoi elle sert |
|---|---|
| **La connexion** | Identifiant, mot de passe, mot de passe oublié, déconnexion |
| **Les rôles** | {{ROLE_ADMIN}} et {{ROLE_RESTREINT}}, tels que définis dans `02-contexte.md` |
| **Les autorisations** | Un refus **par défaut** : tout ce qui n'est pas explicitement autorisé est refusé |
| **La désactivation d'un compte** | Un compte désactivé perd l'accès immédiatement |

### Ce que l'ancien socle assurait, et qui doit être réécrit

*Liste ici, ligne par ligne, ce que {{STACK_ACTUELLE}} garantissait sans qu'on ait à l'écrire, et la
brique qui le remplace. Le tableau complet vit dans `03-stack-et-decisions-techniques.md` ; ici, on
garde le rappel qui empêche de croire l'étape finie trop tôt.*

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Vérifie la matrice des droits ligne à ligne contre `02-contexte.md`, exige les tests de refus |
| **{{IA_QUI_CODE}}** | Écrit la connexion, les rôles, les autorisations et leurs tests |
| **Toi** | Tu essaies **toi-même** de faire ce que tu ne dois pas pouvoir faire |

### 🚪 Porte de sortie

Le geste, et pas un autre : **tu te connectes avec un compte {{ROLE_RESTREINT}} et tu tapes
directement l'adresse d'un écran réservé à {{ROLE_ADMIN}}.** Tu dois voir un **refus** — pas une page
vide, pas un lien absent. Un lien caché n'est pas une protection : c'est un lien caché.

Puis : tu demandes à {{ACCOMPAGNANT}} ou à {{NOM_COPILOTE}} de désactiver un compte d'essai pendant
que tu es connecté avec, et tu constates que l'accès tombe.

### Pièges connus

- **Cacher n'est pas interdire.** Un bouton qu'on ne voit pas reste atteignable par son adresse.
- {{DONNEE_SENSIBLE}} ne doit apparaître **nulle part** pour {{ROLE_RESTREINT}} : ni à l'écran, ni
  dans un export, ni dans une recherche, ni dans un total qui la laisserait deviner.
- Une autorisation « on verra plus tard » ne se rattrape jamais : à l'étape 8, chaque module ajoutera
  ses propres écrans par-dessus.

---

## Étape 8 — Les écrans, un module à la fois

*L'étape la plus longue. Ce qui la rend tenable, c'est le découpage : **chaque module est un lot
fermé**, et l'ordre est fonctionnel, pas alphabétique. Dis explicitement quel module pèse le plus
lourd — un destinataire qui croit piétiner sur le module pivot s'inquiète pour rien, ou pire, presse
l'IA de bâcler.*

**Objectif** : reconstruire les écrans de l'application actuelle, un module à la fois, chacun mis en
ligne dès qu'il est fini.

**Chaque module est un lot fermé** : on l'ouvre, on le termine, on le valide, on passe au suivant.
Jamais deux en même temps.

### L'ordre, et pourquoi

L'ordre de valeur est : {{LISTE_MODULES}}. Il n'est pas alphabétique, il est **fonctionnel** — chaque
module a besoin du précédent, et le module qui lit tous les autres passe en dernier. Le module
**{{MODULE_PIVOT}}** est le cœur du métier : prévois qu'il pèse autant que tous les autres réunis.

### Ce que chaque module produit, sans exception

| Livrable | Qui le produit | Qui le valide |
|---|---|---|
| **Maquette** des écrans dans {{OUTIL_SCHEMA}}, avec les quatre états : vide, en chargement, en erreur, plein | {{NOM_COPILOTE}} propose, tu ajustes | Toi |
| **Les écrans** — liste, fiche, création, modification | {{IA_QUI_CODE}} | Toi, dans l'application en ligne |
| **Les tests** — un par critère de la fiche | {{IA_QUI_CODE}} | Les tests automatiques |
| **Mise en ligne** du module | {{IA_QUI_CODE}} | Toi |
| **Documentation du parcours** mise à jour | {{IA_QUI_CODE}} | {{NOM_COPILOTE}} |

**L'état d'erreur est celui qu'on ne dessine jamais**, et c'est celui qui casse en démonstration.
{{NOM_COPILOTE}} doit te le faire valider explicitement à chaque module.

### Les points d'attention, module par module

*Une ligne par module : la règle métier qu'on oublie, et le droit qui s'y applique. C'est la section
qui évite de redécouvrir en recette ce que le destinataire savait depuis toujours.*

### 🚪 Portes de sortie

**Une par module.** À chaque fois le même geste : tu ouvres l'application en ligne **sur
{{APPAREIL_CIBLE}}**, tu fais le parcours réel du module de bout en bout, et tu confirmes à
{{NOM_COPILOTE}} « module X validé ». Ce n'est pas une relecture de code — c'est un essai avec tes
mains.

Pour {{MODULE_PIVOT}}, le parcours de validation est plus complet : décris-le ici, étape par étape,
jusqu'à l'effet de bord attendu sur les autres modules.

### Pièges connus

- **{{APPAREIL_CIBLE}}, pas l'ordinateur du développeur.** Une validation faite ailleurs que là où le
  travail se fait vraiment ne prouve rien.
- {{MODULE_PIVOT}} est le module où l'envie d'ajouter « juste une petite chose » est la plus forte.
  C'est la liste « plus tard », toujours.
- Chaque module fini part en ligne. On n'en accumule pas trois pour les livrer ensemble.
- Une revue de sécurité est due à chaque module qui touche à de l'argent ou à une saisie — donc
  presque tous.

---

## Étape 9 — Migration des données réelles

*Une seule règle gouverne cette étape, et elle prime sur toutes les autres : **on ne perd aucune
donnée réelle, et on ne recrée rien de zéro**. La seconde partie compte autant que la première : une
donnée retapée à la main est une donnée dont plus personne ne sait si elle est fidèle.*

**Objectif** : faire passer les vraies données vers la nouvelle application, sans en perdre une seule,
et **sans maquiller** les anomalies qu'elles contiennent.

### Ce qu'on déplace

{{VOLUME_DONNEES}}.

### Les anomalies connues — et la règle qui les gouverne

*Liste ici les anomalies déjà repérées dans les données actuelles. La règle : une anomalie se **migre
telle quelle** puis se corrige dans la nouvelle application, à la main, avec une trace. Une anomalie
« nettoyée » au passage est une différence de total que personne ne saura expliquer six mois plus
tard.*

### Livrables

| Livrable | Ce que c'est |
|---|---|
| **Le transfert** | Le mécanisme qui déplace les données, rejouable |
| **Le rapport de contrôle** | Combien d'enregistrements entrés, combien sortis, et les écarts |
| **La comparaison des totaux** | Les mêmes chiffres des deux côtés |
| **La liste des anomalies traitées** | Ce qui a été corrigé après migration, et par qui |

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Définit les contrôles, exige le rapport, refuse un écart non expliqué |
| **{{IA_QUI_CODE}}** | Écrit et exécute le transfert, produit le rapport |
| **Toi** | Tu compares les totaux et tu vérifies au hasard des enregistrements que tu connais par cœur |

### 🚪 Porte de sortie

Deux gestes, tous les deux les tiens :

1. Tu compares les **totaux** entre l'ancienne et la nouvelle application, et ils sont identiques.
2. Tu ouvres **cinq enregistrements au hasard** — dont ceux que tu sais tordus — et tu retrouves
   exactement ce que tu connais.

### Pièges connus

- **Une donnée retapée à la main n'est pas une donnée migrée.** Si un cas résiste, on comprend
  pourquoi ; on ne le ressaisit pas.
- Un transfert qui ne se rejoue pas est un transfert qu'on aura peur de relancer. Il doit pouvoir
  tourner deux fois sans créer de doublons.
- Les compteurs et les numérotations doivent repartir **après** le dernier numéro migré, jamais à zéro.

---

## Étape 10 — Recette par toi, puis bascule

*La seule étape où le destinataire est le juge unique. Elle se fait **en double** — l'ancien et le
nouveau côte à côte, sur du travail réel — et l'ancien reste allumé après la bascule. Une bascule sans
filet est une bascule qu'on ne se permet pas de faire, donc une refonte qui ne se termine jamais.*

**Objectif** : que tu utilises la nouvelle application sur ton travail réel, en parallèle de
l'ancienne, jusqu'à ce que plus rien ne te manque — puis qu'on bascule.

### Le déroulé

1. **En double**, sur une période convenue : tout ce que tu fais dans l'ancienne, tu le refais dans la
   nouvelle. C'est fastidieux, et c'est le prix de la confiance.
2. Tu notes **tout** ce qui cloche, même minuscule, dans une liste unique.
3. {{NOM_COPILOTE}} trie : bloquant / à corriger avant bascule / liste « plus tard ».
4. On corrige les bloquants, et **eux seuls**.
5. Formation des autres utilisateurs, **sur {{APPAREIL_CIBLE}}**, avec leurs propres comptes.
6. **Une sauvegarde restaurée pour de vrai**, au moins une fois, avant la bascule. Une sauvegarde
   jamais restaurée n'est pas une sauvegarde, c'est une intention.
7. Bascule. L'ancienne application **reste accessible {{DUREE_SECOURS}}**, en lecture, avec une date
   d'extinction notée.

### Qui fait quoi

| Rôle | Ce qu'il fait à cette étape |
|---|---|
| **{{NOM_COPILOTE}}** | Tient la liste, trie les retours, refuse d'élargir le périmètre en recette |
| **{{IA_QUI_CODE}}** | Corrige les bloquants, et rien d'autre |
| **{{ACCOMPAGNANT}}** | Rien, sauf si la bascule touche à un plan payant |
| **Toi** | Tu utilises, tu notes, tu formes, tu décides le jour de la bascule |

### 🚪 Porte de sortie — c'est la fin du chantier

Quatre choses, ensemble :

1. La période en double est terminée et **aucun bloquant ne reste**.
2. Les autres utilisateurs sont formés sur {{APPAREIL_CIBLE}}, avec leurs comptes.
3. **Une sauvegarde a été restaurée pour de vrai**, et la date est notée.
4. La bascule est faite ; l'ancienne application reste accessible {{DUREE_SECOURS}}, date d'extinction
   notée.

### Pièges connus

- **La recette est le moment où l'envie d'ajouter revient en force.** Tout ce qui n'est pas un
  bloquant va dans la liste « plus tard », sans discussion.
- Éteindre l'ancienne le jour de la bascule est la décision qu'on regrette. On garde le filet.
- Un utilisateur formé « en montrant l'écran » n'est pas formé. Il l'est quand il a fait le parcours
  lui-même, sur son propre appareil.

---

## Étape 11 — La première fonctionnalité neuve : {{PREMIERE_FONCTIONNALITE_APRES}}

*Elle est **nommée d'avance**, dès le premier jour, et c'est tout l'intérêt : nommer coupe court à
« et si on ajoutait juste ça ? » pendant le chantier. Volontairement peu détaillée ici — elle se cadre
le moment venu, avec l'état réel des choses. Ce qui compte, c'est la barrière : cette étape ne s'ouvre
pas avant que l'étape 10 soit close.*

🔴 **Cette étape ne s'ouvre pas avant que l'étape 10 soit close.** C'est la règle qui protège tout le
projet. Si une envie pressante arrive entre-temps, elle va dans la liste « plus tard » — c'est
précisément à quoi cette liste sert.

### À cadrer avec {{NOM_COPILOTE}} au moment d'ouvrir l'étape

*Pose ici les questions qui devront être tranchées, pas les réponses. Une question bien posée
aujourd'hui vaut mieux qu'une réponse inventée qui sera fausse au moment de faire.*

- **Le déclencheur** : qui ou quoi lance la fonctionnalité, et à quel rythme.
- **Le contenu exact** de ce qui est produit.
- **La preuve** : comment sais-tu que ça a bien eu lieu ? Un mécanisme silencieux qui s'arrête est le
  pire des cas.
- **Le contrôle** : à quelle fréquence on vérifie que le résultat est exploitable.

### 🚪 Porte de sortie

Tu constates **toi-même**, sans intermédiaire, le résultat attendu — et tu sais dire quand il a été
produit.

### Et après ?

La liste « plus tard » constituée depuis l'étape 2 devient le nouveau backlog. On la reprend avec
{{NOM_COPILOTE}}, on l'ordonne par valeur, et on ouvre le lot suivant — **un seul**, comme toujours.

Et on repasse par le même chemin qu'à l'étape 3 : c'est **{{NOM_COPILOTE}} qui recueille le besoin**.
Une ligne de la liste « plus tard » n'est pas une story : c'est une intention, elle doit être reprise
et rédigée avant d'entrer au backlog, dans `{{DOSSIER_SPEC}}` qui fait foi.

---

## Checklist de progression

*Une ligne par porte de sortie, jamais une de plus — la checklist n'est pas un résumé du document,
c'est son tableau de bord. Groupée en blocs qui reprennent les colonnes du schéma, pour qu'on situe sa
progression d'un coup d'œil. Chaque ligne se formule au **je**, au passé, comme un fait constaté.*

### Préparation

- [ ] **1.** {{NOM_COPILOTE}} répond en respectant le format d'étape ; le dépôt {{DEPOT}} est visible
      dans mon compte
- [ ] **2.** Note de cadrage validée : périmètre iso-fonctionnel, coût d'hébergement vu
      ({{COUT_HEBERGEUR}}, sur le compte de {{ACCOMPAGNANT}} — rien de neuf à ma charge), liste
      « plus tard » ouverte
- [ ] **3.** Backlog visible dans le dépôt, relu et validé par moi
- [ ] **3 bis.** Je sais où vivent la spécification (`{{DOSSIER_SPEC}}`), l'avancement
      ({{TABLEAU_SUIVI}}) et les décisions ({{WIKI}}) — et lequel des trois fait foi
- [ ] **3 ter.** Le dépôt est bien **privé**, et je sais que rien ne passe en public sans
      {{ACCOMPAGNANT}}
- [ ] **4.** Demande envoyée à {{ACCOMPAGNANT}}, invitation acceptée, **l'application apparaît dans
      mon tableau de bord {{HEBERGEUR}}**
- [ ] **4 bis.** Le nom exact de l'application est noté ailleurs que dans un e-mail
- [ ] **4 ter.** {{IA_QUI_CODE}} confirme pouvoir lancer l'application chez lui

### Le socle

- [ ] **5.** Page d'accueil vide en ligne, vérifiée depuis {{APPAREIL_CIBLE}}, sans temps de réveil
- [ ] **5 bis.** Le `README.md` porte l'adresse en ligne dans ses premières lignes
- [ ] **6.** Document de structure relu et compris par moi ; les pièges cochés un par un
- [ ] **7.** Connexion opérationnelle ; {{ROLE_RESTREINT}} est **refusé** sur un écran
      {{ROLE_ADMIN}} (pas seulement privé du lien) ; un compte désactivé perd l'accès
- [ ] **7 bis.** {{DONNEE_SENSIBLE}} n'apparaît nulle part pour {{ROLE_RESTREINT}}
- [ ] **7 ter.** Revue de sécurité passée sur la connexion et les droits

### La valeur

*Une ligne par module de {{LISTE_MODULES}}, dans l'ordre. Le module {{MODULE_PIVOT}} porte le parcours
de validation détaillé.*

- [ ] **8a.** Module 1 validé sur {{APPAREIL_CIBLE}}
- [ ] **8b.** Module 2 validé sur {{APPAREIL_CIBLE}}
- [ ] **8c.** Module **{{MODULE_PIVOT}}** validé — parcours complet, effets de bord vérifiés
- [ ] **8d.** Module 4 validé sur {{APPAREIL_CIBLE}}
- [ ] **8e.** Module 5 validé sur {{APPAREIL_CIBLE}}
- [ ] **8f.** Module 6 validé sur {{APPAREIL_CIBLE}}

### Migration et bascule

- [ ] **9.** Totaux identiques entre l'ancienne et la nouvelle application
- [ ] **9 bis.** Cinq enregistrements vérifiés au hasard, dont les cas tordus connus
- [ ] **10.** Recette en double terminée, aucun bloquant restant
- [ ] **10 bis.** Autres utilisateurs formés sur {{APPAREIL_CIBLE}}, avec leurs comptes
- [ ] **10 ter.** Une sauvegarde restaurée pour de vrai, au moins une fois, date notée
- [ ] **10 quater.** Bascule faite — l'ancienne application reste accessible {{DUREE_SECOURS}}, date
      d'extinction notée
- [ ] 🎉 **Le chantier est terminé**

### Après

- [ ] **11.** {{PREMIERE_FONCTIONNALITE_APRES}} opérationnelle, résultat constaté par moi

---

*{{VERSION}} — {{DATE}}*
