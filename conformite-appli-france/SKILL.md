---
name: "conformite-appli-france"
description: "Audite et corrige la conformité légale française d'une appli ou d'un site (RGPD, mentions légales, CGU, consentement, emails, abonnements, stores). À utiliser avant toute mise en ligne ou dès qu'on parle de RGPD, CNIL, mentions légales ou amendes."
---

# Conformité légale d'une appli ou d'un site en France

Ce skill sert à vérifier qu'une application (mobile ou web) ou un site respecte les obligations françaises et européennes courantes, puis à corriger ce qui manque : dans le code quand c'est du code, sous forme de textes prêts à relire quand ce sont des documents légaux.

Il vise les développeurs indépendants et les petites équipes, souvent sans juriste, qui construisent vite (y compris avec l'IA) et oublient les obligations non techniques.

## Principes

- **Dire le risque réel, pas le chiffre qui fait peur.** Les montants qui circulent sont des plafonds légaux, pas des tarifs, et ils ne se multiplient pas « par visiteur ». Pour chaque point, donner le plafond ET ce qui se passe en pratique (mise en demeure d'abord, amendes réelles bien plus basses pour les petits acteurs). L'utilisateur doit pouvoir prioriser calmement.
- **Vérifier avant d'affirmer.** Le droit bouge. Avant de citer un montant, un article de loi ou une règle de store, faire une recherche web sur une source officielle (Légifrance, CNIL, service-public, DGCCRF, règles Apple et Google) et citer la source. Les repères plus bas sont un point de départ daté, pas une vérité permanente.
- **Ne jamais inventer l'identité de l'éditeur.** Nom, statut, SIRET, adresse, hébergeur, contact : les demander, ou laisser des champs `[À COMPLÉTER]` bien visibles. Un texte légal avec de fausses informations est pire que pas de texte.
- **Rester à sa place.** Ce n'est pas un avis d'avocat. Le dire une fois, brièvement, et recommander une relecture professionnelle pour les textes contractuels (CGU, CGV, politique de confidentialité) avant publication. Ne pas le répéter à chaque paragraphe.
- **Corriger, pas seulement lister.** Quand le code est accessible, proposer ou appliquer le correctif concret.

## Déroulé

### 1. Cadrer le projet

Récupérer ces informations (dans la conversation, la mémoire ou le code ; ne demander que ce qui manque, en une seule fois) :

- Type : appli mobile (iOS, Android), appli web, site vitrine, e-commerce
- Statut de l'éditeur : société, entreprise individuelle ou micro-entreprise, particulier non professionnel (les obligations et les plafonds changent)
- Public : des mineurs peuvent-ils s'inscrire ?
- Données collectées, en particulier les données sensibles ou proches (santé, mensurations, poids, localisation, photos)
- Monétisation : abonnements, achats intégrés, paiement externe
- Emails ou notifications à but commercial
- Services tiers : analytics, replay de session, publicité, polices ou scripts chargés depuis des serveurs externes, hébergement hors UE

### 2. Inspecter le code s'il est disponible

Chercher les indices plutôt que de se fier aux déclarations :

- Formulaire d'inscription : champ d'âge ou de date de naissance, cases de consentement, liens vers les documents légaux
- SDK et scripts tiers dans les dépendances et le code : analytics (Firebase, Google Analytics, Mixpanel, PostHog, Amplitude), replay de session (Hotjar, Clarity, FullStory, LogRocket, Smartlook, replay Sentry), publicité, `fonts.googleapis.com`
- Moment où ces outils démarrent : avant ou après le consentement
- Envoi d'emails : expéditeur, lien de désinscription, distinction emails de service / emails commerciaux
- Abonnements : parcours de résiliation, lien vers la gestion d'abonnement du store
- Suppression de compte et export des données
- Sécurité de base : mots de passe hachés, secrets et clés d'API absents du code client, règles d'accès à la base de données, HTTPS

Sans accès au code, faire l'audit à partir des réponses et le signaler comme déclaratif.

### 3. Passer la checklist

**Identité et documents**
- Mentions légales accessibles (éditeur, contact, hébergeur, directeur de publication)
- Politique de confidentialité : données, finalités, bases légales, durées de conservation, destinataires et sous-traitants, transferts hors UE, droits et moyen de les exercer
- CGU, et CGV s'il y a vente (prix, rétractation, médiation de la consommation)
- Liens présents dans l'appli, à l'inscription et sur les fiches des stores

**Données personnelles**
- Collecte minimale : chaque champ demandé a une utilité
- Âge : consentement parental sous l'âge du consentement numérique en France
- Données sensibles : consentement explicite et séparé, sécurité renforcée
- Droits : accès, rectification, suppression, export
- Registre des traitements simple, contrats avec les sous-traitants
- Procédure en cas de fuite de données

**Traceurs et outils tiers**
- Rien de non essentiel ne démarre avant consentement ; refuser est aussi simple qu'accepter
- Replay de session désactivé par défaut, champs sensibles masqués
- Polices et scripts auto-hébergés quand c'est possible
- Sur iOS : demande de suivi (ATT) si suivi publicitaire

**Communication**
- Emails commerciaux : consentement préalable pour les particuliers (ou exception client existant), expéditeur identifié, lien de désinscription fonctionnel dans chaque message
- Notifications push : opt-in

**Abonnements et paiement**
- Prix, durée et renouvellement clairs avant achat
- Résiliation en ligne facile ; pour un achat via Apple ou Google, lien direct vers la gestion d'abonnement du store
- Information sur le renouvellement automatique

**Exigences des stores**
- Suppression de compte depuis l'appli
- Fiches de confidentialité (Apple « Privacy Nutrition Labels », Google « Sécurité des données ») cohérentes avec le code réel
- Classification d'âge correcte

**Selon le projet**
- Contenu généré par les utilisateurs : signalement et modération
- Accessibilité, droit de rétractation, TVA, facturation
- Appli sport ou santé : avertissement que les contenus ne remplacent pas un avis médical

### 4. Rendre le rapport

Format court, lisible sur téléphone. Commencer par le verdict en une phrase, puis trois groupes :

- **Bloquant** : à corriger avant mise en ligne (illégal de façon évidente ou motif de rejet par les stores)
- **Important** : à corriger rapidement
- **À améliorer** : bonnes pratiques

Pour chaque point : le constat (avec le fichier ou l'écran concerné), le risque réel en une ligne (plafond + pratique, source citée), le correctif. Ne pas lister ce qui est déjà conforme, sauf un court « déjà en ordre » à la fin.

### 5. Corriger

- **Code** : appliquer ou fournir les modifications (champ d'âge, écran de consentement, démarrage différé des SDK, bouton de suppression de compte, lien de résiliation, lien de désinscription, auto-hébergement des polices). Respecter la pile technique et le style du projet.
- **Textes** : rédiger mentions légales, politique de confidentialité et CGU adaptées au projet réel, en français clair, avec les champs `[À COMPLÉTER]` pour tout ce qui n'est pas connu. Les livrer comme documents à relire, pas comme version définitive.
- Terminer par ce qui reste à faire côté utilisateur (informations à fournir, relecture par un professionnel, déclarations dans les consoles des stores).

## Repères chiffrés (vérifiés en novembre 2026, à revérifier)

- Absence de mentions légales (LCEN) : jusqu'à 75 000 € et un an d'emprisonnement pour une personne physique, 375 000 € pour une société. Condamnations rares ; un cas connu de 2014 : 6 000 €.
- Résiliation en ligne des abonnements (Code de la consommation, L215-1-1) : jusqu'à 15 000 € pour une personne physique, 75 000 € pour une société.
- Prospection par email sans consentement ou sans désinscription (CPCE, L34-5) : jusqu'à 75 000 € pour une personne physique, 375 000 € pour une société.
- CNIL, procédure simplifiée : plafond de 20 000 € par décision, quel que soit le manquement. La procédure ordinaire peut aller jusqu'à 20 M€ ou 4 % du chiffre d'affaires mondial, ce qui vise les gros acteurs.
- Polices Google : décision d'un tribunal de Munich en 2022 (100 € de dommages à un visiteur). Décision allemande, qui concerne les sites web chargeant les polices depuis les serveurs de Google.
- Replay de session : en France, c'est une question de consentement aux traceurs ; la qualification d'« écoute illégale » vient de procès américains.

À vérifier systématiquement avant de les citer : l'âge du consentement numérique en France, les règles actuelles d'Apple et de Google, et tout montant ci-dessus.