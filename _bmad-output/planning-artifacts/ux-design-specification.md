---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8]
inputDocuments:
  - "_bmad-output/planning-artifacts/product-brief-perso-app.mieuxvoter.fr-v2.md"
  - "_bmad-output/planning-artifacts/prd.md"
  - "docs/110 home page.png"
  - "docs/120 candidats.png"
  - "docs/130 Add candidate.png"
  - "docs/140 candidats.png"
  - "docs/150 paramètres.png"
  - "docs/190 admin.png"
  - "docs/320 vote.png"
  - "docs/353 Animation.png"
  - "docs/mobile/10 00 home page.png"
  - "docs/mobile/20 00 admin candidats list.png"
  - "docs/mobile/20 20 admin add candidat.png"
  - "docs/mobile/30 00 admin parametres.png"
  - "docs/mobile/60 00 admin edit.png"
  - "docs/mobile/20 00 voter vote.png"
  - "docs/mobile/40 00 voter fini.png"
---

# UX Design Specification - MieuxVoter v2

**Author:** MieuxVoter
**Date:** 2026-05-13

---

<!-- UX design content will be appended sequentially through collaborative workflow steps -->

## Executive Summary

### Vision produit

MieuxVoter v2 est une plateforme unifiée de vote par jugement majoritaire à dévoilement progressif. Le parcours par défaut (non connecté) est optimisé pour la vitesse : question + options + lien en moins de 2 minutes sur mobile. Les fonctionnalités organisationnelles (invitations, émargement, relances) se débloquent naturellement quand l'utilisateur en exprime le besoin — jamais imposées en amont.

Le design repart du système visuel de la v1 (bleu roi, typographie bold, mentions colorées, stepper numéroté) et l'étend pour absorber la complexité nouvelle sans la faire peser sur les usages simples.

### Utilisateurs cibles

| Utilisateur | Contexte | Appareil | Priorité |
|---|---|---|---|
| Sophie — organisatrice informelle | Vote rapide, sans compte, < 2 min | Mobile | MVP |
| Karim — organisateur engagé (sondage) | Compte magic-link, liste publique | Desktop/mobile | Post-MVP |
| Michel — responsable associatif (scrutin) | Compte, invitations nominatives, émargement | Desktop | Post-MVP |
| Aïcha — électrice invitée | Lien reçu par email, vote en 3 min | Mobile | MVP |
| Admin MieuxVoter | Modération, traçabilité LCEN | Desktop | MVP |

### Défis UX clés

**1. La matrice de 7 modes sans friction cognitive**
Solution retenue : afficher tous les modes dans le flux de création, avec les modes "organisateur connecté" visibles mais grisés. Un clic sur un mode grisé déclenche une popup "Connectez-vous pour accéder à ce mode". Simple, transparent, pédagogique.

**2. La transition anonyme → connecté au bon moment**
Le compte ne s'impose jamais en amont — il est la réponse naturelle à un besoin exprimé. La popup de connexion doit être légère (magic-link, pas de formulaire lourd) et apparaître seulement au moment du clic sur une option qui la requiert.

**3. La confiance dans le vote (preuve de vote)**
La preuve de vote est un différenciateur produit clé, pas un détail technique. Elle doit être visuellement mémorable, facile à retrouver, et son utilité doit être expliquée au bon moment (après validation du vote, pas avant).

**4. Créer en < 2 min sur mobile**
Le stepper 3 étapes de la v1 reste la bonne structure. La v2 doit absorber le nouveau step "choix du mode" sans allonger la durée perçue — en le plaçant en premier (avant les candidats), contextualisé et rapide à traverser pour Sophie.

### Opportunités design

**1. Le bulletin de vote comme signature visuelle forte**
Les mentions en boutons verticaux (v1 mobile) sont déjà distinctives. La v2 peut renforcer cet aspect avec une micro-animation à la sélection et un traitement couleur plus expressif du dégradé rouge → vert.

**2. La page de résultats comme argument de vente**
L'affichage du résultat JM (mention majoritaire + classement) est l'endroit où l'utilisateur comprend pourquoi cette méthode est meilleure. C'est le moment fort à soigner visuellement.

**3. Le design system de la v1 comme accélérateur**
Le style existant (bleu roi, boutons outlined, stepper, chips mentions) est cohérent et réutilisable. Pas besoin de repartir de zéro — on étend, on ne reconstruit pas.

## Core User Experience

### Defining Experience

Deux actions cœur définissent le produit :

**Pour Sophie (MVP) :** Créer un vote et partager le lien. C'est l'action la plus fréquente, la plus critique, et celle qui conditionne tout le reste. Si elle prend plus de 2 minutes ou demande un effort cognitif, l'utilisateur retombe sur WhatsApp.

**Pour Aïcha (MVP) :** Voter sur un bulletin, comprendre ce qu'on lui demande, et sentir que son vote compte. C'est l'action la plus visible — chaque électeur la vit, l'organisateur non.

### Platform Strategy

- **Web app mobile-first** (PWA) — pas d'app native en v2
- Navigation tactile prioritaire ; support clavier/souris pour les écrans organisateur (desktop)
- Pas d'offline requis
- Le bulletin de vote (électeur) est le seul écran qui doit fonctionner sur des connexions mobiles lentes/instables — priorité de performance absolue sur cet écran
- Les écrans organisateur connecté (tableau de bord, invitations) sont majoritairement desktop — mise en page adaptée

### Effortless Interactions

| Interaction | Ce qui doit être invisible |
|---|---|
| Créer un vote | Pas de compte, pas de formulaire d'inscription — on pose la question et on choisit les options directement |
| Partager le lien | Un tap pour copier, QR code généré automatiquement |
| Voter | Un tap par mention, validation en un bouton — zéro navigation complexe |
| Se connecter (magic-link) | Saisir son email → recevoir le lien → cliquer → connecté. Pas de mot de passe, jamais |
| Débloquer un mode grisé | Un clic → popup magic-link → retour au flux de création avec le mode débloqué |

### Critical Success Moments

| Moment | Enjeu |
|---|---|
| **La saisie de la question** (premier écran) | Si l'UX hésite ici, Sophie part. Le champ doit être focalisé, le CTA évident, aucun obstacle |
| **La sélection du mode de vote** | Si les options sont illisibles ou trop nombreuses, l'utilisateur choisit n'importe quoi ou abandonne |
| **La validation du bulletin** | Aïcha doit ressentir que son acte a compté — confirmation visuelle forte, pas juste un "OK" |
| **La preuve de vote** | Le différenciateur produit. Doit être explicite, mémorable, et rassurant — pas un token cryptique |
| **Les résultats** | Le moment où l'utilisateur comprend pourquoi le JM est meilleur — visualisation claire de la mention majoritaire |

### Experience Principles

1. **La vitesse avant tout pour les usages informels** — chaque champ, chaque étape du flux anonyme est justifiée. Si c'est optionnel pour Sophie, c'est absent par défaut.
2. **Voir avant de s'engager** — les modes grisés montrent ce qui existe sans forcer l'inscription. L'utilisateur choisit de se connecter parce qu'il en voit la valeur, pas parce qu'on l'y oblige.
3. **La confiance se construit à chaque étape** — confirmation du vote, preuve de vote, vérification ultérieure. Chaque micro-moment de réassurance renforce la légitimité perçue du résultat.
4. **Le style de la v1 est un actif, pas une contrainte** — on l'étend proprement, on ne le contourne pas. Chaque nouvel écran doit sembler appartenir à la même famille.

## Desired Emotional Response

### Primary Emotional Goals

**Sophie — organisatrice informelle :**
**Efficacité → Légèreté → Fierté**
"C'est fait, c'est partagé, c'est propre." Elle veut ressentir qu'elle a réglé un problème de groupe rapidement et intelligemment — sans que ça lui ait coûté de l'énergie.

**Aïcha — électrice :**
**Confiance → Légitimité → Satisfaction**
"Mon vote compte, et je peux le prouver." Elle ne doit jamais douter que son geste a eu de l'effet. La preuve de vote transforme une transaction en engagement.

**Michel — organisateur associatif :**
**Contrôle → Sérénité → Crédibilité**
"Je maîtrise mon élection, je peux répondre à n'importe quelle question." La douleur v1 était l'impuissance face à la contestation — la v2 doit la retourner en assurance.

### Emotional Journey Mapping

| Moment | Émotion visée | Émotion à éviter |
|---|---|---|
| Découverte / page d'accueil | Curiosité, invitation | Intimidation, surcharge |
| Saisie de la question (1er écran) | Focus, fluidité | Friction, hésitation |
| Choix du mode de vote | Clarté, contrôle | Confusion, peur de mal choisir |
| Bulletin de vote (électeur) | Calme, expression | Anxiété, incompréhension |
| Validation du vote | Accomplissement, soulagement | Doute ("ça a bien marché ?") |
| Preuve de vote | Confiance, réassurance | Indifférence |
| Résultats | Compréhension, légitimité | Frustration, scepticisme |
| Retour à l'app (2e usage) | Reconnaissance, familiarité | Sentiment de recommencer de zéro |

### Micro-Emotions

- **Confiance vs. scepticisme** — critique sur le vote et la preuve. Le design doit signaler le sérieux sans austérité.
- **Efficacité vs. frustration** — chaque seconde de friction sur le flux de création est une perte de confiance pour Sophie.
- **Accomplissement vs. doute** — la confirmation de vote doit être physiquement ressentie (animation, texte fort) — pas juste un changement d'état discret.
- **Légèreté vs. pesanteur** — malgré les enjeux civiques, l'app doit rester accessible et humaine. Le bleu roi de la v1 est fort mais peut paraître sévère — équilibre à maintenir.

### Design Implications

- **Confiance** → Typographie lisible, hiérarchie claire, jamais d'ambiguïté sur l'état actuel (stepper toujours visible, états bien nommés)
- **Efficacité** → Zéro champ superflu sur le flux anonyme, CTA toujours visible et atteignable au pouce, pas de scroll caché
- **Accomplissement** → Animation de confirmation du vote plein écran (cf. v1 — à conserver et renforcer), message humain et chaleureux (pas "Succès" mais "Votre voix a été enregistrée")
- **Légèreté** → Illustrations expressives pour les moments de succès, tonalité éditoriale détendue mais sérieuse, erreurs formulées sans culpabilisation

### Emotional Design Principles

1. Chaque moment de transition (vote validé, lien copié, mode débloqué) mérite une réponse visuelle explicite — pas de silence de l'interface.
2. La tonalité éditoriale est humaine et encourageante — on ne parle pas à un "utilisateur", on parle à quelqu'un qui veut décider collectivement.
3. L'erreur n'est jamais une faute — les messages d'erreur expliquent sans accuser et proposent toujours une sortie.
4. La confiance se mérite progressivement — pas d'exigence d'engagement (compte, email) avant que l'utilisateur ait vu la valeur du produit.

## UX Pattern Analysis & Inspiration

### Inspiring Products Analysis

**Doodle (concurrent direct simplifié)**
Création ultra-rapide, partage par lien immédiat, zéro friction. L'onboarding ne commence pas par un compte — il commence par la valeur. À éviter : interface vieillissante, grille de créneaux non applicable.

**Typeform**
Une question à la fois, progression claire, animations fluides — le formulaire ne ressemble pas à un formulaire. La saisie séquentielle réduit la charge cognitive perçue sur les flux longs. Applicable au flux de création avec compte (Karim, Michel). À ne pas surappliquer : trop linéaire pour les experts.

**Notion / Linear (magic-link)**
Connexion par email sans mot de passe, naturelle et rapide. Le magic-link bien présenté ("Vérifiez votre boîte mail — le lien expire dans 10 minutes") est rassurant. La v2 doit soigner ce micro-moment.

**Stripe (confirmation et états)**
Chaque action produit un feedback visuel immédiat et explicite — loading states, confirmations, erreurs. Jamais de silence de l'interface. Les états de chargement et de succès sont des opportunités de design, pas des détails techniques.

**Belenios (anti-référence)**
UX austère, aucune pédagogie embarquée, destiné aux experts. Anti-pattern direct : ne jamais supposer que l'utilisateur comprend le JM — toujours contextualiser sans alourdir.

### Transferable UX Patterns

**Navigation & structure**
- Stepper numéroté (v1) — à conserver, fonctionne bien sur mobile
- CTA fixé en bas de l'écran (atteignable au pouce) — déjà présent en v1, à maintenir
- Progression visible à tout moment — réduit l'anxiété du "combien de temps ça va prendre"

**Interactions**
- Sélection par tap pleine largeur (mentions de vote en v1) — excellent sur mobile, à conserver
- Options grisées + popup magic-link de déblocage (Option B validée) — pattern "cadenas" universellement compris (App Store, Spotify, Notion)
- Copie de lien en un tap + feedback "Copié !" — micro-interaction indispensable pour le partage
- Swipe horizontal entre candidats (bulletin de vote v1) — naturel sur mobile, à conserver

**Visuels**
- Confirmation plein écran avec illustration (v1) — moment fort, à renforcer
- Dégradé de couleur sur les mentions (rouge → vert) — signature visuelle MieuxVoter, à conserver
- Cartes blanches sur fond sombre — bon contraste, lisible, à conserver

### Anti-Patterns to Avoid

- **Inscription avant la valeur** — ne jamais bloquer la création sans compte
- **Options cachées derrière un scroll non signalé** — sur mobile, ce qui n'est pas visible n'existe pas
- **Messages d'erreur cryptiques** — toujours expliquer et proposer une action
- **Stepper trop long** — maximum 4 étapes, même avec les nouveaux modes de vote
- **Jargon JM non contextualisé** — "mention majoritaire" doit toujours être accompagnée d'une explication courte à la première occurrence
- **Toasts pour confirmations importantes** — confirmation du vote = plein écran, pas un toast éphémère

### Design Inspiration Strategy

**À adopter directement :**
- Stepper + CTA bas fixe (v1)
- Confirmation plein écran illustrée (v1) — renforcer l'animation et le message
- Magic-link avec instructions claires (Notion/Linear)

**À adapter :**
- Sélection du mode de vote : cards avec description scannables — l'utilisateur compare les modes d'un coup d'œil. Modes nécessitant un compte : grisés avec icône cadenas, popup magic-link au clic (Option B validée).

**À éviter :**
- Formulaires multi-colonnes sur mobile
- One-question-at-a-time (Typeform) pour la sélection du mode — on veut la comparaison, pas la séquentialité

## Design System Foundation

### Design System Choice

Décision ouverte — deux options viables, à trancher par l'équipe technique en début d'implémentation.

**Option A — Radix UI + Tailwind CSS + dnd-kit**
Composants accessibles (Radix) + styles utilitaires (Tailwind) + drag & drop (dnd-kit, déjà en place en v1).
- Accessibilité WCAG 2.1 AA quasi-gratuite sur les composants complexes (modales, toggles, selects)
- Tailwind mobile-first par défaut
- Tokens MieuxVoter (bleu roi, dégradé mentions) configurables dans tailwind.config
- **Risque :** recréer le style visuel de la v1 par-dessus Radix peut demander plus d'effort que prévu — les composants Radix sont unstyled mais ont leur propre structure DOM

**Option B — Design system v1 étendu + dnd-kit**
Repartir des composants React existants, les auditer, les nettoyer, et les étendre avec les nouveaux composants nécessaires (cards de mode, cadenas, tableau de bord organisateur).
- Cohérence visuelle garantie avec la v1
- Pas de dépendance externe supplémentaire
- **Risque :** le design system v1 est éclaté — sans audit et nettoyage sérieux en amont, on reproduit la dette

### Composants à implémenter (communs aux deux options)

- **Stepper** (3-4 étapes, mobile)
- **Bulletin de vote** (carte candidat + mentions verticales, swipe horizontal)
- **Chips mentions** (dégradé rouge → vert, états selected/unselected)
- **Card de mode de vote** (avec état grisé + icône cadenas)
- **Popup magic-link** (modale légère)
- **CTA fixé en bas** (pleine largeur mobile)
- **Toggle paramètres** (avec description sous le label)
- **Drag & drop liste** (réordonnancement candidats et mentions) — dnd-kit dans les deux cas

### Stack décidée

- **Framework :** React (existant v1, reconduit)
- **Drag & drop :** dnd-kit (existant v1, reconduit)
- **Styles :** à confirmer par l'équipe technique (Tailwind si Option A, CSS existant étendu si Option B)

## 2. Core User Experience

### 2.1 Defining Experience

MieuxVoter v2 a deux expériences définissantes, une par rôle :

**Côté organisateur — "Poser une question et obtenir un lien"**
> *"Je pose ma question, j'ajoute mes options, je copie le lien."*

C'est le geste central. Tout le reste (modes, paramètres, invitations) est du raffinement autour de ce geste.

**Côté électeur — "Exprimer mon opinion sur chaque option"**
> *"Je clique sur chaque candidat, je donne ma note, j'envoie."*

C'est le moment le plus visible et le plus pédagogique — si l'électeur comprend ce qu'il fait ici, il devient un ambassadeur du JM.

### 2.2 User Mental Model

**Organisateur :** arrive avec le modèle Doodle/Google Forms — "remplir un formulaire et obtenir quelque chose de partageable". Le JM est une nouveauté, mais le geste de "créer un sondage" ne l'est pas. On s'appuie sur ce modèle connu et on surprend positivement sur le résultat.

**Électeur :** arrive avec le modèle "vote à un tour" (je choisis UN candidat). Le JM demande d'évaluer TOUS les candidats — rupture de modèle mental. L'encart pédagogique (2 phrases + exemple, dismissable) est obligatoire mais ultra-court.

### 2.3 Success Criteria

**Organisateur :**
- Le champ de question est le premier élément visible, focusé automatiquement
- Le bouton "Copier le lien" est atteignable sans scroll sur mobile
- Aucune friction entre "j'arrive sur l'app" et "j'ai un lien à partager"

**Électeur :**
- L'électeur comprend qu'il doit évaluer TOUS les candidats sans avoir lu de doc
- Le bouton "Envoyer" n'est pas actif tant qu'un candidat n'a pas de mention → évite les votes incomplets
- La confirmation est mémorable — pas un simple "merci"

### 2.4 Novel UX Patterns

Pattern établi (cartes de choix) + légèrement novateur (évaluation de tous les candidats vs. choix unique). Pas besoin d'inventer — juste de bien contextualiser via l'encart pédagogique.

**Décision produit future (Post-MVP) :** exposer une option "Sans avis" par candidat sur le bulletin. L'interface devra avertir l'électeur qu'une absence de mention augmente les chances d'élection du candidat concerné — message pédagogique, pas culpabilisant.

### 2.5 Experience Mechanics

**Flux organisateur :**
1. **Initiation** — champ centré sur la page d'accueil, placeholder incitatif, focus automatique
2. **Interaction** — saisie question → ajout options → choix du mode (cards, modes compte grisés avec cadenas) → paramètres optionnels → génération du lien
3. **Feedback** — lien affiché avec bouton "Copier", feedback "Copié !" immédiat, QR code en un clic
4. **Complétion** — lien dans le presse-papier, options de partage natif mobile visibles

**Flux électeur :**
1. **Initiation** — ouverture du lien → bulletin direct (pas de page intermédiaire), encart JM dismissable en haut
2. **Interaction** — une carte par candidat, swipe horizontal, mentions en boutons verticaux pleine largeur, tap pour sélectionner (couleur immédiate), pagination visible
3. **Feedback** — mention sélectionnée colorée immédiatement, progression candidat X/N visible en bas
4. **Complétion** — bouton "Envoyer mon vote" actif quand tous les candidats ont une mention, animation plein écran de confirmation, preuve de vote avec lien de vérification

## Visual Design Foundation

### Color System

| Rôle | Hex | Usage |
|---|---|---|
| **Primary** | `#2400FD` | Fond principal, boutons primaires, stepper actif |
| **Darker** | `#18048F` | Fond sections secondaires, cartes sombres |
| **Darkest** | `#0A004C` | Fond le plus profond, ombres |
| **Coral** | `#FF3E37` | Illustrations, icônes destructives, erreurs |
| **Surface** | `#FFFFFF` | Cartes, modales, champs de saisie |

**Dégradé mentions (7 niveaux) :**

| Mention | Hex |
|---|---|
| À rejeter | `#661800` |
| Insuffisant | `#C23D13` |
| Passable | `#C27C13` |
| Assez bien | `#C2B113` |
| Bien | `#D3D715` |
| Très bien | `#A0CF1C` |
| Excellent | `#3A9918` |

**États :**
- Grisé (cadenas) : opacité 40% sur le Primary + icône cadenas blanc
- Erreur : `#FF3E37` (Coral)
- Succès : `#3A9918` (Excellent)

### Typography System

- **Police :** DM Sans (Google Fonts, libre)
- **Tailles :** à définir lors de l'implémentation
- **Hiérarchie de niveaux :** H1 / H2 / H3 / Body / Label — DM Sans Bold pour les titres, Medium pour les labels, Regular pour le corps
- **Ton :** moderne, accessible, pas austère

### Spacing & Layout Foundation

- **Unité de base :** 8px
- **Marges latérales mobiles :** 16px
- **Espacement liste :** 12px entre items, 24px entre sections
- **Border radius :** 2-4px sur boutons (style carré assumé), 8px sur cartes
- **Layout mobile :** colonne unique, CTA fixé en bas (safe area iOS)
- **Layout desktop :** centré, max-width 800px formulaires, ~1200px dashboard admin

### Accessibility Considerations

- Contraste Primary `#2400FD` sur blanc : à vérifier lors de l'implémentation (ratio cible ≥ 4.5:1 — NFR-17)
- Mentions sombres (À rejeter, Insuffisant, Passable) : texte blanc par-dessus
- Mentions claires (Bien `#D3D715`, Très bien `#A0CF1C`) : texte foncé requis par-dessus
- DM Sans : excellente lisibilité à petite taille, compatible lecteurs d'écran
