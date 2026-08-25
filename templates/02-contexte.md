# Gabarit — Contexte (livrable n° 4)

> **Ce gabarit devient `02-contexte.md` dans `{{DOSSIER_PAQUET}}`.**
> Son lecteur est **l'IA, avant toute décision de conception**. Il consolide ce qui est **déjà tranché**
> pour qu'on cesse de le redemander à {{DESTINATAIRE}}.
>
> 🔴 **Il ne recopie pas les sources du dépôt**, il les consolide — et il dit **en tête qui fait foi** en
> cas de contradiction. Une information qui vit déjà dans {{DOSSIER_DOC_METIER}} se cite, ne se duplique
> pas : deux textes qui disent la même chose finissent toujours par se contredire.
>
> 🔴 **Aucune justification inventée.** Une raison qui manque devient un `⚠️ À TRANCHER` nominatif — qui
> doit trancher, et quoi — jamais une hypothèse plausible glissée au présent de l'indicatif.
>
> 🔴 **Aucun secret en clair** : ni mot de passe, ni jeton, ni clé. On écrit **où** l'identifiant se
> trouve, jamais sa valeur. Ce fichier est versionné et il partira dans l'espace de connaissance d'une
> IA.
>
> *Les lignes en italique sous chaque titre sont les consignes de remplissage. Elles se retirent du
> livrable produit, comme le tableau ci-dessous.*

## Placeholders de ce gabarit

🔴 **Cette section se retire du livrable produit.**

| Placeholder | À quoi il correspond | Exemple |
|---|---|---|
| `{{PROJET}}` | le nom du projet ou de l'application | `Facturation Atelier` |
| `{{OBJET_PROJET}}` | ce que fait l'application, en une ligne | `émettre les devis et les factures et suivre le stock` |
| `{{DESTINATAIRE}}` | le prénom de celui qui reçoit la passation et qui pilotera | `Camille` |
| `{{ACCOMPAGNANT}}` | le prénom de celui qui passe la main | `Alex` |
| `{{METIER_DESTINATAIRE}}` | son activité réelle, en une ligne — ce sur quoi il est expert | `patronne d'un atelier de menuiserie de huit personnes` |
| `{{NIVEAU_DESTINATAIRE}}` | son niveau réel, outil par outil — jamais « débutant » en bloc | `débutante complète sur l'IA et sur Mac ; à l'aise sur un tableur` |
| `{{ORGANISATION}}` | l'entreprise ou la structure du destinataire | `l'atelier` |
| `{{DEPOT}}` | le chemin court du dépôt | `mon-orga/facturation-atelier` |
| `{{DOSSIER_PAQUET}}` | le dossier du dépôt qui porte ce paquet | `docs/refonte/` |
| `{{DOSSIER_DOC_METIER}}` | le ou les dossiers du dépôt qui portent déjà la doc métier — **les sources qui font foi** | `docs/product/` et `docs/specs/` |
| `{{URL_APP_ACTUELLE}}` | l'adresse où tourne l'application existante | `https://facturation-atelier.exemple.net` |
| `{{STACK_ACTUELLE}}` | la base technique de l'existant | `l'application actuelle en ligne` |
| `{{STACK}}` | la base technique visée | `Django` |
| `{{HEBERGEUR}}` | où la nouvelle application sera mise en ligne | `Fly.io` |
| `{{IA_QUI_CODE}}` | l'outil qui écrit et exécute le code | `Codex` |
| `{{NOM_COPILOTE}}` | le nom donné à l'IA qui pilote | `Copilote Atelier` |
| `{{VERSION}}` | la version du document | `v01` |
| `{{DATE}}` | la date de dernière modification | `25/08/2026` |

---
---

# {{PROJET}} — contexte métier et projet

Ce document est la **mémoire de référence** de {{PROJET}} — de quoi {{OBJET_PROJET}}. Il se lit **avant
toute décision de conception ou de code**, aussi bien pour faire évoluer l'existant que pour le
reconstruire.

**Ce qui est tranché ici ne se redemande pas à {{DESTINATAIRE}}.** Chaque point de ce document a déjà
coûté une discussion, un test ou un bug. Le rouvrir sans raison nouvelle, c'est le repayer.

🔴 **Qui fait foi.** Les sources du dépôt — {{DOSSIER_DOC_METIER}} — restent la référence de détail. Ce
document en est la **lecture consolidée** : en cas de contradiction entre les deux, **la source du dépôt
gagne**, et c'est ce document qui se corrige. Ce qui ne figure ni ici ni là-bas n'est pas décidé : ça se
demande, ça ne s'invente pas.

*Consigne — ce chapeau se garde tel quel, en n'adaptant que les noms. Les trois choses qu'il doit dire
sont : c'est la mémoire · ce qui est tranché ne se redemande pas · qui gagne en cas de contradiction.
Un contexte sans règle d'arbitrage produit deux vérités dès la première divergence.*

---

## 1. Qui est {{DESTINATAIRE}}, l'activité, le contexte de travail

*Consigne — {{METIER_DESTINATAIRE}}, {{NIVEAU_DESTINATAIRE}}, les profils d'utilisateurs de
{{ORGANISATION}} et ce que chacun fait dans la journée. 🔴 **Le contexte géographique et matériel n'est
pas de la couleur locale** : chaque élément se traduit en **contrainte vérifiable dans le code**. Une
contrainte qui n'est pas écrite ici sera oubliée à l'implémentation, et redécouverte par l'utilisateur.*

### Les profils qui utilisent l'application

*Consigne — un profil par ligne. Sur quel terminal il travaille, où, et ce qu'il fait. C'est ce qui
justifiera plus tard les choix d'écran, pas une préférence esthétique.*

| Profil | Sur quoi il travaille, et où | Ce qu'il fait | Ce qu'il ne voit ni ne fait jamais |
|---|---|---|---|
| | | | |

### Du constat à la contrainte

*Consigne — la colonne de droite est la seule qui compte pour l'IA : elle doit être **vérifiable**,
c'est-à-dire qu'on puisse dire oui ou non en regardant l'écran ou le code. « Réseau parfois instable »
n'est pas une contrainte ; « toute saisie longue conserve un brouillon local et se renvoie au retour du
réseau » en est une.*

| Constat | Contrainte vérifiable qui en découle |
|---|---|
| Réseau | |
| Terminaux et taille d'écran | |
| Langue et format de date | |
| Devise et arrondis | |
| Fuseau horaire de référence pour tout calcul de période | |
| Support technique disponible sur place | |
| Cadre légal ou fiscal applicable | |

⚠️ Le **fuseau de référence** se fixe ici, une fois, explicitement — y compris s'il ne correspond pas à
l'heure locale des utilisateurs. Sans cette ligne, chaque calcul mensuel sera recalé au hasard, et les
chiffres cesseront de se recouper d'un écran à l'autre.

## 2. L'état actuel — ce qui existe et tourne

*Consigne — ce que couvre l'application d'aujourd'hui, ce qu'elle ne couvre pas, et comment y accéder.
Une limite écrite ne se redécouvre pas ; une limite tue se redécouvre en production, au pire moment.*

### Ce que ça fait

*Consigne — la liste des domaines fonctionnels couverts, un par ligne, en langue du métier. Pas de nom
de fichier ni de composant technique : cette liste sert à savoir ce qui existe déjà, pas comment c'est
fait.*

-

### Limites connues, et pourquoi elles sont là

*Consigne — chaque limite avec **sa raison** et **ce qu'elle empêche concrètement**. Une limite dont la
raison n'est pas écrite se fait « corriger » par la première IA venue, et le problème d'origine revient.*

| Limite | Pourquoi elle existe | Ce qu'elle empêche |
|---|---|---|

### Ce qui est explicitement hors périmètre

*Consigne — ce qui a été écarté volontairement, et qui le reste tant que {{DESTINATAIRE}} ne décide pas
l'inverse. Sans cette liste, chaque fonctionnalité écartée se repropose à chaque conversation.*

-

### Accès

*Consigne — où ça tourne, où vit le code, et **où** se trouvent les identifiants. 🔴 Jamais la valeur
d'un mot de passe, d'une clé ou d'un jeton dans ce fichier.*

- **Application en ligne** : {{URL_APP_ACTUELLE}}
- **Dépôt de code** : `{{DEPOT}}` — privé
- **Identifiants de test** : *(dire où ils sont rangés, jamais ce qu'ils valent)*

## 3. Structure des données, et les pièges déjà payés

*Consigne — les entités du métier, leurs champs structurants, leurs relations, et les décisions de
structure déjà prises. Puis, séparément, les pièges. C'est **la section qui évite qu'une IA redécouvre à
la dure un bug déjà corrigé une fois** — et c'est la première qu'on oublie d'écrire.*

### Les décisions de structure déjà prises

*Consigne — numérotées, une par ligne, formulées comme une décision et non comme une observation. Chacune
répond d'avance à une question qu'on reposerait sinon à chaque conception d'écran.*

1.

### Les entités

*Consigne — une entrée par entité : les champs qui portent une règle, ceux qui sont calculés, et ceux
qui sont réservés pour plus tard. Ne pas recopier le schéma complet s'il vit déjà dans
{{DOSSIER_DOC_METIER}} : y renvoyer et ne garder ici que ce qui porte une décision.*

**`<entité>`** — champs structurants, champs calculés, contraintes.

### Ce qui est réservé pour plus tard, et **ne doit pas être anticipé**

*Consigne — les extensions prévues mais non construites. Les nommer évite qu'on les improvise
différemment ; dire qu'elles ne sont pas à créer évite qu'on les construise trop tôt.*

-

### 🔴 Pièges à ne JAMAIS réintroduire

*Consigne — un par bug déjà rencontré et corrigé. **Trois colonnes obligatoires** : ce qui s'est passé ·
la règle qui l'empêche · comment on vérifie que la règle tient. Un piège sans règle vérifiable est une
anecdote, et une anecdote ne protège rien. C'est la partie du document que {{IA_QUI_CODE}} doit lire
avant d'écrire la moindre ligne de structure.*

| # | Ce qui s'est passé | La règle qui l'empêche | Comment on vérifie |
|---|---|---|---|
| 1 | | | |

⚠️ Ces pièges sont **indépendants du socle technique**. Changer de langage ou de base ne les fait pas
disparaître : il les fait réapparaître sous une autre forme si personne ne les a réécrits en règles.

## 4. Règles métier et droits par rôle

*Consigne — les règles invariantes du métier, puis la matrice des droits. La matrice est **la source de
vérité des permissions** : ce qui n'y figure pas n'est pas autorisé.*

### Règles invariantes

*Consigne — une règle par ligne, au présent, sans conditionnel. Une règle formulée « il faudrait que »
n'est pas une règle, c'est un souhait, et elle sera arbitrée par l'IA à ta place.*

-

### Matrice des droits par rôle

*Consigne — un module par section, une action par ligne, une colonne par rôle. Mettre en gras les cases
qui sont contre-intuitives : ce sont celles qu'une IA « corrigera » spontanément si rien ne signale
qu'elles sont voulues.*

| Module | Action | *(rôle A)* | *(rôle B)* |
|---|---|:--:|:--:|
| | | | |

**Principe général** : *(résumer en deux phrases ce que le tableau dit, pour qu'une contradiction saute
aux yeux — le résumé et le tableau se relisent l'un l'autre).*

### Cas limites déjà tranchés

*Consigne — les questions déjà posées et déjà répondues : doublons, suppressions, sessions, dates
dépassées, saisies vides, accès concurrent. 🔴 **Ne pas les redemander à {{DESTINATAIRE}}** — c'est
exactement ce que ce document sert à éviter.*

-

## 5. Les indicateurs qui comptent

*Consigne — un dictionnaire, pas une liste de vœux. Chaque indicateur a une **formule sans ambiguïté**,
un **périmètre** et une **visibilité**. Figer aussi ceux qui ne sont pas encore construits : c'est ce
qui évite qu'ils soient redéfinis au moment de les livrer, quand plus personne ne se souvient de
l'intention.*

| Indicateur | Formule et périmètre | Visible par | Déjà livré ? |
|---|---|---|:--:|

**Notes qui font foi** : *(les règles de non-double-comptage, ce qu'une annulation retire, ce qui est
masqué à quel rôle. Deux lignes ici valent mieux qu'un débat plus tard.)*

## 6. Le socle retenu, et pourquoi

*Consigne — ce qui est retenu, et **la raison**. 🔴 Si la raison de refaire ce qui marche n'est pas
documentée, **ne l'invente pas** : pose le `⚠️ À TRANCHER` ci-dessous et nomme qui doit répondre. Une
décision de refonte non motivée par écrit se rediscute à chaque difficulté — et un chantier qui se
rediscute est un chantier qui s'arrête.*

| | Aujourd'hui | Visé |
|---|---|---|
| Base technique | {{STACK_ACTUELLE}} | {{STACK}} |
| Mise en ligne | | {{HEBERGEUR}} |

**Pourquoi {{STACK}} plutôt que faire évoluer {{STACK_ACTUELLE}}** :

⚠️ **À TRANCHER — la raison de la refonte.** *(Cette rubrique est **obligatoire** tant que la raison
n'est pas écrite noir sur blanc. Nommer qui doit trancher — en général {{ACCOMPAGNANT}} — et ce qu'on
attend de lui. Tant qu'elle est ouverte : ne présumer d'aucun défaut technique de l'existant, et ne
proposer à {{DESTINATAIRE}} aucune justification a posteriori. Une fois la réponse obtenue, remplacer
cette rubrique par la raison, datée.)*

*Consigne — si la raison est déjà connue, supprimer le bloc `⚠️ À TRANCHER` ci-dessus et écrire la
raison à sa place. Ne jamais garder les deux : un document qui porte à la fois une justification et un
avertissement disant qu'elle manque n'est plus lisible.*

## 7. 🔴 Ce qui ne doit PAS changer, et ce qui est ouvert

*Consigne — **deux listes séparées et explicites**. C'est la section la plus utile du document et celle
qu'on oublie : sans elle, une IA traite tout comme négociable et refait des choix déjà payés. Si une
chose n'apparaît dans aucune des deux listes, elle n'est pas tranchée : elle se demande.*

### Ne doit pas changer

*Consigne — les invariants du produit, indépendants du socle technique. Pour chacun, dire **où** il est
défini en détail, plutôt que de le recopier ici.*

- **La structure des données** de la section 3 : entités, relations, champs calculés, règles
  d'identifiants.
- **Les règles métier** de la section 4, et la **matrice des droits** telle quelle.
- **Les pièges** de la section 3 : ce sont des bugs déjà vécus et corrigés une fois. Ils se
  réimplémentent, ils ne se rediscutent pas.
- **Les définitions d'indicateurs** de la section 5, y compris celles pas encore construites.
- **Le périmètre écarté** de la section 2 : ce qui est hors périmètre le reste, sauf décision
  explicite de {{DESTINATAIRE}}.
- **Les contraintes** de la section 1 : langue, devise, terminaux, fuseau de référence.
- **Les données existantes** : elles se migrent, elles ne se recréent pas et elles ne se perdent pas.
  *(Nommer ici les volumes réels et les anomalies déjà repérées dans ces données : une reprise qui
  découvre les anomalies en cours de route s'arrête au milieu.)*

### Ouvert

*Consigne — ce sur quoi l'IA a le droit de proposer sans rien redemander. Une liste vide est un signal
d'alarme : tout n'est jamais figé, et un document qui n'ouvre rien produit un chantier bloqué.*

- **Le socle technique** lui-même et toute la mécanique d'implémentation : découpage du code,
  bibliothèques, conventions, tests.
- **Le choix d'hébergement définitif**, à trancher avec sa grille tarifaire propre.
- **L'habillage visuel**, tant que les contraintes de la section 1 sont tenues.
- **L'ordre de livraison** et les fonctionnalités de moindre priorité : {{DESTINATAIRE}} peut les
  reséquencer ou les retirer librement.

## 8. Ce que l'ancien socle assurait gratuitement

*Consigne — 🔴 **la section qui n'apparaît dans aucun cahier des charges, et le risque de régression
n° 1 d'une refonte.** Changer de socle fait disparaître des garanties que personne n'avait demandées
parce que l'ancien outil les rendait sans qu'on y pense. Chacune se réimplémente **nommément**, avec un
responsable et une manière de vérifier qu'elle est bien là.*

| Ce qui était assuré sans qu'on le demande | Qui le rendait | Ce qu'il faut refaire dans {{STACK}} | Comment on vérifie que c'est là |
|---|---|---|---|
| Cloisonnement des données entre rôles | | | |
| Blocage des colonnes sensibles au niveau du stockage | | | |
| Contraintes de cohérence portées par la base | | | |
| Sauvegardes et restauration testée | | | |
| Chiffrement des échanges et gestion des sessions | | | |
| Journalisation des accès et des erreurs | | | |
| Migrations de structure réversibles | | | |

⚠️ **Une ligne de ce tableau qui reste vide est un trou de sécurité ou de données**, pas un détail de
finition. {{NOM_COPILOTE}} le vérifie **avant** la mise en ligne, jamais après : après, on ne découvre
plus le trou, on découvre ses conséquences.

*Consigne — ajouter les lignes propres au projet et supprimer celles qui ne s'appliquent pas. Une ligne
retirée doit l'être parce qu'elle est sans objet, jamais parce que personne ne sait quoi y mettre : dans
ce cas, elle devient un `⚠️ À TRANCHER`.*

---

*{{VERSION}} — {{DATE}}*
