# conformite-appli-france

Skill pour Claude qui vérifie qu'une application (mobile ou web) ou un site respecte les obligations légales françaises et européennes, puis corrige ce qui manque.

## Ce qu'il fait

- Cadre le projet : type d'appli, statut de l'éditeur, données collectées, monétisation
- Inspecte le code : inscription, SDK tiers, consentement, emails, abonnements, sécurité
- Passe une checklist : mentions légales, politique de confidentialité, CGU, RGPD, traceurs, prospection, résiliation, règles Apple et Google
- Rend un rapport priorisé : bloquant, important, à améliorer
- Corrige le code et rédige les textes légaux à relire

## Principes

- Donne le risque réel, pas le chiffre qui fait peur : les montants légaux sont des plafonds, pas des tarifs
- Vérifie chaque montant et chaque règle sur une source officielle avant de les citer
- N'invente jamais l'identité de l'éditeur (SIRET, adresse, hébergeur)

## Installation

Copier le dossier `conformite-appli-france` dans `.claude/skills/` de votre projet, ou l'ajouter à vos skills dans Claude.

## Avertissement

Ce skill ne remplace pas un avocat. Faites relire vos textes contractuels par un professionnel avant publication.
