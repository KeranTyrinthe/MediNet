# MediNet – Localisation intelligente des médicaments à Lubumbashi (V1)

## 🎯 Objectif principal
MediNet est une plateforme web et mobile permettant aux habitants de Lubumbashi de rechercher des médicaments et des services médicaux (en cas d’urgence) via un système de géolocalisation.

## 👥 Rôles dans le système

1. **Utilisateur normal (patient)** : Recherche les médicaments et consulte les disponibilités autour de lui.
2. **Pharmacie** : Gère ses informations, ses stocks et ses prix.
3. **Hôpital** : Gère également ses stocks internes de médicaments et leurs disponibilités.
4. **Administrateur** : Supervise l’ensemble du système, les données et les activités (sans devoir valider manuellement les inscriptions).

## ⚙ Fonctionnalités détaillées

### 🧾 1. Authentification, Registre et gestion des comptes
**Objectif** : Garantir un accès sécurisé et personnalisé selon le type d’utilisateur.

#### Pour tous :
- Création de compte via e-mail et mot de passe.
- Connexion sécurisée (chiffrement des mots de passe).
- Réinitialisation du mot de passe par e-mail.
- Déconnexion et gestion de session sécurisée.

#### Types d’inscription :
- **Utilisateur normal (patient)** : Connexion sans identification requise. Formulaire simple (nom complet, e-mail, mot de passe, téléphone facultatif).
- **Admin** : Formulaire simple (nom complet, e-mail, mot de passe, téléphone facultatif).
- **Hôpital / Pharmacie** :
  1. Nom de l’établissement.
  2. Type (case à cocher : Hôpital ou Pharmacie).
  3. E-mail professionnel.
  4. Mot de passe d’accès à la plateforme.
  5. Téléphone principal et secondaire.
  6. Adresse complète (commune, avenue, quartier, numéro, ville).
  7. Coordonnées GPS exactes (sélection sur carte).
  8. Nom et fonction du responsable ou pharmacien en chef.
  9. Horaires d’ouverture (optionnel).
  10. Services fournis (opération, accouchement…).
  11. Possibilité de renseigner manuellement un quartier ou une commune si le GPS est désactivé.
  12. Médicaments en stock.

Une fois le formulaire soumis, l’établissement est immédiatement ajouté au système, peut être localisé par les patients, et l’administrateur peut superviser les nouveaux comptes.

### 🏥 2. Tableau de bord HÔPITAL / PHARMACIE
**Objectif** : Permettre à chaque établissement de gérer son inventaire et ses informations (ex. : dossiers médicaux ou ordonnances).

#### a. Gestion du profil
- Mise à jour des informations générales (adresse, contact, horaires, responsable, etc.).
- Ajout ou modification de la position géographique sur la carte (restreindre les modifications à 6 mois pour la sécurité).
- Photo/logo de l’établissement (optionnel).

#### b. Gestion des médicaments
- **Ajout d’un médicament** :
  - Nom du médicament.
  - Catégorie (antibiotique, antipaludéen, antalgique, etc.).
  - Prix unitaire.
  - Quantité disponible.
  - Date d’expiration.
  - Statut de disponibilité : “En stock”, “Rupture de stock”.
- Modification et suppression des médicaments existants.
- Historique des mises à jour (dates et quantités modifiées).
- Filtrage par nom, catégorie, disponibilité.
- **Système d’alerte interne** :
  - Notification lorsque le stock devient faible (ex. <10 unités).
  - Notification lorsqu’un médicament est proche d'expirer (ex. <2 mois).
- Vue d’ensemble du stock total.
- Statistiques internes (nombre de médicaments enregistrés, en stock, en rupture, expirant).

#### c. Liste de consultation (en cas de réservation)

### 👤 3. Tableau de bord UTILISATEUR NORMAL
**Objectif** : Permettre à toute personne de rechercher rapidement un médicament disponible autour d’elle.

#### a. Géolocalisation
- Détection automatique de la position actuelle via GPS.
- Possibilité de renseigner manuellement un quartier ou une commune si le GPS est désactivé.
- Visualisation de sa position sur la carte interactive.

#### b. Recherche de médicaments
- Saisie du nom du médicament dans la barre de recherche.
- Affichage des résultats selon :
  - Proximité géographique (distance calculée à partir de la position de l’utilisateur).
  - Disponibilité (en stock).
  - Prix (si renseigné).
  - Type d’établissement (Hôpital / Pharmacie).

#### c. Détails d’un résultat
Pour chaque établissement trouvé :
- Nom de l’établissement.
- Type (pharmacie / hôpital).
- Adresse complète.
- Distance depuis la position actuelle.
- Nom et prix du médicament.
- Quantité disponible.
- Statut de disponibilité par établissement.
- Bouton “Voir sur la carte” → ouvre la position sur la carte.
- Bouton “Itinéraire” → redirige vers Google Maps ou OpenStreetMap pour s’y rendre.

#### d. En cas d’indisponibilité
- Si le médicament n’est pas trouvé à proximité : Message : “Aucune pharmacie ou hôpital proche ne dispose actuellement de ce médicament.”
- Suggestion du lieu le plus proche où il est disponible, même s’il est plus éloigné.

#### e. Historique (optionnel)
- L’utilisateur peut voir ses 5 dernières recherches.
- Suggestions automatiques basées sur l’historique (le plus fréquenté par exemple).

### 🧭 4. Carte interactive (géolocalisation intelligente)
**Objectif** : Visualiser les établissements et les médicaments disponibles sur une carte claire. Intégration avec OpenStreetMap (ou Leaflet.js pour affichage).

- Marqueurs colorés :
  - 🏥 Bleu : Hôpitaux
  - 💊 Vert : Pharmacies
- Clic sur un marqueur → affiche les informations de l’établissement + liste des médicaments disponibles.
- Recherche dynamique sur la carte : zoom automatique vers la zone pertinente.

### 🧑‍💼 5. Tableau de bord ADMINISTRATEUR
**Objectif** : Offrir une supervision complète du système, sans gérer les inscriptions manuellement.

#### a. Gestion des utilisateurs
- Liste complète des comptes : Utilisateurs, Pharmacies, Hôpitaux.
- Possibilité de suspendre ou réactiver un compte en cas d’abus ou d’erreur.
- Supprimer un établissement inactif.

#### b. Supervision globale
- Accès à toutes les informations : Médicaments enregistrés par chaque établissement, stocks disponibles, dernières mises à jour.
- Visualisation de la carte globale des établissements actifs.
- Consultation des recherches les plus fréquentes (ex. “Paracétamol”, “Amoxicilline”).

#### c. Statistiques & analyses
- Nombre total d’utilisateurs.
- Nombre total de pharmacies / hôpitaux actifs.
- Nombre total de médicaments enregistrés.
- Médicaments les plus recherchés.
- Taux d’indisponibilité moyen.
- Graphiques simples de suivi d’activité.

#### d. Journalisation
- Enregistrement automatique des actions importantes : Ajout / suppression de médicament, connexion / déconnexion d’un établissement, mises à jour de stock, recherches des utilisateurs.

### 📊 6. Système de recherche centralisé
**Objectif** : Interroger simultanément toutes les bases de données des établissements.

- Recherche textuelle intelligente (corrige les fautes mineures de frappe).
- Indexation automatique des nouveaux médicaments ajoutés.
- Filtrage par type d’établissement, prix ou distance.
- Résultats triés automatiquement par pertinence.

### 🔔 7. Notifications (version légère pour la V1)
- **Notification interne pour les hôpitaux / pharmacies** : “Stock faible sur Paracétamol (5 unités restantes).” “Un utilisateur a recherché un médicament que vous possédez.” (optionnel pour plus tard).
- **Notification admin** : “Nouveau compte créé : Pharmacie du Centre.”

### 🔐 8. Sécurité et confidentialité
- Chiffrement des mots de passe.
- Protection des requêtes API.
- Accès restreint selon le rôle.
- Aucune donnée médicale personnelle enregistrée.
- Respect de la confidentialité des utilisateurs.

## Installation et Configuration

[Instructions d'installation à ajouter, basées sur Laravel.]

## Technologies Utilisées

- Framework : Laravel (PHP)
- Base de données : [Spécifier, ex. MySQL]
- Cartes : OpenStreetMap / Leaflet.js
- Autres : [Ajouter si connu]

## Contribution

Les contributions sont les bienvenues ! Veuillez suivre les directives de Laravel.

## Licence

Ce projet est sous licence MIT.

## Contact

Pour plus d'informations, contactez l'équipe de développement.
