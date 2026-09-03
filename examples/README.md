# Cas réels

🔴 **Des pointeurs, jamais des copies.** Un cas recopié ici diverge de son dépôt d'origine dans la
semaine, et on ne sait plus lequel fait foi. Chaque entrée dit où aller lire, et ce que ce cas a
appris au gabarit.

---

## Le cas fondateur — un dirigeant non technique reprend une refonte (25/08/2026)

**Où lire** : le paquet de passation vit dans le dépôt du projet, sous `docs/refonte/`.
*(Dépôt privé. Ce cas figure ici pour sa méthode, pas pour son code — et le destinataire
n'est pas nommé : ce gabarit décrit des situations, pas des personnes.)*

**La situation** : une application de facturation et de stock, en production, construite par
l'accompagnant. L'accompagnant n'est plus disponible. Le dirigeant de l'entreprise reprend le
pilotage d'une refonte complète vers une autre stack, avec ses propres outils. Il ne code pas et
ne le souhaite pas — c'est précisément la situation que ce gabarit adresse, pas une lacune.

**Le dispositif retenu** : un projet Codex déjà connecté au dépôt écrit le code ; un Custom GPT créé
pour l'occasion tient la méthode et les portes de sortie. Le Custom GPT n'a **pas** d'accès Git — le
destinataire fait le pont à la main. Ce choix est délibéré : donner à un Custom GPT l'illusion d'un
accès au dépôt produit des réponses inventées sur son état.

**Ce que ce cas a appris au gabarit** :

- Le paquet de passation vit **dans le dépôt du projet**, pas dans un espace de notes séparé. Le
  destinataire l'a déjà cloné ; `git pull` puis `git diff` lui suffisent à voir ce qui arrive.
- La question « pourquoi refondre plutôt que faire évoluer ? » n'était écrite nulle part. Une
  décision de refonte non motivée par écrit se rediscute à chaque difficulté — et un chantier qui se
  rediscute est un chantier qui s'arrête. Le gabarit exige désormais cette justification, et marque
  `⚠️ À TRANCHER` quand elle manque plutôt que de l'inventer.
- La sécurité portée par l'infrastructure de la v1 (RLS Postgres) disparaît en changeant de stack.
  Tout changement de socle doit lister **ce que le socle assurait gratuitement** et qui doit être
  réimplémenté — c'est le risque de régression n° 1 d'une refonte.
- Le contexte géographique du destinataire n'est pas de la couleur locale : réseau instable et
  terminaux modestes se traduisent en contraintes de code vérifiables.
- Nommer **à l'avance** la première fonctionnalité d'après-refonte évite la discussion « et si on
  ajoutait juste ça ? » pendant la refonte.
- Le premier réflexe, quand les comptes d'hébergement appartiennent à l'accompagnant, est d'inventer
  un rituel de demande permanent. C'était une erreur : elle remet l'accompagnant sur le chemin
  critique alors qu'il n'est justement plus disponible. La correction — **donner les accès une fois,
  et ne garder que la facturation et le passage en public** — est devenue une règle du gabarit.
- Le recueil des besoins n'avait pas été attribué. Sans attribution explicite, il retombe par
  défaut sur le destinataire — ce n'est pas son métier, et l'accompagnement se dégrade alors en
  prise de commande.
