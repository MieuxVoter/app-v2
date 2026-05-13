---
stepsCompleted: ["step-01-init", "step-02-discovery", "step-02b-vision", "step-02c-executive-summary", "step-03-success", "step-04-journeys", "step-05-domain", "step-06-innovation"]
inputDocuments:
  - "_bmad-output/planning-artifacts/product-brief-perso-app.mieuxvoter.fr-v2.md"
briefCount: 1
researchCount: 0
brainstormingCount: 0
projectDocsCount: 0
workflowType: 'prd'
classification:
  projectType: web_app
  domain: govtech_civic
  complexity: high
  projectContext: greenfield
---

# Product Requirements Document - perso-app.mieuxvoter.fr-v2

**Author:** MieuxVoter
**Date:** 2026-05-01

## Executive Summary

MieuxVoter v2 est la plateforme de référence francophone pour organiser des votes collectifs par jugement majoritaire — une méthode d'évaluation graduée qui exprime mieux les préférences réelles, élimine les votes stratégiques, et produit un résultat que chacun peut accepter comme légitime.

**Promesse produit :** Aussi simple qu'un Doodle, aussi fiable qu'une urne.

La plateforme cible deux segments sur une surface unique à dévoilement progressif : les groupes informels (amis, collègues) qui veulent créer un vote en moins de 2 minutes sans compte, et les organisations (associations, entreprises, écoles) qui ont besoin d'invitations nominatives, de traçabilité et de liste d'émargement. Le parcours par défaut n'expose que le strict nécessaire ; les fonctionnalités organisationnelles sont invoquées par l'intention de l'utilisateur, jamais imposées.

Différenciateur clé côté électeur : à la validation du vote, l'électeur reçoit une preuve de vote et peut vérifier à tout moment que son bulletin est bien comptabilisé dans l'urne. Cette transparence visible renforce la légitimité perçue du résultat pour tous les participants.

La v2 est également une reconstruction technique : la v1 (Python) atteint ses limites de scalabilité au moment où la croissance s'accélère (+23 % d'élections en 2025). La v2 reconstruit la plateforme sur des bases capables d'absorber la croissance à venir, tout en comblant une dette de conformité réglementaire (LCEN, DSA, RGPD) non adressée en v1.

**Note architecturale :** La vérifiabilité cryptographique de type Belenios est hors scope v2, mais l'architecture du moteur de vote doit être conçue pour ne pas fermer cette porte. Une abstraction propre autour du moteur permettra d'activer un niveau de sécurité renforcé pour les élections formelles à forts enjeux dans une version future, sans reconstruction.

### Ce qui rend MieuxVoter différent

Aucun outil existant ne couvre simultanément les usages informels et organisationnels avec une UX accessible et une mission de démocratisation du jugement majoritaire. Belenios est technique et austère ; Cap Collectif est B2B et payant ; les projets open source peu maintenus n'ont pas de plan produit grand public. MieuxVoter est l'unique outil JM maintenu, gratuit, souverain (association française), pédagogique (explication in-app de la méthode), et pensé pour le grand public francophone.

L'avantage structurel : la combinaison accessibilité + légitimité académique (Balinski & Laraki, Sciences Po) + mission associative crédible — dans un marché sans concurrent direct sur ce positionnement.

## Classification du Projet

- **Type :** Application web (SPA/PWA, mobile-first)
- **Domaine :** Civic tech / GovTech — vote, gouvernance participative, démocratie
- **Complexité :** Élevée — contraintes LCEN/DSA, RGPD, confidentialité des votes, traçabilité légale
- **Contexte :** Greenfield (reconstruction complète depuis la v1)

## Critères de Succès

### Succès utilisateur

**Organisateur :**
- Taux de complétion du flux de création > 80 % (mesuré dès le jour 1 de mise en ligne)
- Taux de participation moyen des invités identifiés > 70 %
- Rétention organisateur : > 40 % créent une 2e élection dans les 180 jours
- NPS organisateurs > 30 (mesuré à T+6 mois)

**Électeur :**
- Taux de complétion du vote (lien ouvert → vote validé) > 85 %
- Preuve de vote délivrée à 100 % des votes validés
- Taux de vérification de la preuve de vote (métrique secondaire, à observer sans cible fixe en v2)

**Segment informel :**
- Temps médian de création d'une élection < 2 minutes
- Taux de complétion flux création > 80 % (même indicateur, décliné par segment)
- Taux de partage : > 60 % des élections créées sans compte génèrent au moins 3 votes

### Succès business

**Indicateurs de volume — horizon 12 mois post-lancement :**
- Élections créées / an : 5 250 – 6 050 (vs 4 034 en 2025)
- Votants uniques / an : 44 000 – 51 000 (vs 33 905 en 2025)
- Diversité des segments : au moins 2 sous-segments organisationnels (associatif, éducation, entreprise) dépassent 20 % du volume

**Croissance annuelle cible :** +30 à +50 % par an

### Succès technique

- Plateforme capable de supporter 5 000 votants simultanés sans dégradation
- Instrumentation analytique opérationnelle dès le jour 1 (sans baseline v2, les indicateurs ci-dessus ne sont pas mesurables)
- Temps de réponse : à définir avec l'équipe technique, mais la perception de fluidité est non-négociable sur mobile
- Architecture du moteur de vote découplée — conçue pour permettre l'ajout futur d'une couche de vérifiabilité cryptographique (type Belenios) sans reconstruction

### Succès conformité

- Implémentation des 3 obligations minimales LCEN/DSA dès la mise en prod : traçabilité IP/timestamp, bouton de signalement, CGU acceptées à la création
- Revue juridique par un avocat spécialisé LCEN/DSA : **objectif T+6 mois post-lancement** (non bloquant pour la mise en prod)

### Résultats mesurables

- Instrumentation en place dès le lancement (Plausible, Posthog ou équivalent RGPD-compatible)
- Tracking segmenté : informel vs organisationnel, pour mesurer la diversité des usages
- Baseline v2 établie dans les 30 premiers jours

## Périmètre Produit

### MVP — Minimum Viable Product

- Création d'élection sans compte (flux < 2 minutes)
- Vote par lien et QR code
- Interface pédagogique jugement majoritaire
- Preuve de vote + vérification en temps réel
- Résultats accessibles selon paramètres organisateur
- Traçabilité minimale LCEN (IP + timestamp)
- Bouton de signalement + CGU acceptées à la création
- Instrumentation analytique opérationnelle

### Fonctionnalités de croissance (Post-MVP)

- Comptes organisateurs (magic-link ou login social Google/Apple)
- Tableau de bord des élections et invitations
- Invitations nominatives avec statut en temps réel (envoyé / ouvert / voté)
- Relances automatiques des non-votants
- Liste d'émargement configurable et exportable (PDF/CSV)
- Mode hybride présentiel/distanciel (QR code en salle)

### Vision (Futur)

- Vérifiabilité cryptographique de type Belenios pour élections formelles à forts enjeux
- Intégrations tierces (Slack, Teams) et SSO entreprise
- Support d'autres méthodes de scrutin (architecture prévue, non activée)
- Expansion européenne (multilingue)
- Application mobile native

## Matrix d'option de vote et traduction de leurs intentions

MieuxVoter v2 supporte six modes de vote correspondant à des intentions et contextes distincts :

| Nom | Contexte | Type | Admin | Vote validé par mail | Qui a voté (admin) | Qui a voté (tous) | Qui a voté quoi | Suppression auto | Option résultat | Description | Usage estimé |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Vote rapide** | Informel | Public | Anonyme ou loggé | Non | Non | Non | Non | 30j | Résultat direct | Choix collectif anonyme sans friction — les utilisateurs peuvent voter plusieurs fois. | ⭐ Rare |
| **Vote rapide semi-transparent** | Informel | Public | Anonyme ou loggé | Non | N/A | Oui | Non | 30J | Résultat direct | Choix collectif où la liste d'émargement est visible mais on n'a pas le détail des votes. | ⭐⭐⭐⭐⭐ Très fréquent |
| **Vote rapide transparent** | Informel | Public | Anonyme ou loggé | Non | N/A | N/A | Oui | 30J | Résultat direct | Choix collectif transparent — tout le monde voit comment tout le monde a voté. | ⭐⭐⭐⭐⭐ Très fréquent |
| **Sondage** | Organisé | Public | Loggé | Oui | Non | Non | Non | Non | Configurable (immédiat / à la clôture) | Recueil d'avis ouvert avec traçabilité — un email est requis pour limiter les votes multiples. | ⭐⭐ Occasionnel |
| **Scrutin** | Organisé | Sur invitation | Loggé | N/A | Oui | Non | Non | Non | Configurable (immédiat / à la clôture) | Vote formel sur liste fermée — secret du vote garanti, émargement privé pour l'organisateur. | ⭐⭐⭐⭐ Fréquent |
| **Scrutin avec liste d'émargement publique** | Organisé | Sur invitation | Loggé | N/A | Oui | Oui (nom choisi) | Non | Non | Configurable (immédiat / à la clôture) | Vote formel sur liste fermée — émargement visible par tous avec le nom choisi par l'électeur. Utile pour les AG avec obligation statutaire de transparence sur la participation. | ⭐⭐ Occasionnel |
| **Scrutin transparent** | Organisé | Sur invitation | Loggé | N/A | N/A | N/A | Oui | Non | Configurable (immédiat / à la clôture) | Décision collégiale transparente — jury, comité de recrutement, CA. Chaque membre voit les votes de tous. | ⭐⭐ Occasionnel |

## Parcours Utilisateurs

### 1. Sophie — L'organisatrice informelle (Vote rapide)

**Profil :** Sophie, 28 ans, chef de projet. Chaque vendredi son équipe de 8 personnes débat pendant 20 minutes pour choisir où déjeuner. C'est épuisant et ça finit toujours par le choix de celui qui parle le plus fort.

**Scène d'ouverture :** Lundi matin, Sophie découvre MieuxVoter via un lien partagé sur Twitter. Elle a 2 minutes avant sa réunion.

**Déroulé :**
1. Elle ouvre l'app sur mobile — **sans créer de compte**
2. Elle saisit la question ("Où déjeune-t-on vendredi ?") et 4 options (Sushi, Italien, Libanais, Burger)
3. Elle choisit le mode **Vote rapide semi-transparent** — tout le monde verra qui a voté, mais pas le détail des votes
4. Elle copie le lien et le colle dans le Slack de l'équipe
5. Les 8 collègues votent dans la journée depuis leur téléphone
6. Sophie voit en temps réel la liste des participants et les résultats agrégés — le Libanais gagne haut la main
7. Vendredi : personne ne conteste, tout le monde avait son mot à dire
8. L'élection est automatiquement supprimée au bout de 30 jours

**Moment clé :** En moins de 90 secondes, Sophie a un lien prêt à partager — zéro compte, zéro friction.

**Nouvelle réalité :** Sophie utilise MieuxVoter tous les vendredis. Six mois plus tard, elle le propose à son association de quartier pour élire son bureau — et là elle crée un compte.

**Capabilities révélées :** création sans compte, flux mobile ultra-rapide, partage par lien, résultats en temps réel, suppression automatique 30j, mode Vote rapide semi-transparent.

> **Variante — Vote rapide (anonyme) :** même parcours, mais personne ne voit qui a voté. Idéal quand le groupe est sensible à l'influence sociale. Les utilisateurs peuvent voter plusieurs fois.
>
> **Variante — Vote rapide transparent :** même parcours, mais chacun voit le détail des votes de tous. Adapté aux petits groupes qui veulent une totale transparence (ex. jury informel, choix de design).

---

### 2. Karim — L'organisateur engagé (Sondage)

**Profil :** Karim, 38 ans, responsable bénévole d'une association culturelle de 200 membres. Il veut recueillir l'avis de ses membres sur la programmation de la prochaine saison. Il a besoin d'un résultat crédible — pas d'un vote multiple bourré par deux ou trois militants.

**Scène d'ouverture :** Karim prépare son sondage depuis son ordinateur. Il a une liste d'adhérents mais pas envie de gérer des invitations individuelles — il veut juste s'assurer que chacun ne vote qu'une fois.

**Déroulé :**
1. Karim **crée un compte** via magic-link (son email, c'est tout)
2. Il crée une élection en mode **Sondage** — public, mais chaque vote est validé par email
3. Il saisit sa question et ses options de programmation
4. Il configure l'affichage des résultats : à la clôture uniquement (pour éviter les effets de meute)
5. Il partage le lien dans sa newsletter et sur les réseaux de l'association
6. Chaque votant saisit son email pour valider son vote — un seul vote par adresse
7. À la clôture, Karim consulte les résultats — sans voir qui a voté quoi, seulement les agrégats
8. Il publie les résultats à ses membres avec confiance

**Moment clé :** Karim peut partager le lien publiquement sans craindre le bourrage — l'email agit comme garde-fou sans friction excessive pour les votants légitimes.

**Nouvelle réalité :** Karim utilise MieuxVoter pour tous ses sondages annuels. Il commence à envisager le mode Scrutin pour l'AG.

**Capabilities révélées :** compte organisateur magic-link, mode Sondage, validation email par votant, résultats configurables (immédiat / à la clôture), résultats agrégés sans attribution.

---

### 3. Michel — Le responsable associatif (Scrutin)

**Profil :** Michel, 54 ans, trésorier d'une association culturelle de 120 membres. Chaque année, l'AG élit le bureau. L'an dernier, un membre a contesté le résultat — personne ne pouvait prouver qui avait voté. Michel a reçu des emails pendant trois semaines.

**Scène d'ouverture :** Michel prépare l'AG de juin. Il a la liste des 120 membres adhérents à jour. Il veut un outil qui lui évite le cauchemar de l'an dernier.

**Déroulé :**
1. Michel **crée un compte** (magic-link email — pas de mot de passe à retenir)
2. Il crée une élection en mode **Scrutin** — liste fermée, secret du vote, émargement privé pour lui
3. Il importe sa liste de 120 emails membres
4. Chaque membre reçoit un lien unique personnalisé
5. Michel suit en temps réel : 67/120 ont voté, 12 liens n'ont pas été ouverts
6. Il envoie une relance ciblée aux 53 non-votants — sans savoir comment ils ont voté
7. À la clôture : 98/120 participants, quorum atteint
8. Michel télécharge la liste d'émargement en PDF pour ses archives
9. Les résultats sont proclamés — chaque membre peut vérifier que son vote est dans l'urne

**Moment clé :** Un membre conteste. Michel ouvre la liste d'émargement et montre que le quorum est atteint et que chaque vote est traçable. La contestation s'arrête là.

**Nouvelle réalité :** Michel recommande MieuxVoter à 3 autres associations de son réseau.

**Capabilities révélées :** compte organisateur magic-link, import liste emails, liens uniques par électeur, tableau de bord invitations avec statuts, relances ciblées, liste d'émargement exportable, résultats configurables, preuve de vote vérifiable.

> **Variante — Scrutin avec liste d'émargement publique :** même parcours, mais la liste des participants (avec leur nom choisi) est visible par tous les électeurs. Utile pour les AG avec obligation statutaire de transparence sur la participation.
>
> **Variante — Scrutin transparent :** même parcours sur invitation, mais chaque membre voit le détail des votes de tous. Adapté aux décisions collégiales (jury, comité de recrutement, CA) où la transparence totale est souhaitée.

---

### 4. Aïcha — L'électrice invitée

**Profil :** Aïcha, 41 ans, membre du CA d'une association. Elle reçoit un email de Michel avec un lien pour voter.

**Scène d'ouverture :** Aïcha reçoit l'email un mardi soir. Elle est sur son téléphone, elle a 3 minutes.

**Déroulé :**
1. Elle clique sur son lien unique depuis l'email
2. L'app s'ouvre directement sur le bulletin de vote — pas de compte, pas de friction
3. Un court encart lui explique le jugement majoritaire en 2 phrases et un exemple visuel
4. Elle évalue chaque candidat avec les mentions (Très bien / Bien / Passable / Insuffisant / À rejeter)
5. Elle valide — une animation confirme que son vote est enregistré
6. Elle reçoit sa preuve de vote avec un identifiant unique
7. Trois jours plus tard, curieuse, elle clique sur le lien de vérification : "Votre vote est bien dans l'urne ✓"

**Moment clé :** La confirmation visuelle et la preuve de vote lui donnent confiance dans le processus — elle n'a aucun doute que son vote compte.

**Nouvelle réalité :** Aïcha parle de l'expérience à Michel ("c'était vraiment simple") et suggère de l'utiliser pour d'autres décisions du CA.

**Capabilities révélées :** lien unique par électeur, onboarding pédagogique JM, bulletin de vote mobile-first, confirmation visuelle, preuve de vote avec identifiant, vérification ultérieure.

> **Note — Scrutin semi-transparent ou transparent :** après avoir voté, Aïcha peut voir la liste des participants (semi-transparent) ou le détail des votes de tous (transparent). L'app l'en informe avant qu'elle valide.
>
> **Note — Flux Sondage :** au lieu d'un lien unique, Aïcha accède au bulletin via un lien public et saisit son email pour valider son vote. Pas de preuve de vote dans ce cas — seulement la confirmation de prise en compte.

---

### 5. L'administrateur MieuxVoter — Modération plateforme

**Profil :** Membre de l'équipe MieuxVoter, responsable de la modération et du support.

**Scène d'ouverture :** Un utilisateur signale une élection dont l'intitulé semble diffamatoire envers une personne publique.

**Déroulé :**
1. L'admin reçoit une notification de signalement
2. Il accède au tableau de bord d'administration (liste de tous les signalements en attente)
3. Il consulte l'élection concernée : titre, options, date de création, IP de création, email organisateur si compte existant
4. Il juge le contenu manifestement illicite
5. Il suspend l'élection (elle n'est plus accessible aux votants)
6. Il notifie l'organisateur de la raison de la suspension
7. Il documente l'action dans le journal de modération (traçabilité LCEN)

**Moment clé :** L'action est documentée et traçable — si l'association est mise en cause, elle peut prouver qu'elle a appliqué sa procédure notice-and-action.

**Nouvelle réalité :** L'association est protégée par son statut d'hébergeur, à condition d'agir promptement sur les signalements.

**Capabilities révélées :** interface d'administration plateforme, liste des signalements, accès aux métadonnées de création (IP, email), suspension d'élection, notification organisateur, journal de modération LCEN.

---

### Synthèse des capabilities révélées par les parcours

| Capability | Sophie (Vote rapide) | Karim (Sondage) | Michel (Scrutin) | Aïcha (Électrice) | Admin |
|---|---|---|---|---|---|
| Création sans compte | ✓ | | | | |
| Compte organisateur (magic-link) | | ✓ | ✓ | | |
| Flux mobile < 2 min | ✓ | | | | |
| Suppression automatique 30j | ✓ | | | | |
| Validation email par votant | | ✓ | | | |
| Résultats configurables (immédiat / clôture) | | ✓ | ✓ | | |
| Import liste emails | | | ✓ | | |
| Liens uniques par électeur | | | ✓ | ✓ | |
| Tableau de bord invitations avec statuts | | | ✓ | | |
| Relances ciblées | | | ✓ | | |
| Liste d'émargement exportable | | | ✓ | | |
| Pédagogie JM embarquée | | | | ✓ | |
| Preuve de vote + vérification | | | | ✓ | |
| Confirmation visuelle du vote | | | | ✓ | |
| Interface modération plateforme | | | | | ✓ |
| Signalement + notice-and-action | | | | | ✓ |
| Journal de modération LCEN | | | | | ✓ |

## Exigences Domaine

### Conformité & Réglementation

**LCEN / DSA (hébergeur) :**
- Traçabilité IP + timestamp systématique à la création d'élection (admins uniquement — les votes ne sont pas tracés par IP)
- Bouton de signalement accessible sur chaque élection publique
- Procédure notice-and-action documentée et journal de modération
- CGU claires interdisant les usages illégaux, acceptées à la création d'élection ou de compte

**RGPD :**
- L'organisateur est **responsable de traitement** pour les données personnelles qu'il importe (emails des électeurs) — stipulé explicitement dans les CGU
- MieuxVoter est **sous-traitant** — minimisation des données collectées
- Conservation des données admins : durée à définir avec un juriste (cible indicative : 3 ans post-clôture de l'élection)
- Aucune conservation des données personnelles des votants au-delà du nécessaire

**Responsabilité juridique :**
- MieuxVoter se protège via une **clause limitative de responsabilité** dans les CGU — l'outil ne se substitue pas à un huissier ou prestataire certifié pour les scrutins à valeur légale obligatoire
- Disclaimer affiché dans l'interface pour les scrutins à enjeux formels

### Contraintes Techniques

**Confidentialité des votes :**
- Séparation stricte entre les données d'identité (qui a voté) et les données de vote (comment a voté) — liées uniquement par un token opaque
- **Buffer de votes** : les votes sont collectés dans un buffer et mélangés avant enregistrement, rendant impossible de relier l'ordre d'arrivée à l'identité de l'électeur
- Confidentialité activée selon le mode de vote — certains modes (Scrutin, Scrutin avec liste d'émargement publique) garantissent le secret du vote, d'autres non (Vote transparent, Scrutin transparent)

**Preuve de vote :**
- Token unique généré à la validation du vote, stocké hashé
- Vérifiable par l'électeur à tout moment sans révéler le contenu du vote
- Architecture compatible avec une évolution vers une preuve cryptographique plus robuste (type Belenios) en version future

**Sécurité :**
- Liens de vote uniques par électeur pour les modes sur invitation (non réutilisables, non devinables)
- Protection contre le vote multiple sur les modes publics avec validation email (Sondage)
- Vote rapide : pas de protection contre le vote multiple — documenté et assumé

### Risques & Mitigations

| Risque | Mitigation |
|---|---|
| Manipulation par un organisateur (faux emails, fausse liste d'émargement) | Responsabilité contractuelle de l'organisateur via les CGU — MieuxVoter est sous-traitant |
| Contestation juridique d'un résultat | Clause limitative de responsabilité dans les CGU — vision future : PDF de PV horodaté avec hash des résultats |
| Contenu illicite dans une élection | Procédure notice-and-action, suspension par l'admin MieuxVoter, journal de modération |
| Scalabilité (pic de votants) | Architecture cible : 5 000 votants simultanés sans dégradation |

## Innovation & Patterns Novateurs

### Axes d'innovation détectés

**1. Dévoilement progressif par intention**
Le compte utilisateur n'est jamais promu comme une feature — il est toujours l'aboutissement naturel d'un besoin exprimé par l'utilisateur. Cette approche inverse le modèle classique "créez un compte pour débloquer X" et élimine la friction cognitive pour les usages informels tout en préservant un chemin fluide vers les usages organisationnels.

**2. Buffer de votes**
Les votes sont collectés dans un buffer et mélangés avant enregistrement, rendant impossible de relier l'ordre d'arrivée à l'identité de l'électeur. Simple techniquement, mais rare dans les outils de vote grand public — renforce la confidentialité sans complexité cryptographique.

**3. Matrice de modes de vote**
La taxonomie en 6 modes (informel/organisé × public/invitation × niveaux de transparence) est une modélisation fine du domaine que les concurrents n'ont pas. Elle couvre un spectre complet d'intentions de vote sur une seule plateforme, et peut devenir un avantage produit durable et un outil pédagogique en soi.

**4. Preuve de vote vérifiable sans révéler le contenu**
La combinaison token hashé + URL de vérification appliquée à un outil grand public est peu courante hors des systèmes institutionnels. Elle rend la confiance dans l'urne tangible et visible pour chaque électeur, sans complexité cryptographique en v2 — et est conçue pour évoluer vers une vérifiabilité de type Belenios sans reconstruction.
