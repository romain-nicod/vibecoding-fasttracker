# Gabarit — Mise en route (livrable n° 1)

> **Ce gabarit devient le `README.md` du paquet de passation**, à la racine de `{{DOSSIER_PAQUET}}`.
> C'est le premier et parfois le seul fichier que le destinataire lira. Il doit pouvoir aller du néant
> à « mon IA a repris le relais » **seul, sans aide, un vendredi soir**.
>
> 🔴 **Zéro commande de terminal.** Chaque geste nomme la page où aller, le libellé exact du bouton, et
> **ce qu'il doit voir à la fin** pour savoir que c'est réussi.

## Placeholders de ce gabarit

🔴 **Cette section se retire du livrable produit.** Elle n'existe que pour celui qui remplit.

| Placeholder | À quoi il correspond | Exemple |
|---|---|---|
| `{{DESTINATAIRE}}` | le prénom de celui qui reçoit la passation et qui pilotera | `Camille` |
| `{{ACCOMPAGNANT}}` | le prénom de celui qui passe la main | `Alex` |
| `{{PROJET}}` | le nom du projet ou de l'application | `Facturation Atelier` |
| `{{ORGANISATION}}` | l'entreprise ou la structure du destinataire | `l'atelier` |
| `{{DEPOT}}` | le chemin court du dépôt, tel qu'il s'affiche | `mon-orga/facturation-atelier` |
| `{{URL_DEPOT}}` | l'URL complète du dépôt | `https://github.com/mon-orga/facturation-atelier` |
| `{{PLATEFORME_DEPOT}}` | l'hébergeur du dépôt | `GitHub` |
| `{{IA_QUI_CODE}}` | l'outil qui écrit et exécute le code | `Codex` |
| `{{IA_QUI_PILOTE}}` | la forme de l'IA qui cadre — assistant configuré, espace de projet, prompt | `un assistant configuré` |
| `{{NOM_COPILOTE}}` | le nom donné à cet assistant, tel qu'il apparaîtra dans la barre latérale | `Copilote Atelier` |
| `{{ABONNEMENT_IA}}` | le plan payant qui donne accès aux deux IA | `ChatGPT Pro` |
| `{{URL_CONFIG_IA_PILOTE}}` | la page où l'on configure l'IA qui pilote | `https://chatgpt.com/gpts/editor` |
| `{{OUTIL_SCHEMA}}` | l'outil de dessin pour les wireframes et schémas | `Excalidraw` |
| `{{HEBERGEUR}}` | où l'application est mise en ligne — sur le compte de l'accompagnant | `Fly.io` |
| `{{DOSSIER_PAQUET}}` | le dossier du dépôt qui porte ce paquet | `docs/refonte/` |
| `{{DOSSIER_DOC_METIER}}` | le ou les dossiers du dépôt qui portent déjà la doc métier | `docs/product/` et `docs/specs/` |
| `{{DEPOT_METHODE}}` | le dépôt gabarit de méthode auquel on renvoie | `mon-orga/kickoff` |
| `{{URL_DEPOT_METHODE}}` | son URL complète | `https://github.com/mon-orga/kickoff` |
| `{{VERSION}}` | la version du document | `v01` |
| `{{DATE}}` | la date de dernière modification | `25/08/2026` |

---
---

# {{PROJET}} — par où commencer

Ce dossier est la **passation** de {{ACCOMPAGNANT}} à {{DESTINATAIRE}} : à partir de maintenant,
{{DESTINATAIRE}} pilote la suite du projet avec ses propres outils d'IA, sans que {{ACCOMPAGNANT}} soit
disponible au quotidien.

**Avant de faire quoi que ce soit sur le code**, suis les étapes ci-dessous, dans l'ordre. Elles
n'installent aucun outil de code — elles mettent en place l'assistant qui te guidera ensuite pas à pas
pour tout le reste.

Rien de ce qui suit ne se fait dans un terminal. Tout se passe dans une page web ou une application,
avec un bouton à cliquer.

## Ce qu'il y a dans ce dossier

| Fichier | À quoi il sert |
|---|---|
| `README.md` | ce fichier — la mise en route |
| `00-methode-et-roles.md` | la méthode de travail et le texte exact à coller pour créer {{NOM_COPILOTE}} |
| `01-phasing-et-checklist.md` | les grandes étapes du projet, une fois {{NOM_COPILOTE}} actif |
| `02-contexte.md` | ce qui est déjà tranché et ce qui reste ouvert |
| `03-stack-et-decisions-techniques.md` | les consignes techniques que {{IA_QUI_CODE}} lit avant d'écrire du code |
| `handover.html` | **la vue d'ensemble en images** — double-clique dessus pour l'ouvrir dans ton navigateur |

💡 **Si tu ne lis qu'une seule chose avant de commencer**, ouvre `handover.html` : objectifs,
dispositif, dépendances, phasing et coût des outils sur une seule page.

{{DOSSIER_DOC_METIER}} (à côté de ce dossier) contient toute la documentation métier de l'application
actuelle — {{NOM_COPILOTE}} ira la lire, tu n'as rien à en faire toi-même pour l'instant.

## Ce que tu n'as **pas** à faire

Trois inquiétudes classiques, levées tout de suite :

- **Tu n'as pas à rédiger tes besoins.** Ce n'est pas à toi d'écrire ce que l'application doit faire.
  {{NOM_COPILOTE}} te posera des questions simples, une à la fois, sur ton métier — pas sur des écrans
  ni sur de la technique. Il reformulera ce qu'il a compris, te le fera confirmer, et c'est **lui** qui
  mettra ça en forme. Ton seul travail : relire et dire « oui, c'est bien ça » ou « non, en fait… ».
- **Tu n'as aucun compte payant à ouvrir, et aucune carte bancaire à donner.** L'hébergement
  ({{HEBERGEUR}}), le dépôt et la facturation vivent sur les comptes de {{ACCOMPAGNANT}}. Il t'ajoute
  une fois comme collaborateur, et tu travailles ensuite tout seul dessus.
- **Tu n'as pas à demander la permission à chaque fois.** Une fois les accès donnés, tu déploies et tu
  avances sans repasser par {{ACCOMPAGNANT}}. Il ne reste sur le chemin que pour trois choses : donner
  ces accès la première fois, tout ce qui touche à un paiement, et rendre un dépôt public.

---

## Étape 1 — Vérifier tes accès

1. Ouvre [{{DEPOT}}]({{URL_DEPOT}}).
2. Si la page t'affiche le code (fichiers, dossiers) : c'est bon, passe à l'étape 2.
3. Si la page affiche « 404 — page introuvable » ou te demande de te connecter : tu n'as pas encore
   l'accès. Préviens {{ACCOMPAGNANT}} — c'est à lui de t'inviter en tant que collaborateur, tu recevras
   un e-mail d'invitation à accepter.

Fais la même vérification sur [{{DEPOT_METHODE}}]({{URL_DEPOT_METHODE}}) (le gabarit de méthode utilisé
pour structurer le projet) — même geste si l'accès manque.

Vérifie enfin que tu es bien **collaborateur sur {{HEBERGEUR}}**, là où l'application sera mise en
ligne : connecte-toi et regarde si le projet apparaît dans ta liste. Le compte reste celui de
{{ACCOMPAGNANT}} — tu n'en ouvres pas, tu es simplement invité dessus.

**Ce que tu dois voir à la fin** : les deux pages du dépôt s'ouvrent et affichent une liste de fichiers,
et le projet apparaît dans ton {{HEBERGEUR}}.

💡 Ces trois invitations, c'est **la seule chose** que {{ACCOMPAGNANT}} doit faire pour toi au démarrage.
Une fois qu'elles sont là, tu n'as plus à le solliciter pour travailler. Et quand une demande devra
vraiment lui être adressée, {{NOM_COPILOTE}} t'en écrira le texte prêt à envoyer — tu n'auras jamais à
improviser une demande, ni à attendre sans rien faire : il te dira aussi quoi avancer pendant ce temps.

## Étape 2 — Vérifier que {{IA_QUI_CODE}} pointe sur ce dépôt

{{IA_QUI_CODE}} est l'outil qui écrira le code. Il est déjà relié au dépôt {{DEPOT}}.

1. Ouvre-le, et demande-lui de **se resynchroniser avec le dépôt** (le bouton ou la commande qui
   récupère la dernière version depuis {{PLATEFORME_DEPOT}}).
2. Demande-lui ensuite de te lister le contenu du dossier `{{DOSSIER_PAQUET}}`.

**Ce que tu dois voir à la fin** : il te cite les fichiers listés dans le tableau ci-dessus. S'il ne
voit pas ce dossier, il n'est pas à jour : redemande-lui explicitement de se resynchroniser avant de
continuer.

## Étape 3 — Mettre en place {{NOM_COPILOTE}}, l'IA qui pilote

C'est le cœur de la passation : un assistant configuré avec la méthode de {{ACCOMPAGNANT}}, qui va
maintenant te guider à sa place. Il ne code pas — il cadre, conçoit, relit ce que {{IA_QUI_CODE}}
produit, et refuse d'avancer tant qu'une étape n'est pas finie.

<!-- SECTION CONDITIONNELLE : procédure de création d'un « assistant configuré une fois pour toutes »
     de type Custom GPT. Elle se remplace intégralement si {{IA_QUI_PILOTE}} est d'un autre type :
       - un espace de projet (Claude Project, ChatGPT Project) → créer le projet, coller le texte
         « Instructions » dans les instructions du projet, déposer les fichiers dans son espace de
         connaissance ;
       - un simple prompt à recoller → aucune installation ; le destinataire ouvre une conversation
         neuve et colle le texte « Instructions » en premier message, à refaire à chaque nouvelle
         conversation — le dire explicitement, c'est le piège de cette variante.
     Dans tous les cas, garder les points « Ce que tu dois voir à la fin » et « Piège connu ». -->

> *Les points 1 à 6 ci-dessous valent si {{IA_QUI_PILOTE}} est un **assistant configuré une fois pour
> toutes**. Si c'est un espace de projet ou un simple prompt à recoller, cette procédure se remplace —
> le reste de l'étape ne change pas.*

1. Va sur [{{URL_CONFIG_IA_PILOTE}}]({{URL_CONFIG_IA_PILOTE}}) (connecté avec ton compte
   {{ABONNEMENT_IA}}).
2. Choisis la configuration **par formulaire** plutôt que la création guidée à l'oral : on va remplir
   les champs directement, c'est plus fiable.
3. Ouvre le fichier `00-methode-et-roles.md` de ce dossier. Il contient, prêts à copier-coller, les
   champs **Nom**, **Description**, **Instructions** et **Phrases de démarrage**. Colle chacun dans le
   champ correspondant, **sans rien modifier**.
4. Dans les **capacités** de l'assistant, active la **recherche web**. Laisse l'**exécution de code** et
   les **intégrations / actions** désactivées : {{NOM_COPILOTE}} ne code pas, c'est le rôle de
   {{IA_QUI_CODE}}.
5. Dans l'espace **fichiers de connaissance**, ajoute :
   - tous les fichiers de {{DOSSIER_DOC_METIER}}
   - les quatre fichiers `{{DOSSIER_PAQUET}}00-methode-et-roles.md`, `01-phasing-et-checklist.md`,
     `02-contexte.md` et `03-stack-et-decisions-techniques.md`

   Le plus simple pour les récupérer : dans {{PLATEFORME_DEPOT}}, ouvre chaque fichier puis le bouton
   qui télécharge le fichier brut ; ou demande à {{IA_QUI_CODE}} de te les préparer dans un dossier que
   tu glisses-déposes ici.
6. Enregistre, puis choisis le partage **privé / moi seulement** — cet assistant contient de la
   documentation interne à {{ORGANISATION}}, il ne doit pas être public.

**Ce que tu dois voir à la fin** : un assistant nommé « {{NOM_COPILOTE}} » apparaît dans ta barre
latérale. Ouvre-le et envoie un premier message, par exemple :

```
On démarre {{PROJET}}, cadre-moi la première étape
```

S'il te répond en rappelant le cadre de l'étape, les livrables, ce qui est attendu de lui et de toi
(voir le format d'étape décrit dans `00-methode-et-roles.md`) — la passation a réussi, tu peux
continuer avec lui pour la suite.

⚠️ **Piège connu** : un assistant configuré **ne se resynchronise jamais tout seul** avec le dépôt. Si
un des fichiers de connaissance change plus tard, il faut retélécharger la nouvelle version et la
réuploader à la main.

## Étape 4 — Ouvrir {{OUTIL_SCHEMA}} (pour les schémas)

Tu t'en serviras pour les maquettes d'écran et les schémas que {{NOM_COPILOTE}} te demandera de valider.

1. Va sur {{OUTIL_SCHEMA}} — aucune installation n'est nécessaire, ça marche directement dans le
   navigateur.
2. Pour retrouver tes schémas d'une session à l'autre, crée un compte gratuit plutôt que de rester en
   mode invité.

**Ce que tu dois voir à la fin** : une page blanche avec une barre d'outils de dessin — c'est prêt,
{{NOM_COPILOTE}} t'expliquera comment l'utiliser au moment venu.

## Étape 5 — Continuer avec {{NOM_COPILOTE}}

Une fois les étapes 1 à 4 faites, retourne dans la conversation avec {{NOM_COPILOTE}} et demande-lui de
cadrer la suite. `01-phasing-et-checklist.md` liste les grandes étapes qu'il te fera traverser une par
une — tu n'as pas besoin de le lire en entier maintenant, il te guidera dessus.

Il commencera par te faire **parler de ton métier** : comment ça se passe aujourd'hui, qui fait quoi, ce
qui coince. Réponds simplement, comme tu l'expliquerais à quelqu'un qui débarque. C'est de là qu'il
tirera la liste de ce qu'il faut construire — et il te la fera relire avant de la retenir.

Une seule étape ouverte à la fois. C'est la règle qui empêche le chantier de partir dans tous les sens.

---

*{{VERSION}} — {{DATE}}*
