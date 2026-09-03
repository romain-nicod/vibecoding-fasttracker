# Gabarit — Stack et décisions techniques (livrable n° 5)

> **Ce gabarit devient `03-stack-et-decisions-techniques.md` dans `{{DOSSIER_PAQUET}}`.**
> Son lecteur est **l'IA qui code**, et elle le lit **avant d'écrire la moindre ligne**. Le
> destinataire ne l'ouvrira sans doute jamais : le document a donc le droit d'être dense, et le devoir
> d'être précis.
>
> 🔴 **Prescriptif, jamais descriptif.** On n'écrit pas ici ce que le système fait : on écrit ce que
> l'IA a le droit de faire, ce qu'elle n'a pas le droit de faire, et comment elle le vérifie elle-même.
> Une phrase qui ne se traduit pas en « je peux constater que c'est respecté » n'a rien à faire dans ce
> document.
>
> 🔴 **Chaque piège connu de l'ancien système se traduit ici en règle vérifiable.** Un piège qui reste
> raconté au lieu d'être traduit en règle sera réintroduit — c'est mécanique, pas hypothétique.
>
> 🔴 **Ne réécris pas la méthode de projet** — « prêt à démarrer » / « fini », spécification qui génère
> le backlog, jalons, board vivent dans `{{DEPOT_METHODE}}`. On y **renvoie**, on ne les recopie pas.

## Placeholders de ce gabarit

🔴 **Cette section se retire du livrable produit.**

| Placeholder | À quoi il correspond | Exemple |
|---|---|---|
| `{{PROJET}}` | le nom du projet ou de l'application | `Facturation Atelier` |
| `{{DESTINATAIRE}}` | le prénom de celui qui reçoit la passation et qui pilotera | `Camille` |
| `{{ACCOMPAGNANT}}` | le prénom de celui qui passe la main | `Alex` |
| `{{NOM_COPILOTE}}` | le nom donné à l'IA qui pilote | `Copilote Atelier` |
| `{{IA_QUI_CODE}}` | l'outil qui écrit et exécute le code | `Codex` |
| `{{DEPOT}}` | le chemin court du dépôt | `mon-orga/facturation-atelier` |
| `{{PLATEFORME_DEPOT}}` | l'hébergeur du dépôt | `GitHub` |
| `{{DOSSIER_PAQUET}}` | le dossier du dépôt qui porte ce paquet de passation | `docs/refonte/` |
| `{{DOSSIER_DOC_METIER}}` | le ou les dossiers du dépôt qui portent déjà la doc métier | `docs/product/` et `docs/specs/` |
| `{{DOSSIER_SPEC}}` | le dossier où atterrissent spécification et stories — **celui qui fait foi** | `docs/specs/` |
| `{{DOC_SCHEMA_ACTUEL}}` | le document qui décrit la structure de données actuelle | `docs/specs/modele-donnees.md` |
| `{{TABLEAU_SUIVI}}` | l'outil qui porte l'avancement, une carte par story | `le tableau Projects du dépôt` |
| `{{WIKI}}` | l'espace où un humain vient lire décisions et procédures, hors du code | `le wiki du dépôt` |
| `{{DEPOT_METHODE}}` | le dépôt gabarit de méthode auquel on renvoie | `mon-orga/kickoff` |
| `{{REFERENTIEL_CODE}}` | le référentiel d'idiomes obligatoires du langage retenu | `la skill maison d'idiomes du framework` |
| `{{STACK}}` | la stack cible, en une expression courte | `Laravel + MySQL` |
| `{{STACK_ACTUELLE}}` | ce qui fait tourner l'application aujourd'hui | `un générateur no-code et sa base hébergée` |
| `{{HEBERGEUR}}` | où l'application est mise en ligne — sur le compte de l'accompagnant | `Fly.io` |
| `{{COUT_HEBERGEUR}}` | ce que l'hébergement coûte par mois, une fois en ligne | `~8 $/mois` |
| `{{DEVISE_LOCALE}}` | la devise dans laquelle le destinataire raisonne au quotidien | `euros` |
| `{{LANGUE_APP}}` | la langue de l'interface, sans exception | `français` |
| `{{FUSEAU}}` | le fuseau de référence pour découper les périodes | `Europe/Paris` |
| `{{LIEU_UTILISATEURS}}` | où et dans quelles conditions matérielles les utilisateurs travaillent | `sur le terrain, en déplacement, avec un réseau mobile instable` |
| `{{APPAREIL_CIBLE}}` | l'appareil sur lequel l'application est réellement utilisée | `un téléphone d'entrée de gamme` |
| `{{OUTIL_CONNEXION}}` | la brique qui gère identifiants, sessions et mot de passe oublié | `la brique d'authentification standard du framework` |
| `{{OUTIL_AUTORISATIONS}}` | la brique qui décide qui a le droit de faire quoi | `une couche de règles d'autorisation par ressource` |
| `{{ROLE_ADMIN}}` | le rôle qui voit et peut tout | `administrateur` |
| `{{ROLE_RESTREINT}}` | le rôle limité, celui sur qui porte le contrôle de non-régression | `intervenant` |
| `{{DONNEE_SENSIBLE}}` | ce que `{{ROLE_RESTREINT}}` ne doit voir **nulle part** | `les données de rémunération` |
| `{{ENTITE_PIVOT}}` | l'entité centrale du modèle, celle qui porte le cœur des règles | `intervention` |
| `{{VOLUME_DONNEES}}` | ce qu'il y a à migrer, en volume réel | `environ 200 dossiers, 40 intervenants et trois ans d'historique` |
| `{{VERSION}}` | la version du document | `v01` |
| `{{DATE}}` | la date de dernière modification | `25/08/2026` |

---
---

# {{PROJET}} — stack et décisions techniques

## À quoi sert ce document

*Le chapeau répond à trois questions et pas une de plus : à quoi sert ce document, qui le lit, et **ce
qui fait foi ailleurs**. La troisième est celle qu'on oublie, et c'est la plus utile : sans elle, l'IA
qui code redécide du métier au fil de l'eau parce qu'elle ne sait pas où le lire.*

C'est le **brief technique de référence de {{PROJET}}**. Il est écrit pour être lu par
{{IA_QUI_CODE}} **avant d'écrire la moindre ligne de code**, et relu chaque fois qu'une question
d'architecture se pose. Il ne décrit pas le métier : il **traduit en décisions techniques** des
invariants déjà validés ailleurs.

**Ce qui fait foi ailleurs — ne pas le redécider ici :**

| Sujet | Document qui fait foi |
|---|---|
| Métier, structure de données, règles de gestion, droits par rôle, définitions des chiffres | `{{DOSSIER_PAQUET}}02-contexte.md` |
| Méthode de travail et rôles — qui valide quoi | `{{DOSSIER_PAQUET}}00-methode-et-roles.md` |
| Étapes, portes de sortie, checklist de progression | `{{DOSSIER_PAQUET}}01-phasing-et-checklist.md` |
| Documentation produit et règles métier déjà écrites | `{{DOSSIER_DOC_METIER}}` |
| Structure de données réelle du système actuel | `{{DOC_SCHEMA_ACTUEL}}` |
| Idiomes de code obligatoires | `{{REFERENTIEL_CODE}}` — repris en §3 ci-dessous |
| Definition of Ready / Done, spécification → backlog, jalons | `{{DEPOT_METHODE}}` |

🔴 **Règle de lecture en cas de contradiction** : le document de contexte gagne sur le **métier**, ce
document gagne sur la **technique**. Si la contradiction porte sur les deux à la fois, c'est une
question pour {{DESTINATAIRE}}, pas une décision de {{IA_QUI_CODE}}.

🔴 **Périmètre : iso-fonctionnel.** La cible fait ce que fait l'existant, ni plus ni moins. Toute idée
de fonctionnalité nouvelle qui surgit en cours de route se note au backlog ; elle ne se code pas
(§11).

---

## 1. Stack cible

*Un tableau, quatre colonnes : couche · choix · version visée · **pourquoi**. La quatrième colonne
n'est pas décorative : elle doit permettre à l'IA de **défendre le choix**, pas seulement de
l'appliquer. Une IA qui sait pourquoi une brique a été retenue ne propose pas d'en changer à la
première difficulté — et sait dire quand la raison ne tient plus.*

*Une version se **fige** : même valeur en local et en ligne, écrite dans un fichier du dépôt. Une
version « la dernière » est une version qui changera sans prévenir, un mardi matin.*

| Couche | Choix | Version visée | Pourquoi |
|---|---|---|---|
| Langage | | | *la raison en une phrase* |
| Framework | | | |
| Base de données | | | *si c'est le même moteur qu'aujourd'hui, dis-le : ce qui se transpose tel quel ne se réécrit pas* |
| Squelette de départ | | | |
| Assets / CSS | | | |
| JavaScript | | | *dis ce que ce choix remplace, et ce qu'il allège* |
| Authentification | {{OUTIL_CONNEXION}} | | |
| Autorisations | {{OUTIL_AUTORISATIONS}} | | *le point le plus sensible — voir §6* |
| Formulaires | | | |
| Traductions / formats | | | *interface 100 % en {{LANGUE_APP}}* |
| Documents imprimables | | | *privilégier ce qui n'exige aucun binaire système : chaque dépendance système est un risque de mise en ligne* |
| Variables d'environnement | | | |
| Tests | | | |
| Analyse statique / sécurité | | | |
| Hébergement | {{HEBERGEUR}} | | *sur le compte de {{ACCOMPAGNANT}} — voir §9* |

⚠️ **Vérifie la compatibilité du squelette de départ avant le premier enregistrement dans le dépôt.**
Un modèle de projet qui n'a pas suivi la dernière version du framework produit une application qui ne
démarre pas. Si ça casse : **ne bricole pas** — fige une version plus ancienne, relance la génération,
et écris la version retenue dans le `README.md`.

---

## 2. 🔴 Ce qui disparaît de l'ancien socle, et par quoi c'est remplacé

*🔴 **La section la plus importante du document.** {{STACK_ACTUELLE}} assurait gratuitement des choses
que personne n'a jamais écrites dans un cahier des charges : sécurité portée par l'infrastructure,
contraintes tenues par la base, sauvegardes, garanties de cohérence. Elles **disparaissent avec elle**,
sans erreur, sans avertissement, sans qu'on s'en aperçoive avant l'incident.*

*C'est le risque de régression n° 1 d'un changement de socle. Le remplissage de ce tableau n'est pas
une formalité : c'est le travail d'analyse le plus rentable de tout le projet. Une ligne « sans objet »
doit dire **pourquoi** c'est sans objet, pas simplement l'affirmer.*

| Ce que {{STACK_ACTUELLE}} assurait | Ce qui le remplace dans {{STACK}} | Où c'est traité |
|---|---|---|
| *l'authentification et la session* | {{OUTIL_CONNEXION}} | §6 |
| *le filtrage des lignes par utilisateur, tenu par la base* | {{OUTIL_AUTORISATIONS}}, **et rien d'autre** | §6 |
| *le masquage d'une colonne sensible, tenu par la base* | *une requête qui ne sélectionne pas la colonne* | §6 |
| *les vues ou procédures qui portaient une règle de sécurité* | | §6 |
| *les fonctions serveur privilégiées* | | §5 |
| *la clé publique utilisée par le navigateur* | *sans objet — plus aucun accès direct à la base depuis le navigateur* | §6 |
| *les contraintes et garde-fous posés dans la base* | *à reposer nommément, un par un* | §4, §5 |
| *les sauvegardes automatiques* | | §9 |
| *les vues de calcul et d'agrégat* | | §5 |
| *le rendu de l'interface* | | §7 |

🔴 **Conséquence à intégrer avant d'écrire le premier écran** : là où l'ancien socle rattrapait un
oubli, il n'y a désormais **rien derrière**. Un contrôle oublié n'est plus une petite faille, c'est un
accès complet. Écris cette phrase dans le livrable, avec le nom de la brique concernée : c'est elle
qui justifie toutes les règles du §6.

---

## 3. Les règles non négociables

*Une liste numérotée d'**interdits vérifiables** : « JAMAIS X », « TOUJOURS Y ». La formulation compte
plus que le contenu — l'IA doit pouvoir **s'auto-contrôler sur cette liste avant chaque livraison**, en
répondant oui ou non à chaque ligne. Une règle qui commence par « privilégier », « autant que
possible » ou « éviter de » ne se vérifie pas : reformule-la ou retire-la.*

*Le fond de la liste vient de `{{REFERENTIEL_CODE}}` — l'idiome du langage retenu, ce qui rend le code
relisable par quelqu'un d'autre. Complète-la avec les règles ci-dessous, qui valent quelle que soit la
stack.*

1. **JAMAIS de secret en dur.** Le code lit une variable d'environnement ; le **nom** de la variable
   est versionné dans un fichier d'exemple, au même enregistrement ; la **valeur** vit dans la
   configuration locale non versionnée et dans celle de {{HEBERGEUR}}. Aucune exception « juste pour ce
   test ».
2. **JAMAIS d'appel réseau vers un domaine tiers depuis une page servie** — polices, icônes, scripts,
   mesure d'audience. Toute dépendance front est téléchargée et servie par l'application (§7).
3. **JAMAIS de refactorisation de ce qui marche** sans demande explicite : pas de renommage au
   passage, pas d'extraction de méthode pour factoriser deux bouts qui se ressemblent. Deux fois le
   même code est acceptable ; à la troisième, on le **signale**, on ne le fait pas.
4. **JAMAIS de construction hors du programme du référentiel** — métaprogrammation, indirections
   maison, one-liners denses. Quand une construction moins courante est le bon outil, l'utiliser **et
   ajouter un commentaire d'une ligne disant ce qu'elle produit**.
5. **JAMAIS créer quoi que ce soit de sa propre initiative sur {{PLATEFORME_DEPOT}}** en dehors des
   branches et des propositions de modification : ni tableau, ni page de {{WIKI}}, ni changement de
   visibilité du dépôt (§8).
6. **JAMAIS provisionner une ressource payante** chez {{HEBERGEUR}} ou ailleurs de sa propre
   initiative (§9).
7. **TOUJOURS écrire le test depuis le critère d'acceptation**, le regarder échouer, puis écrire le
   minimum qui le fait passer. L'intitulé du test est un livrable : il décrit le comportement refusé
   ou attendu, jamais « ça marche ».
8. **TOUJOURS décomposer en commentaires numérotés avant d'écrire une fonction**, et **laisser les
   commentaires dans le code livré**. Si une étape ne tient pas en une ligne de commentaire, elle
   mérite sa propre fonction.
9. **TOUJOURS coder en silo** : une page complète — route, traitement, écran — vérifiée dans le
   navigateur avant de commencer la suivante. Jamais toutes les routes, puis tous les traitements,
   puis tous les écrans.
10. **TOUJOURS une story = une branche**, nommée d'après elle.
11. **TOUJOURS des garde-fous en base en plus des contrôles applicatifs.** Un garde-fou qui ne vit que
    dans le code saute au premier import de données (§10).
12. **TOUJOURS lire le critère d'acceptation dans `{{DOSSIER_SPEC}}`**, jamais dans une carte de
    {{TABLEAU_SUIVI}} ni dans une page de {{WIKI}} (§8).

*Ajoute ici les règles propres à la stack retenue, dans la même forme. Vise une liste qui se relit en
deux minutes : au-delà d'une vingtaine de lignes, une liste de règles cesse d'être relue.*

---

## 4. Décisions de socle — à poser avant la première ligne

*Ce sont les décisions qui coûtent cher à changer une fois que des données existent. Elles se posent
**avant** la première structure de données, pas quand la question se présente. Pour chacune : le choix,
la raison, et ce qu'on casse en la changeant plus tard.*

| Décision | Ce qu'il faut trancher | Pourquoi maintenant |
|---|---|---|
| **Identifiants** | quel type de clé pour chaque enregistrement, et si l'on **conserve les identifiants du système actuel** | Les conserver rend la migration presque gratuite : les liens entre tables pointent déjà vers les bonnes valeurs, il n'y a rien à remapper. Les changer se paye une fois, à l'import, et pour toujours |
| **Identifiants lisibles** | les références affichées à l'écran et imprimées | 🔴 **Elles ne servent jamais de clé de jointure.** Une référence lisible se cherche et s'imprime ; elle ne relie pas deux tables. Une relation qui pointe vers une référence lisible est un bug |
| **Format de la structure de données versionnée** | le format dans lequel le schéma est enregistré dans le dépôt | Le format par défaut de beaucoup d'outils ne sait pas représenter les contraintes fines, les colonnes calculées ni les types particuliers. S'il en existe dans la base, il faut le format complet — sinon les garde-fous disparaissent silencieusement au premier rechargement |
| **Fuseau et dates** | {{FUSEAU}} comme fuseau de référence, et le format d'affichage en {{LANGUE_APP}} | Un chiffre mensuel calculé dans un fuseau et lu dans un autre donne deux totaux différents pour le même mois. C'est le genre d'écart qu'on met des semaines à expliquer |
| **Montants** | l'unité de stockage — **entiers dans la plus petite unité**, jamais de nombre à virgule flottante | Un montant en flottant produit des totaux faux d'un centime, à l'endroit exact où personne ne l'accepte. L'affichage se fait par une fonction dédiée, jamais dans l'écran |
| **Fractions et pourcentages** | pour chaque taux : **fraction ou pourcentage**, et la contrainte qui le garantit en base | Un taux stocké tantôt en `0,1` tantôt en `10` produit des remises d'un facteur cent. La contrainte en base est la seule protection qui survive à un import |
| **Statuts** | la liste fermée des états de chaque entité, adossée à une **contrainte en base** | Un statut libre finit par contenir des valeurs qu'aucun écran ne sait afficher |
| **Numérotation** | pour chaque compteur : le préfixe, la longueur, et **si elle doit être sans trou** | « Sans trou » et « unique » ne sont pas la même exigence, et n'ont pas la même implémentation. Trancher lesquels des compteurs sont concernés |

*Pour chaque ligne, écris dans le livrable **la décision retenue**, pas seulement la question. Une
décision de socle laissée ouverte se prendra toute seule, par défaut, au premier fichier écrit.*

---

## 5. Mapping ancien → nouveau, entité par entité

*Une section par entité, toujours la même anatomie. C'est le cœur du document et sa partie la plus
longue — elle est aussi celle qui évite de redécouvrir à la main tout ce qui a déjà été payé une fois.*

*🔴 **La règle qui gouverne cette section** : chaque piège connu de l'ancien système se traduit ici en
**règle vérifiable** dans le nouveau. Un piège raconté (« attention, cette colonne est particulière »)
sera réintroduit ; un piège traduit (« aucune écriture sur cette colonne, elle est calculée par la
base, et un test le prouve ») ne le sera pas.*

Anatomie à répéter pour chaque entité :

| Rubrique | Ce qu'on y met |
|---|---|
| **Ancien nom → nouveau nom** | et le renommage éventuel, avec **la raison** — un renommage sans raison écrite se rediscute |
| **Champs** | un par un, avec le type retenu et l'obligation ou non |
| **Relations** | vers quoi, et le comportement à la suppression, **choisi d'après la règle métier** : tout ne se supprime pas en cascade, certaines relations doivent au contraire **refuser** la suppression |
| **Contraintes en base** | les garde-fous que la base refuse de laisser passer |
| **Règles métier** | ce que le code doit garantir en plus |
| **Pièges attachés → règle vérifiable** | le piège en une ligne, la règle qui l'empêche, et **le test qui le prouve** |

### Les pièges de l'existant, traduits

*Numérote-les : la porte de sortie de l'étape « structure de données » consiste à les cocher un par
un, et une liste non numérotée ne se coche pas. Chaque piège tient en trois lignes — le symptôme, la
règle, le test.*

*Familles de pièges qu'on retrouve d'un projet à l'autre, à vérifier même si personne ne les a
signalées :*

- **Une clé de jointure qui pointe vers un identifiant lisible** au lieu de la vraie clé.
- **Une colonne calculée par la base** qu'un import ou un formulaire tenterait d'écrire.
- **Un taux stocké dans une unité et lu dans une autre.**
- **Une numérotation attribuée trop tôt**, qui laisse un trou quand l'opération échoue.
- **Une quantité qui peut passer sous zéro** quand deux opérations se croisent.
- **Un prix figé au moment de la saisie** qui se remettrait à suivre le tarif courant.
- **Une valeur absente traitée comme un zéro** au lieu de rester vide.

### {{ENTITE_PIVOT}} — l'entité centrale

*Traite-la en premier et en détail : c'est elle qui porte le cœur des règles, et c'est sur elle que
l'IA se trompera si le document est vague. Décris son cycle de vie état par état, ce qui devient
immuable et à quel moment, et **ce qui bouge ailleurs** quand elle change d'état — une opération qui
touche plusieurs tables se fait en une seule transaction, ou elle ne se fait pas.*

---

## 6. Autorisations et droits

*Section dédiée, jamais un paragraphe glissé ailleurs. C'est ici que se réimplémente ce que
{{STACK_ACTUELLE}} assurait gratuitement, et c'est la section dont l'absence produit le plus de dégâts
silencieux.*

### 6.1 Pourquoi c'est le risque de régression n° 1

*Écris ce raisonnement en toutes lettres dans le livrable, avec les noms réels des briques. C'est lui
qui justifie que chaque action autorise, sans exception — sans lui, la discipline s'érode dès le
troisième écran.*

Là où {{STACK_ACTUELLE}} portait une partie de la sécurité **hors de l'application**, {{STACK}} n'a
plus qu'**une seule barrière côté serveur** : {{OUTIL_AUTORISATIONS}}. Il n'y a plus rien derrière.

🔴 **Un contrôle d'autorisation oublié n'est pas une petite faille, c'est un accès complet.**

### 6.2 Les règles

1. **Refus par défaut.** Tout ce qui n'est pas explicitement autorisé est refusé. Une règle
   d'autorisation par ressource, jamais un contrôle éparpillé dans les écrans.
2. **Chaque action autorise, sans exception** — y compris les pages d'apparence anodine.
3. **Un filet qui rend l'oubli bruyant.** Le socle doit **échouer** quand une action n'a pas autorisé,
   plutôt que de laisser passer. Un oubli doit produire une erreur, pas une fuite.
4. **La restriction porte sur les données, pas sur l'affichage.** Une donnée interdite ne se masque pas
   à l'écran : elle **n'est pas lue**. Le filtrage se fait à la requête.
5. **Les champs acceptés en écriture dépendent du rôle.** Un rôle restreint qui envoie un champ qu'il
   n'a pas le droit de modifier doit voir ce champ ignoré, pas appliqué.
6. **Un compte désactivé perd l'accès immédiatement**, session en cours comprise.
7. **Aucune énumération.** Les messages d'erreur de connexion et de mot de passe oublié ne disent
   jamais si un compte existe.

### 6.3 Checklist de non-régression par rapport à l'ancien système

*🔴 **Cette checklist est le livrable de la section.** Une ligne par garantie que l'ancien socle
assurait, et son équivalent nommé dans le nouveau. À cocher **avant la première mise en ligne
réelle**, et à repasser à chaque revue de sécurité.*

| # | Ce que l'ancien socle assurait | Équivalent dans {{STACK}} | Vérifié par |
|---|---|---|---|
| 1 | *filtrage des lignes par utilisateur, tenu hors de l'application* | *une autorisation dans chaque action* | *le filet qui rend l'oubli bruyant, plus un test par écran* |
| 2 | *lecture restreinte par rôle* | *une requête filtrée dans chaque liste* | |
| 3 | *masquage d'une colonne sensible* | *une requête qui ne sélectionne pas la colonne* | *un test qui cherche la valeur dans la réponse complète* |
| 4 | *vues ou procédures portant une règle de sécurité* | | |
| 5 | *contrôle du rôle dans les fonctions serveur* | | |
| 6 | *aucune clé privilégiée côté navigateur* | | |
| 7 | *aucune clé d'API dans la page servie* | *une recherche dans les gabarits d'écran* | |
| 8 | *session invalidée pour un compte désactivé* | | |
| 9 | *pas d'énumération d'adresses au mot de passe oublié* | | |
| 10 | *contrainte de cohérence tenue en base* | | *un test de concurrence* |
| 11 | *numérotation sans trou* | | *un test : une opération qui échoue ne consomme pas de numéro* |

🔴 **La ligne 1 est la seule qui compte vraiment ; les autres en sont des conséquences.** Une action
qui n'autorise pas rend toutes les autres inutiles.

### 6.4 Le test qui prouve que ça tient

*Écris-le explicitement, parce qu'il est contre-intuitif : le test ne consiste pas à vérifier qu'un
lien n'apparaît pas.*

Un compte {{ROLE_RESTREINT}} demande directement l'adresse d'un écran réservé à {{ROLE_ADMIN}} : il
doit obtenir un **refus**. Et {{DONNEE_SENSIBLE}} ne doit apparaître **nulle part** pour lui — ni à
l'écran, ni dans un export, ni dans une recherche, ni dans un total qui la laisserait déduire. Le test
cherche la valeur dans la **réponse complète**, pas dans ce qui est affiché.

---

## 7. Contraintes de terrain

*🔴 **Ce n'est pas de la couleur locale.** Le contexte matériel et géographique des utilisateurs se
traduit en **conséquences vérifiables sur le code et l'interface**. Une contrainte de terrain écrite
comme une anecdote (« ils ont parfois du réseau ») ne change rien au code ; écrite comme une règle
(« aucune requête vers un domaine tiers depuis une page servie ») elle se vérifie et elle tient.*

*S'il n'y a réellement aucune contrainte particulière, écris-le — mais vérifie d'abord : l'absence de
contrainte est presque toujours une question qu'on n'a pas posée.*

Les utilisateurs travaillent {{LIEU_UTILISATEURS}}, sur {{APPAREIL_CIBLE}}. Ce n'est pas un contexte
d'usage secondaire : c'est le contexte principal. Les décisions ci-dessous en découlent et ne sont pas
négociables « pour aller plus vite ».

| Contrainte de terrain | Conséquence sur le code | Comment on le vérifie |
|---|---|---|
| **Réseau instable ou lent** | 🔴 aucune requête vers un domaine tiers depuis une page servie : polices, icônes, scripts et mesure d'audience sont téléchargés et servis par l'application | une recherche dans les fichiers servis ne trouve aucune adresse externe |
| **Appareils modestes** | pages légères, rendu côté serveur, pas d'application monopage lourde ; un budget de poids par page, écrit | mesure du poids de la page la plus lourde |
| **Coupures en pleine saisie** | 🔴 un formulaire long **survit à une coupure** : la saisie est conservée localement et restituée au retour. Un enregistrement perdu au bout de dix minutes de saisie fait abandonner l'application, définitivement | essai réel : couper le réseau en cours de saisie, revenir |
| **Usage mobile réel** | conçu d'abord pour l'écran étroit ; zones tactiles suffisantes, pas de survol comme seul moyen d'accès, pas de tableau large sans repli | la validation de chaque module se fait sur {{APPAREIL_CIBLE}}, pas sur un ordinateur |
| **Langue, devise, formats** | interface 100 % en {{LANGUE_APP}} ; montants en {{DEVISE_LOCALE}} au format local ; dates au format local ; périodes découpées sur {{FUSEAU}} | aucune chaîne d'interface hors {{LANGUE_APP}}, y compris les messages d'erreur techniques |

⚠️ **Attention aux valeurs par défaut des outils.** Beaucoup d'outils de dépendances front pointent
par défaut vers un service de distribution externe. C'est le défaut, et c'est exactement ce qu'on ne
veut pas : il faut demander explicitement le téléchargement local, puis **vérifier le fichier de
configuration produit**.

---

## 8. Où atterrit le travail

*Trois emplacements, trois usages, **un seul qui fait foi**. Cette section n'est pas de
l'organisation : elle détermine **où l'IA va lire un critère d'acceptation** avant d'écrire un test.
Sans elle, elle codera sur la foi d'une carte de tableau que personne n'a mise à jour.*

| Emplacement | Ce qu'il porte | Fait foi |
|---|---|---|
| **`{{DOSSIER_SPEC}}` du dépôt** | la spécification et les stories, en fichiers versionnés | 🔴 **oui** |
| **{{TABLEAU_SUIVI}}** | l'avancement : une carte par story, **dérivée** des fichiers | non — se régénère |
| **{{WIKI}}** | ce qu'un humain lit hors du code : décisions et leur raison, procédures | pour son sujet seul |

Conséquences opérationnelles pour {{IA_QUI_CODE}} :

- **La source d'un critère d'acceptation est le fichier de `{{DOSSIER_SPEC}}`**, jamais une carte ni
  une page de {{WIKI}}. Si une carte contredit un fichier, le fichier gagne et la carte se régénère.
- Une story est produite par {{NOM_COPILOTE}} et validée par {{DESTINATAIRE}} ; {{IA_QUI_CODE}}
  l'**exécute**, elle ne l'invente pas. Une story qui ne peut pas se démontrer à l'écran n'est pas une
  story.
- **Jamais de spécification recopiée dans {{WIKI}}.** Une spécification à deux endroits est une
  spécification dont une des deux copies est déjà fausse.
- 🔴 **Le dépôt {{DEPOT}} est privé par défaut.** Aucun passage en public ne se décide sans
  {{ACCOMPAGNANT}}, quelle qu'en soit la raison invoquée : le dépôt contient des règles de gestion et
  des données réelles.

🔴 **Ce que {{IA_QUI_CODE}} a le droit de créer** : des branches et des propositions de modification.
**Rien d'autre** sur {{PLATEFORME_DEPOT}} — ni tableau, ni page de {{WIKI}}, ni changement de
visibilité, tant que ce n'est pas explicitement tranché.

⚠️ **À TRANCHER si ce n'est pas déjà fait** : *qui* exécute concrètement la création des cartes de
{{TABLEAU_SUIVI}} et des pages de {{WIKI}} — {{IA_QUI_CODE}} si elle dispose des accès,
{{DESTINATAIRE}} dans l'interface web, ou {{ACCOMPAGNANT}}. Tant que ce n'est pas décidé, la règle
ci-dessus s'applique sans exception.

---

## 9. Déploiement

*Deux choses à écrire, et une interdiction. Les deux choses : **sur quel compte l'application vit**, et
**quel accès a été donné une fois pour toutes**. L'interdiction : provisionner du payant.*

### 9.1 Le modèle d'accès

L'application vit sur le compte {{HEBERGEUR}} de {{ACCOMPAGNANT}}. **{{DESTINATAIRE}} n'ouvre aucun
compte et ne fournit aucune carte bancaire** — ne le lui demande jamais, même quand un écran semble
l'exiger.

{{ACCOMPAGNANT}} **donne l'accès une fois** — collaborateur sur {{HEBERGEUR}}, collaborateur sur
{{DEPOT}} — et {{DESTINATAIRE}} est **autonome ensuite** : il met en ligne, consulte les journaux,
redémarre l'application.

🔴 **N'invente jamais un rituel de demande permanent.** « Demander à {{ACCOMPAGNANT}} avant chaque mise
en ligne » remet sur le chemin critique quelqu'un qui n'est justement plus disponible au quotidien : le
dispositif s'arrête au premier délai de réponse. Trois choses seulement lui reviennent : l'octroi
initial des accès, ce qui touche à la facturation ou à un plan payant, et le passage du dépôt en
public.

### 9.2 🔴 Aucune ressource payante de sa propre initiative

**{{IA_QUI_CODE}} ne provisionne jamais de ressource payante** — service additionnel, palier
supérieur, environnement supplémentaire, nom de domaine. Elle **propose**, chiffre, et attend. Un
service ajouté « parce que ça simplifierait » est une ligne de facture que personne n'a vue arriver,
sur le compte de quelqu'un d'autre.

Un seul environnement en ligne, sauf décision explicite. Un environnement de test oublié allumé coûte
tous les mois sans rien produire.

### 9.3 Ce qu'il faut mettre en place, dans l'ordre

*Numérote la séquence réelle : création de l'application, configuration, base de données, variables
d'environnement, première mise en ligne, automatisation. Pour chaque étape, **ce qu'on doit voir** à la
fin — pas seulement la commande.*

### 9.4 Variables d'environnement

*Un tableau `Variable | Requise | Usage`, les valeurs réelles jamais versionnées. Le nom de chaque
variable est ajouté au fichier d'exemple **dans le même enregistrement** que le code qui la lit.*

### 9.5 Sauvegardes

*Écris : ce qui est sauvegardé, à quelle fréquence, où ça vit, et **combien de temps c'est conservé**.
Puis la règle : 🔴 **une sauvegarde jamais restaurée n'est pas une sauvegarde.** Une restauration
réelle doit être faite au moins une fois avant la bascule, et la date notée. Ne déclare pas les
sauvegardes « en place » avant cette vérification.*

### 9.6 Le coût — sur le compte de {{ACCOMPAGNANT}}, à annoncer quand même

*🔴 Le fait qu'un tiers paie ne dispense jamais d'annoncer un coût. Ce que {{DESTINATAIRE}} doit
savoir, c'est ce que son application consomme — c'est aussi ce qui permet de voir tout de suite qu'un
chiffre a doublé sans raison.*

| Poste | Coût mensuel | Qui paie |
|---|---|---|
| | | {{ACCOMPAGNANT}} |
| | | |
| **Total** | **{{COUT_HEBERGEUR}}** | **{{ACCOMPAGNANT}} — rien à la charge de {{DESTINATAIRE}}** |

*Convertis le total en {{DEVISE_LOCALE}} et en coût annuel : c'est l'ordre de grandeur qui parle, pas
le prix unitaire. Et dis les réserves plutôt que de les taire — une facturation dans une devise
étrangère fluctue, un petit palier offre moins de garanties qu'un grand. Ces prix sont un **ordre de
grandeur daté, pas un devis** : à revérifier au moment de la création.*

---

## 10. Migration des données

### 10.1 La règle qui prime sur toutes les autres

🔴 **On ne perd aucune donnée réelle, on ne recrée rien de zéro, et on n'invente aucune valeur.**
{{VOLUME_DONNEES}} : c'est l'historique d'une activité qui tourne, pas un jeu d'essai. Une donnée qu'on
ne sait pas importer se **signale** ; elle ne se devine pas et elle ne se supprime pas.

### 10.2 La stratégie

*Décris-la en trois points : d'où sortent les données, où elles atterrissent en attendant, et par quoi
elles sont importées. Deux précisions à ne pas oublier :*

- *Le dossier qui reçoit les fichiers d'export est **exclu du versionnement** : il contient des données
  réelles. Son **nom**, lui, est documenté.*
- *Un import n'est pas un jeu de données de démonstration. On veut un rapport détaillé et la
  possibilité de **relancer sans dupliquer** — ce sont deux besoins différents et ils changent
  l'outil.*

### 10.3 Ce que l'import doit garantir

| Exigence | Ce que ça veut dire |
|---|---|
| **Rejouable sans dupliquer** | chaque enregistrement est retrouvé par son identifiant d'origine. Relancer ne crée rien en double |
| **Identifiants préservés** | c'est tout l'intérêt de la décision de socle du §4 : les liens entre tables pointent déjà vers les bonnes valeurs, il n'y a rien à remapper |
| **Tout ou rien** | l'import entier passe, ou rien ne passe |
| **Ordre respecté** | les entités référencées avant celles qui les référencent |
| **Colonnes calculées ignorées** | ne jamais écrire une valeur que la base calcule, même si elle figure dans le fichier source |
| **Renommages appliqués** | ceux décidés au §5, et eux seuls |
| **Contrôles contournés seulement où il faut** | l'historique contient des états que les règles d'aujourd'hui refusent. Contourner **uniquement** sur les lignes historiques, jamais dans le code applicatif, et journaliser chaque cas |
| **Rapport écrit** | lignes lues, créées, ignorées, **avec le motif** |

### 10.4 Après l'import : les gestes obligatoires

1. **Initialiser les compteurs** sur le maximum déjà utilisé — sinon le prochain numéro écrase un
   numéro existant. *Écris un tableau : entité, préfixe, longueur, valeur après import.*
2. **Recalculer les valeurs dérivées** depuis les données importées, puis lancer le contrôle de
   cohérence. Le rapport doit être vide. Un écart est un bug à comprendre, pas à effacer.
3. **Contrôles de recette**, à comparer avec l'existant avant de déclarer l'import réussi : les totaux,
   les décomptes par entité, et quelques enregistrements ouverts au hasard et comparés à l'écran.

### 10.5 Les anomalies connues — traitement prescrit

*Liste-les une par une, avec leur traitement. La règle : une anomalie se **migre telle quelle** et se
corrige ensuite depuis l'application, à la main, avec une trace. Une anomalie « nettoyée » au passage
est un écart de total que personne ne saura expliquer six mois plus tard.*

| Anomalie | Traitement | À trancher |
|---|---|---|
| *donnée illisible dans un champ numérique* | *importer ce qui est lisible, isoler le reste dans un fichier d'anomalies avec son contenu brut* | *ce que cette valeur représentait — par {{DESTINATAIRE}}* |
| *enregistrement vide mais numéroté* | *importer tel quel, dans l'état qui convient — le numéro reste réservé, la numérotation reste sans trou* | *ce que ces numéros représentaient* |
| *dates manquantes* | 🔴 *ne jamais inventer une date ni la déduire d'une autre colonne. La laisser vide et lister chaque cas dans le rapport* | *fournir les dates réelles, ou accepter l'état* |
| *valeur absente là où c'est normal* | *comportement attendu, pas une anomalie : la valeur reste vide et l'affichage la masque sans erreur* | — |

🔴 **Aucune de ces questions ne bloque le chantier.** L'import se fait, les anomalies sont importées
dans l'état documenté, et la correction se fait plus tard depuis l'application. Ne pas attendre les
réponses pour avancer sur le code.

---

## 11. Ce qu'on ne fait PAS

*La liste des tentations à refuser. Chacune est une bonne idée — dans un autre projet, ou plus tard.
🔴 **Une idée qui apparaît dans cette liste se note au backlog et ne se code pas.** Écris-la : une
tentation non nommée sera cédée, avec les meilleures intentions du monde.*

### 11.1 Aucune fonctionnalité nouvelle

*Reprends la liste du document de contexte, telle quelle. Et ajoute la règle qu'on oublie :*
🔴 **les emplacements « réservés pour plus tard » ne se créent pas.** Une table vide créée par
anticipation est une table qu'on migrera pendant des années sans jamais l'utiliser.

### 11.2 Aucune refactorisation de ce qui marche

- Pas de renommage de table ni de champ — **sauf** ceux décidés au §5, avec leur raison écrite.
- Pas de traduction du vocabulaire métier. Les termes que {{DESTINATAIRE}} emploie restent tels quels
  dans le code : c'est son vocabulaire, et il est repris à l'identique de l'existant.
- Pas d'indirection supplémentaire — couches maison, objets de service, abstractions « au cas où ».
- Pas de « pendant qu'on y est » sur les règles métier. Un cas limite déjà tranché dans le document de
  contexte ne se rediscute pas, même s'il paraît discutable.

### 11.3 Aucun changement de périmètre technique

| Tentation | Pourquoi non |
|---|---|
| *remplacer une brique du §1 par une autre, mieux connue* | *elle vient avec le squelette, et elle est connue de ceux qui reliront* |
| *une interface de programmation « au cas où »* | *personne ne la consomme, et chaque point d'entrée est une surface d'autorisation de plus* |
| *un mode hors ligne complet* | *l'existant est en ligne seulement ; la sauvegarde locale du formulaire (§7) est la réponse retenue* |
| *une file de traitements asynchrones* | *aucun traitement asynchrone dans le périmètre — un service de plus, un coût de plus* |
| *une interface d'administration générique* | *la gestion des comptes est un ensemble d'écrans simples avec ses règles d'autorisation* |
| *un environnement conteneurisé en développement* | *personne dans l'équipe ne le maintiendra* |
| *une chaîne d'intégration élaborée* | *les tests au vert avant la proposition de modification, plus l'analyse de sécurité à la revue* |
| *faire vivre les deux versions en parallèle* | *une seule application fait foi. La bascule est un moment daté, pas une transition* |

### 11.4 Côté méthode

- **Pas de code avant les routes ni avant les tests.**
- **Pas de gros lot.** Une story, une branche, une proposition de modification. Un lot qui ne tient pas
  en une passe se découpe.
- **Pas d'écran sans règle d'autorisation**, y compris les pages d'apparence anodine.
- **Pas de spécification écrite ailleurs que dans `{{DOSSIER_SPEC}}`** (§8).
- **Pas d'initiative sur {{PLATEFORME_DEPOT}}** au-delà des branches et des propositions de
  modification (§8).

---

## 12. Récapitulatif des points à trancher

*🔴 **Marque `⚠️ À TRANCHER` plutôt que d'inventer.** Une justification inventée parce que la vraie
manquait est le défaut le plus coûteux de ce document : elle a l'air d'une décision, elle se cite
comme une décision, et personne ne sait plus qu'elle n'en est pas une.*

*Pour chaque point : qui tranche, et **bloquant ou non**. La seconde colonne compte autant que la
première — un point non bloquant ne doit jamais servir de prétexte à l'attente. Dis explicitement ce
qui peut avancer pendant ce temps.*

| # | Point | Qui tranche | Bloquant ? |
|---|---|---|---|
| 1 | | | *Non — on développe pendant ce temps, on tranche avant la mise en ligne* |
| 2 | | | |
| 3 | | | |

### Tranché depuis — ne pas rouvrir

*Le bloc qu'on oublie toujours, et qui fait gagner le plus de temps. Une décision acquise qui n'est pas
écrite ici sera reposée en question à la première difficulté — et une IA qui rediscute une décision
acquise use un débutant plus vite que n'importe quel bug.*

- **Qui détient les comptes et la carte bancaire.** L'application vit sur le compte {{HEBERGEUR}} de
  {{ACCOMPAGNANT}}, qui ajoute {{DESTINATAIRE}} comme collaborateur ; {{DESTINATAIRE}} n'ouvre aucun
  compte et ne fournit aucune carte (§9.1).
- **Le périmètre est iso-fonctionnel.** La cible fait ce que fait l'existant, ni plus ni moins (§11).
- **Le dépôt est privé par défaut** (§8).
- *Ajoute ici chaque décision acquise au fil du projet, avec la section qui la porte.*

---

*{{VERSION}} — {{DATE}}*
