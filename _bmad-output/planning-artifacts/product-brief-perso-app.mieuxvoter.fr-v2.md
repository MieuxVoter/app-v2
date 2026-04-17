---
title: "Product Brief: MieuxVoter v2"
status: "draft"
created: "2026-04-17"
updated: "2026-04-17"
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
- Compte utilisateur optionnel (pour les informels) ou requis (pour les organisationnels)
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
**Besoin :** Créer et partager un vote en moins de 2 minutes, sans compte, depuis son téléphone.
**Aha moment :** "En 30 secondes j'ai un lien à partager, et le résultat représente vraiment ce que tout le monde préfère."

### Segment 2 — L'usage organisationnel
**Profil :** Responsables d'association (CA, AG), animateurs, enseignants, RH de PME — 30-60 ans, modérément techniques, qui organisent des votes formels ou semi-formels.
**Besoin :** Invitations nominatives, traçabilité, liste d'émargement, export des résultats, anonymat garanti pour les votants.
**Aha moment :** "Je sais exactement qui a voté, je peux relancer les absents, et j'ai un export PDF pour mes archives."

*Note : La question d'une segmentation produit (une app unique vs. deux surfaces distinctes) reste ouverte et fera l'objet d'un arbitrage en phase de brainstorming.*

---

## Critères de succès

**Mission :** Croissance du nombre d'élections créées et de votants uniques d'une année sur l'autre.

**Indicateurs produit :**
- Taux de complétion du flux de création d'élection (objectif : > 80 %)
- Taux de participation moyen par élection (objectif : > 70 % des invités)
- Taux de rétention des organisateurs (retour pour une 2e élection)
- NPS organisateurs et électeurs

**Indicateurs de mission :**
- Nombre d'élections créées par an
- Nombre de votants uniques par an
- Diversité des segments couverts (informel, associatif, éducation, entreprise)

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

**Hors scope pour l'instant :**
- Niveau de sécurité cryptographique type Belenios (vote institutionnel)
- Intégrations tierces (Slack, Teams, SSO, LDAP)
- Autres méthodes de scrutin (architecture scalable prévue, mais non activée)
- Application mobile native

---

## Vision à 3 ans

MieuxVoter est la référence française — et à terme européenne — pour tout groupe qui veut décider collectivement de manière juste et légitime. La plateforme est utilisée par des millions de personnes, des groupes d'amis aux assemblées générales associatives, en passant par les jurys de concours et les consultations internes d'entreprises.

Le jugement majoritaire n'est plus une curiosité académique : c'est la méthode de vote par défaut pour quiconque veut un résultat que tout le monde peut accepter. MieuxVoter a rendu cela possible en le rendant aussi simple qu'un sondage.
