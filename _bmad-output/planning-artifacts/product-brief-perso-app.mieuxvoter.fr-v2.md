---
title: "Product Brief: MieuxVoter v2"
status: "finalized"
created: "2026-04-17"
updated: "2026-04-24"
inputs: ["session de découverte guidée", "recherche concurrentielle (web)", "recherche UX/personas (web)"]
---

# Product Brief : MieuxVoter v2

## Résumé exécutif

Organiser un vote collectif est frustrant. Les outils courants (Doodle, Framadate, sondages WhatsApp) réduisent des décisions nuancées à un clic binaire — perdant l'essentiel de l'intelligence collective. À l'opposé, les outils sérieux (Belenios, OpaVote) sont techniques, payants, et inadaptés au quotidien des associations ou des groupes informels.

MieuxVoter v2 est la plateforme de référence française pour organiser des votes par jugement majoritaire — une méthode d'évaluation graduée (ex. : Très bien / Bien / Passable / Insuffisant / À rejeter) qui exprime mieux les préférences réelles, élimine les votes stratégiques, et produit un résultat que chacun peut accepter comme légitime.

L'objectif de cette version est double : rendre le jugement majoritaire aussi simple à lancer qu'un sondage Doodle pour les usages informels, et fiable et traçable comme un outil professionnel pour les associations et organisations. Une seule plateforme, progressive, souveraine, et gratuite — portée par une association française dont c'est la mission.

---

## Le problème

### Pour les groupes informels (amis, famille, petits groupes)
Choisir un restaurant, une destination, un film : les outils disponibles sont soit trop simples (vote à la majorité simple qui ignore les préférences nuancées), soit absents. Le résultat est souvent un non-consensus frustrant ou un choix imposé par défaut.

### Pour les organisations (associations, entreprises, écoles)
Les administrateurs d'élections font face à des problèmes concrets et récurrents :
- **Perte d'accès** : sans compte utilisateur, un lien d'administration perdu = une élection inaccessible
- **Opacité des invitations** : impossible de savoir si un email est arrivé, a été ouvert, ou si l'électeur a voté
- **Absence de liste d'émargement** : impossible de prouver le quorum ou de contester un résultat
- **Résultats non fiables** : sans traçabilité, les résultats peuvent être contestés

Ces frustrations ne sont pas anecdotiques — elles poussent les organisations à abandonner les outils numériques ou à se tourner vers des solutions payantes étrangères qui ne parlent pas la langue de la gouvernance associative française.

---

## La solution

MieuxVoter v2 est une plateforme unifiée d'organisation d'élections par jugement majoritaire, accessible sans friction pour tous, avec des fonctionnalités avancées pour les organisations qui en ont besoin.

**Pour l'organisateur :**
- Création d'une élection en moins de 2 minutes
- Création possible sans compte ; création de compte proposée au moment où l'utilisateur exprime un besoin qui le requiert (invitations nominatives, suivi des votants, export…)
- Tableau de bord des élections créées et des invitations envoyées
- État en temps réel des invitations : envoyé / ouvert / voté
- Liste d'émargement nominative (configurable selon le besoin)
- Relances automatiques des non-votants

**Pour l'électeur :**
- Vote par lien, QR code ou email — sans compte requis
- Interface pédagogique expliquant le jugement majoritaire en quelques secondes
- Confirmation de prise en compte du vote
- Accès aux résultats selon les paramètres définis par l'organisateur

**Fil rouge de la conception :** chaque étape non indispensable supprimée pour les usages informels, chaque garantie nécessaire activable pour les usages formels.

---

## Ce qui rend MieuxVoter différent

Quelques outils proposent le jugement majoritaire : Belenios (expérimental, cryptographie avancée, UX austère), Cap Collectif (B2B/B2G, payant, ciblant les collectivités), et quelques projets open source peu maintenus (jugementmajoritaire.net, jm.instantz.org, maju.app). Aucun ne couvre à la fois les usages informels et organisationnels avec une UX accessible et une mission de démocratisation.

| Dimension | MieuxVoter v2 | Concurrents avec JM |
|---|---|---|
| **Accessibilité** | Zéro friction, sans compte pour les votants | Belenios : UX technique ; Cap Collectif : B2B uniquement |
| **Double segment** | Informel + organisationnel sur une seule plateforme | Chaque concurrent couvre un seul segment |
| **Souveraineté & gratuité** | Association française, open source, gratuit | Cap Collectif : payant ; Belenios : INRIA, pas de plan produit grand public |
| **Pédagogie embarquée** | Explication de la méthode in-app | Absente chez les concurrents |
| **Mission** | Démocratisation du JM comme finalité | Fonctionnalité parmi d'autres pour les concurrents |

L'avantage structurel de MieuxVoter est sa combinaison unique : **l'outil JM le plus accessible et le plus maintenu pour le grand public francophone**, porté par une légitimité académique (Balinski & Laraki, Sciences Po) et une mission associative crédible.

---

## À qui cela s'adresse

### Segment 1 — L'usage informel
**Profil :** Individus de 20-45 ans, actifs sur smartphone, qui organisent des choix collectifs ponctuels (restaurant, film, destination, cadeau commun).
**Fréquence d'usage :** 3 à 5 votes par an et par utilisateur — usage récurrent mais espacé, pas quotidien.
**Taille du groupe :** 2 à 10 personnes — petits cercles d'amis, collègues, famille proche.
**Douleurs principales (par ordre d'intensité) :**
1. **Temps de création** — tout ce qui dépasse ~60 secondes pousse l'utilisateur à retomber sur WhatsApp ou Doodle.
2. **Friction du partage** — le lien doit circuler aussi naturellement qu'un message texte (copier-coller, QR code, partage natif mobile).

**Besoin :** Créer et partager un vote en moins de 2 minutes, sans compte, depuis son téléphone.
**Aha moment :** "En 30 secondes j'ai un lien à partager, et le résultat représente vraiment ce que tout le monde préfère."
**Implication produit :** le flux de création en mode anonyme doit être obsédé par la vitesse. Chaque champ, chaque micro-étape compte. La vélocité perçue est le seul vrai différenciateur face aux outils généralistes.

### Segment 2 — L'usage organisationnel
**Profil :** Responsables d'association (CA, AG), animateurs, enseignants, RH de PME — 30-60 ans, modérément techniques, qui organisent des votes formels ou semi-formels.
**Fréquence d'usage :** 1 à 6 votes par an et par organisation — usage rare et espacé, avec un fort coût de ré-apprentissage entre deux usages.
**Taille du collège votant :** 10 à 500 votants — très large amplitude, l'UX et l'infra doivent absorber les deux extrêmes.
**Douleurs principales (par ordre d'intensité, validées qualitativement) :**
1. **Perte d'accès à l'élection** — l'organisateur n'a pas noté le lien admin et se retrouve incapable de consulter les résultats ou de relancer. *Douleur validée par des emails reçus de vrais utilisateurs en v1.*
2. **Opacité des invitations** — impossible de savoir si un email est arrivé, a été ouvert, ou si l'électeur a voté.
3. **Absence d'émargement** — impossible de prouver le quorum ou de contester un résultat.

**Besoin :** Invitations nominatives, traçabilité, liste d'émargement, export des résultats, anonymat garanti pour les votants.
**Aha moment :** "Je sais exactement qui a voté, je peux relancer les absents, et j'ai un export PDF pour mes archives."
**Implication produit :** la fréquence annuelle basse (parfois 1 vote/an) impose une ré-authentification sans friction — **magic-link email ou login social (Google / Apple)**, plutôt qu'un mot de passe à mémoriser douze mois après. Sinon la v2 déplace simplement la douleur "lien admin perdu" vers "mot de passe oublié".

### Architecture produit : surface unique, à dévoilement progressif par intention

MieuxVoter v2 est **une seule application**, pas deux surfaces. Le parcours par défaut (non connecté) n'expose que le strict nécessaire : question, options de vote, partage. Les fonctionnalités organisationnelles (invitations nominatives, liste d'émargement, relances, export, statuts de vote) ne sont **pas visibles par défaut** — elles sont **invoquées par l'intention** : lorsque l'utilisateur clique sur un besoin spécifique qui les requiert, l'application propose la création de compte comme contrepartie naturelle, puis débloque les options concernées.

Cette règle de conception garantit trois choses :
- **Aucun coût cognitif** pour l'utilisateur informel — il ne voit jamais des options qu'il n'utilisera pas.
- **Un chemin fluide** de l'usage informel vers l'usage organisationnel, qui coïncide avec notre principal funnel d'acquisition (un utilisateur découvre le JM en choisissant un restaurant, puis l'amène à son AG associative six mois plus tard).
- **Une seule base de code, une seule marque, un seul produit** à faire connaître — compatible avec les moyens d'une équipe associative.

Le compte utilisateur n'est donc jamais promu comme une feature ("créez un compte pour débloquer X") — il est toujours l'aboutissement d'un besoin exprimé par l'utilisateur.

---

## Critères de succès

### Baseline v1 — point de référence

- **4 034 élections** créées en 2025 (+23 % vs 2024, après deux années plates 2023→2024). Run-rate T1 2026 : ~390 élections/mois (+15 % vs moyenne mensuelle 2025).
- **33 905 votants uniques** en 2025 (+28 % vs 2024). Run-rate T1 2026 : ~3 250 votants/mois (+15 %).
- **Taux de complétion du flux de création : non mesuré en v1.** L'instrumentation est un prérequis de la v2, pas un livrable optionnel.

### Ambition de croissance : +30 à +50 % par an

Cette fourchette double le rythme de croissance organique 2024→2025. Elle reflète une ambition associative — croissance durable et ancrée, pas viralité court-termiste. L'essentiel du gain doit venir de la levée de frictions (v2) et de l'ouverture au segment informel, pas d'un effort d'acquisition payant.

### Indicateurs produit — horizon T+6 mois post-lancement v2

| Indicateur | Baseline | Cible T+6 mois |
|---|---|---|
| Taux de complétion du flux de création | non tracké en v1 | instrumentation en place + **> 80 %** |
| Taux de participation moyen (élections à invités identifiés) | à établir dès v2 | **> 70 %** des invités |
| Rétention organisateur (2e élection < 180 j) | à établir dès v2 | **> 40 %** |
| NPS organisateurs | à établir dès v2 | **> 30** |

### Indicateurs de mission — horizon 12 mois post-lancement v2

| Indicateur | Baseline 2025 | Cible année pleine post-v2 |
|---|---|---|
| Élections créées / an | 4 034 | **5 250 – 6 050** |
| Votants uniques / an | 33 905 | **44 000 – 51 000** |
| Diversité des segments (informel + sous-segments organisationnels : associatif, éducation, entreprise) | non ventilé | tracking en place + **informel + au moins 2 sous-segments organisationnels dépassent 20 %** du volume |

### Prérequis transverse

Aucun des indicateurs ci-dessus n'est mesurable sans instrumentation analytique de la v2 dès le jour 1 de mise en ligne. Le tracking n'est pas différable : sans baseline v2, il devient impossible de défendre l'atteinte des cibles — et donc la pertinence de la v2 elle-même.

---

## Contraintes légales & modération

MieuxVoter v2 relève du statut d'**hébergeur** au sens de la LCEN française (2004) et du DSA européen (2024). Ce statut est protecteur pour l'association éditrice — à condition que trois obligations minimales soient couvertes. Aucune n'est en place en v1 : la v2 est donc également un **rattrapage de dette de conformité**.

1. **Traçabilité minimale à la création** — toute élection, y compris créée sans compte, doit être techniquement traçable. Log IP + timestamp systématique ; identifiants complémentaires (email, nom) uniquement s'ils ont été volontairement fournis par l'utilisateur (création de compte, opt-in notifications, invitation nominative — principe RGPD de minimisation). Invisible côté utilisateur, conservé selon les durées légales en vigueur.
2. **Mécanisme de signalement** — un bouton "signaler" accessible sur chaque élection publique, couplé à une procédure documentée de retrait en cas de contenu manifestement illicite ("notice and action").
3. **CGU et acceptation** — CGU claires interdisant les usages illégaux (diffamation, incitation, harcèlement…), acceptées à la création d'élection ou à la création de compte.

**Dépendance bloquante :** aucune revue juridique n'a été faite à date, et aucun avocat référent n'est identifié. Avant passage en développement, l'association doit mandater un avocat spécialisé (droit du numérique, LCEN/DSA) pour valider les durées de conservation, le libellé des CGU, et la procédure de notice-and-action. Cette revue est un **prérequis non négociable de la PRD**.

---

## Périmètre v2

**Dans le scope :**
- Comptes utilisateurs (organisateurs) avec gestion des élections
- Tableau de bord des invitations avec statut en temps réel
- Liste d'émargement configurable
- Relances automatiques
- Interface pédagogique sur le jugement majoritaire
- Vote par lien, QR code et email
- Export des résultats (PDF / CSV)
- Mode hybride présentiel/distanciel (QR code en salle)
- Acceptation des CGU à la création d'élection ou de compte
- Mécanisme de signalement des contenus illicites (notice-and-action)

**Hors scope pour l'instant :**
- Niveau de sécurité cryptographique type Belenios (vote institutionnel)
- Intégrations tierces et SSO entreprise (Slack, Teams, SAML, LDAP)
- Autres méthodes de scrutin (architecture scalable prévue, mais non activée)
- Application mobile native

---

## Vision à 3 ans

MieuxVoter est la référence française — et à terme européenne — pour tout groupe qui veut décider collectivement de manière juste et légitime. La plateforme est utilisée par des millions de personnes, des groupes d'amis aux assemblées générales associatives, en passant par les jurys de concours et les consultations internes d'entreprises.

Le jugement majoritaire n'est plus une curiosité académique : c'est la méthode de vote par défaut pour quiconque veut un résultat que tout le monde peut accepter. MieuxVoter a rendu cela possible en le rendant aussi simple qu'un sondage.
