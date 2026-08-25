---
name: vibecoding-fasttracker
description: Produire le paquet de passation qui amène un débutant complet à l'autonomie en vibe coding — le contexte, le cadre de méthode, les rôles et le plan de vol que son IA lira pour prendre le relais du pilotage. À déclencher quand on passe un projet à quelqu'un qui débute et qui le mènera avec sa propre IA (ChatGPT, Claude, autre) : « je passe la main sur ce projet », « handover », « accompagnement au vibe coding », « il va reprendre avec son ChatGPT », « prépare la passation ». Ne pas déclencher pour démarrer un projet neuf entre gens du métier — c'est `project-kickoff`.
---

# Vibecoding Fasttracker

## Ce que tu produis, et pour qui

Un **paquet de passation** : un dossier de documents, dans le dépôt du projet, qui permet à
**l'IA du destinataire** de prendre le relais du pilotage — pas seulement de l'écriture du code.

🔴 **Les deux bouts de la chaîne ne se confondent jamais.**

| | Qui | Lit quoi |
|---|---|---|
| **L'accompagnant** | te lit, toi | cette skill |
| **Le destinataire** | débute complètement | le `README.md` du paquet, et rien d'autre au départ |
| **L'IA du destinataire** | ChatGPT, Claude, autre | tout le reste du paquet |

Tu écris donc pour **trois lecteurs différents** dans le même dossier. Un document qui se trompe de
lecteur est un document raté : le `README.md` du destinataire n'a pas le droit d'être dense, et le
brief technique n'a pas le droit d'être pédagogique.

## 🔴 La règle anti-divergence

**Cette skill ne contient aucun texte de méthode.** Elle dit quel document remplir et ce qui le rend
bon — jamais ce que le document dit. `templates/` du dépôt `vibecoding-fasttracker` est l'unique
source du figé.

Si tu te surprends à écrire ici une formulation qui devrait apparaître dans un livrable, arrête :
elle va dans le gabarit, et le gabarit est cité, pas recopié.

Même chose vers l'extérieur : pour toute la **méthode de projet** — Definition of Ready / Done,
spécification qui génère les issues, jalons, board — tu **renvoies** au dépôt `kickoff`. Tu ne la
réécris pas. Deux textes de méthode divergent toujours.

---

## Étape 0 — Ce que tu dois savoir avant d'écrire une ligne

Ne devine jamais ces réponses. Demande-les, en une seule fois, et marque `⚠️ À TRANCHER` dans le
livrable pour celles qui restent en suspens plutôt que d'inventer.

1. **Qui reçoit** — son métier, son niveau réel sur chaque outil concerné (pas « débutant » en bloc :
   débutant sur quoi exactement), sa machine, ce qu'il veut faire lui-même et ce qu'il veut déléguer.
2. **Quelle IA** il utilisera, et sous quelle forme — un assistant configuré une fois pour toutes,
   un espace de projet, un prompt à recoller. Le mécanisme change la forme du livrable.
3. **Cette IA a-t-elle accès au dépôt ?** Presque toujours non pour l'IA qui pilote, souvent oui pour
   celle qui code. C'est la question la plus structurante du paquet : une IA sans accès Git doit
   **demander** l'état du dépôt, jamais le supposer, et il faut l'écrire dans ses instructions.
4. **Le projet** — ce qui existe déjà, ce qui est refait, ce qui est ajouté. Et si c'est une
   refonte : **pourquoi refondre plutôt que faire évoluer**.
5. **Le périmètre au-delà du premier projet** — souvent il y en a un, souvent il n'est pas dit.
6. **Les outils payants**, qui paie, et **sur le compte de qui** ils vivent. Si c'est l'accompagnant :
   quels accès il délègue, et ce qui lui reste.
7. **Les dépendances** que l'accompagnant seul peut lever : accès, invitations, comptes.
8. **Où atterrissent la spécification, l'avancement et les décisions** — et si le dépôt est privé.

### Les trois questions qu'on oublie toujours de poser

- **« Pourquoi refaire ce qui marche ? »** Une décision de refonte non motivée par écrit se
  rediscute à chaque difficulté — et un chantier qui se rediscute est un chantier qui s'arrête. Si
  personne ne sait répondre, c'est un `⚠️ À TRANCHER` en tête du contexte, pas une justification que
  tu inventes.
- **« Qu'est-ce que l'ancien socle assurait gratuitement ? »** Changer de stack fait disparaître des
  garanties invisibles — sécurité portée par l'infrastructure, sauvegardes, contraintes de base de
  données. Ce qui disparaît doit être listé et réimplémenté nommément. C'est le risque de régression
  n° 1 d'une refonte, et il ne se voit pas dans le cahier des charges.
- **« Où travaillent les utilisateurs ? »** Le contexte géographique et matériel n'est pas de la
  couleur locale : réseau instable, terminaux modestes, langue, devise, fuseau se traduisent en
  contraintes de code vérifiables. S'ils ne sont pas écrits, ils seront oubliés.

---

## Étape 1 — Où va le paquet

**Dans le dépôt du projet**, sous un dossier dédié — pas dans un espace de notes séparé. Le
destinataire a déjà le dépôt cloné dans son outil ; il reçoit les mises à jour par une
synchronisation qu'il sait déjà faire, et il voit ce qui a changé.

Une seule raison de faire autrement : le destinataire n'a pas de dépôt du tout. Dans ce cas, choisis
un support qu'il ouvre sans rien installer et dis-le explicitement dans le paquet.

Vérifie avant d'écrire ce que le dépôt porte **déjà** — spécification, modèle de données, règles
métier. Tu ne les réécris pas, tu y renvoies. Ce que tu produis, c'est ce qui manque : la méthode, les
rôles, le plan de vol, et une lecture consolidée du métier à l'usage de l'IA.

## Étape 2 — Les six livrables

Chacun a son gabarit dans `templates/`. Remplis, adapte, supprime ce qui ne s'applique pas — mais ne
change pas l'ordre ni le découpage : il est fait pour qu'un destinataire perdu retrouve toujours où
il en est.

| # | Livrable | Lecteur | Ce qui le rend bon |
|---|---|---|---|
| 1 | **Mise en route** (`README.md`) | le destinataire, seul | Il peut aller du néant à « mon IA a repris le relais » sans aide et sans terminal. Chaque geste nomme la page, le bouton exact, et **ce qu'il doit voir à la fin** pour savoir que c'est réussi. |
| 2 | **Méthode et rôles** | l'IA pilote | Contient le texte d'instructions **prêt à coller**, sans un mot à adapter. Les rôles y sont exclusifs : qui code, qui pilote, qui décide. |
| 3 | **Phasing et checklist** | l'IA pilote, et le destinataire pour se repérer | Chaque étape a une **porte de sortie** que le destinataire franchit explicitement. Se termine par une checklist à cocher. |
| 4 | **Contexte** | l'IA, avant toute décision | Consolide ce qui est **déjà tranché** pour qu'on cesse de le redemander. Sépare nettement ce qui ne doit pas changer de ce qui est ouvert. |
| 5 | **Stack et décisions techniques** | l'IA qui code | Prescriptif, pas descriptif. Chaque piège connu de l'existant y est traduit en règle vérifiable dans la nouvelle stack. |
| 6 | **Page de présentation** (HTML) | le destinataire, et qui il veut montrer | S'ouvre d'un double-clic, sans connexion. Objectifs, dépendances, phasing, outils et leur coût — d'un coup d'œil. |

### Le recueil des besoins appartient à l'IA pilote

C'est la responsabilité qu'on oublie le plus souvent d'écrire, et son absence est ce qui transforme
un accompagnement en atelier de prise de commande. Le destinataire connaît son métier, pas la manière
d'en faire une spécification — c'est l'IA pilote qui la lui extrait. Le paquet doit lui imposer :

1. **Faire parler du métier, pas de l'écran imaginé.** Qui fait quoi, quand, avec quoi aujourd'hui,
   et ce qui coince réellement.
2. **Des questions simples, une à la fois**, en langue courante. Un questionnaire de dix points d'un
   coup fait décrocher un débutant, et un débutant qui décroche n'ose souvent pas le dire.
3. **Reformuler et faire confirmer avant d'écrire.** Un besoin mal compris coûte dix fois plus cher
   une fois codé.
4. **Rédiger ensuite** au format story — rôle, action, bénéfice — avec des critères d'acceptation
   **vérifiables à l'écran**, un identifiant et une priorité. Ce qui ne peut pas se démontrer n'est
   pas une story.
5. **Faire valider chaque story par le destinataire, dans ses mots à lui**, avant qu'elle entre au
   backlog.

### Où atterrissent les livrables de pilotage

Trois emplacements, trois usages. Le paquet doit les nommer et dire **lequel fait foi** — sans quoi
la spécification finit recopiée à trois endroits qui divergent.

| Emplacement | Ce qu'il porte | Fait foi |
|---|---|---|
| Le dépôt (`docs/`) | la spécification et les stories, en fichiers | 🔴 oui |
| Le tableau de suivi (GitHub Project ou équivalent) | l'avancement : une carte par story, **dérivée** des fichiers | non — se régénère |
| Le wiki | ce qu'un humain vient lire hors du code : décisions et leur raison, procédures | pour son sujet seul |

**Le dépôt est privé par défaut**, et son passage en public est une décision de l'accompagnant, jamais
un effet de bord. Écris-le : un débutant qui découvre les réglages d'un dépôt peut le publier sans
mesurer ce qu'il expose.

⚠️ **Qui exécute concrètement** la création des cartes et des pages de wiki n'est pas évident : l'IA
pilote n'a pas d'accès, l'IA qui code ne peut pas toujours appeler une API, et le destinataire n'est
pas toujours autorisé. Tranche-le explicitement dans le paquet, ou marque-le `⚠️ À TRANCHER`.

### Les comptes restent à l'accompagnant — donne l'accès, ne sers pas de relais

Hébergement, dépôt, facturation vivent presque toujours sur les comptes de l'accompagnant. Le réflexe
naturel est d'en faire un rituel de demande permanent : **c'est un piège**. Un dispositif où chaque
déploiement passe par un aller-retour humain s'arrête au premier délai de réponse, et ne produit
jamais d'autonomie.

La bonne forme : l'accompagnant **donne les accès une fois** — collaborateur sur l'hébergement,
collaborateur sur le dépôt — et le destinataire est autonome ensuite. Ne restent à l'accompagnant que
l'octroi initial, ce qui touche à la facturation, et le passage en public.

Pour ces quelques demandes-là, le paquet impose à l'IA pilote de **rédiger le message prêt à
envoyer**, jamais de laisser le destinataire improviser. Toujours les quatre mêmes points : ce qui
est demandé en une phrase · pourquoi maintenant · ce qui est bloqué en attendant · ce que le
destinataire doit recevoir en retour pour savoir que c'est fait. Et immédiatement après : **ce qu'il
peut avancer pendant l'attente**.

### Ce que le paquet doit contenir, quel que soit le projet

- **Deux rôles d'IA, jamais confondus.** Celle qui code n'arbitre pas la méthode ; celle qui pilote ne
  touche pas au code et ne prétend jamais avoir exécuté quoi que ce soit.
- **Un format d'étape imposé** à l'IA pilote, qu'elle rappelle avant chaque étape : le cadre ·
  les livrables · ce qui est attendu d'elle et du destinataire · les prérequis · ce que le
  destinataire valide · les outils · l'étape suivante. Aucune étape ne s'enchaîne sans validation
  explicite.
- **Le double rôle de l'IA pilote** : garante de la solution *et* mentor. Le second est celui qu'on
  oublie — c'est lui qui produit l'autonomie plutôt que la dépendance.
- **Un seul lot ouvert à la fois**, et la première chose d'après nommée à l'avance. Nommer d'avance
  coupe court à « et si on ajoutait juste ça ? » pendant le chantier.
- **Le coût des outils annoncé avant** que le destinataire s'engage.
- **Les dépendances** que lui seul, ou l'accompagnant seul, peut lever.

---

## Étape 3 — Ce qui rend le paquet mauvais

Relis-toi contre cette liste avant de rendre la main. Ce sont des défauts constatés, pas des
hypothèses.

- **Une commande de terminal dans un livrable destinataire.** S'il ne code pas, il n'ouvre pas de
  terminal. Jamais. Reformule en gestes d'interface, ou fais-la exécuter par l'IA qui code.
- **Du jargon non expliqué à sa première apparition.** Un mot non expliqué est un mot qui bloque, et
  un débutant qui bloque n'ose souvent pas le dire.
- **Un livrable qui recopie ce qui existe déjà ailleurs dans le dépôt.** Deux vérités qui
  divergeront. Pointe, ne recopie pas — et quand une consolidation est vraiment utile, dis en tête
  qui fait foi en cas de contradiction.
- **Un ton condescendant.** Le destinataire est presque toujours expert de son métier et débutant
  seulement sur l'outil. Tutoiement, chaleureux, jamais paternaliste.
- **Une justification inventée** parce que la vraie manquait. Marque `⚠️ À TRANCHER` et nomme qui
  doit trancher.
- **Un phasing sans portes de sortie.** Une liste d'étapes sans critère de passage n'est pas un plan,
  c'est une intention.
- **Une IA à qui on laisse croire qu'elle voit le dépôt.** Elle inventera son état avec aplomb.
- **Un dispositif où l'accompagnant reste sur le chemin critique.** S'il faut le solliciter pour
  déployer, le projet s'arrête au premier délai de réponse. Il donne les accès, il ne sert pas de
  relais.
- **Une spécification recopiée dans le wiki ou saisie d'abord dans le tableau de suivi.** Deux
  vérités qui divergeront. Le fichier fait foi, le reste en dérive.

## Étape 4 — Rendre la main

1. Relis chaque livrable **dans la peau de son lecteur**, en particulier le `README.md` dans celle du
   destinataire : est-ce qu'il peut aller au bout seul, un vendredi soir, sans personne à qui
   demander ?
2. Liste à l'accompagnant tous les `⚠️ À TRANCHER` et les dépendances qu'il doit lever lui-même.
3. Committe dans le dépôt du projet, en français, sujet puis détail.
4. Ajoute le cas dans `examples/` du dépôt `vibecoding-fasttracker` — **en pointeur, jamais en
   copie**, et écris ce que ce cas a appris au gabarit. C'est ce qui fait progresser le Fasttracker
   d'une passation à l'autre.
5. Écris la mémoire du projet dans le vault, et une carte pour le sous-projet d'accompagnement.
