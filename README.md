# Projet réalisé pendant mon jour d'intégration à **Ynov**
# Ypokémon ⚔️

Ypokémon est une petite application web qui permet de **faire combattre deux Pokémon** en se basant sur leurs vraies statistiques récupérées depuis une API publique.  
Elle se joue directement dans le navigateur, sans backend.

---

## ✨ Fonctionnalités

- Saisie du **nom d’un Pokémon** pour chaque côté (Pokémon 1 et Pokémon 2).  
- Récupération automatique des données depuis l’API `https://tyradex.vercel.app/api/v1/pokemon/{nom}`.  
- Affichage :
  - Sprite du Pokémon  
  - Type principal (icône)  
  - Points de vie (barre de progression)  
  - Attaque, Défense, Attaque Spé, Défense Spé, Vitesse  
- Bouton **« Combattre »** qui lance un combat automatique tour par tour.  
- Calcul des dégâts simple à chaque seconde, avec mise à jour des barres de vie.  
- Détection du vainqueur ou du match nul, avec message de résultat.

---

## 🧱 Technologies utilisées

- **HTML5** pour la structure de la page.  
- **CSS / Bootstrap 5.3** (via CDN) pour la mise en forme et le layout responsive.  
- **JavaScript Vanilla** pour :
  - Appeler l’API Tyradex (via `fetch`)  
  - Mettre à jour le DOM (images, stats, barres de vie)  
  - Gérer la boucle de combat (avec `setInterval`).  

---

## 📁 Structure du projet (simplifiée)

ypokemon/
├── index.html # Page principale (tout le code HTML + JS intégré)
└── assets/
└── img.pokeball.png # Icône Pokéball affichée dans le titre

## 🚀 Lancer le projet

Aucune installation compliquée n’est nécessaire.

1. Télécharge ou clone le projet.  
2. Ouvre simplement `index.html` dans ton navigateur (double‑clic ou clic droit → « Ouvrir avec »).  
3. Assure‑toi d’avoir une connexion Internet (pour :  
   - le CDN Bootstrap  
   - l’API `https://tyradex.vercel.app`).

C’est tout : l’application est prête à l’emploi.

---

## 🎮 Comment utiliser l’application

1. Dans le champ **« Pokémon 1 »**, tape le nom d’un Pokémon (par exemple `pikachu`).  
2. Dans le champ **« Pokémon 2 »**, tape le nom d’un autre Pokémon.  
3. À chaque changement :
   - L’application appelle l’API Tyradex.  
   - Affiche l’image, le type et les statistiques du Pokémon.  
   - Met à jour la barre de PV (points de vie).  
4. Quand **les deux Pokémon sont valides**, le bouton **« Combattre »** se déverrouille.  
5. Clique sur **« Combattre »** :
   - Toutes les secondes, chaque Pokémon inflige des dégâts à l’autre :  
     `dégâts = max(0, attaque - défense adverse)`  
   - Les PV diminuent visuellement dans la barre de progression.  
   - Quand un ou deux Pokémon tombent à 0 PV :
     - Affichage du message :  
       - `X gagne !` si un seul survit  
       - `Match nul !` si les deux tombent en même temps.  
   - Le combat s’arrête automatiquement.

---

## 🧠 Détails algorithmiques (simplifiés)

- **HP_MAX = 250** : valeur max utilisée pour normaliser l’affichage des PV en pourcentage.  
- Chaque Pokémon possède un objet `stats` (hp, atk, def, spe_atk, spe_def, vit).  
- À chaque « tour » (toutes les 1 seconde) :
  - On calcule les dégâts reçus par Pokémon 1 :  
    `damageToPokemon1 = max(0, pokemon2.stats.atk - pokemon1.stats.def)`  
  - Idem pour Pokémon 2.  
  - On met à jour les PV, puis on met à jour l’affichage (largeur de la barre + texte).  
- Les images sont estompées (opacity = 0.2) quand un Pokémon tombe K.O.

---

## 💡 Pistes d’amélioration

- Ajouter la prise en compte du **type** (faiblesses / résistances).  
- Prendre en compte la **vitesse** pour déterminer qui attaque en premier.  
- Afficher un historique du combat (log des tours).  
- Séparer le JavaScript dans un fichier `script.js` dédié.  
- Gérer proprement les erreurs (Pokémon introuvable, faute de frappe, API down).

---

## 👨‍💻 Auteurs

- Projet front‑end réalisé en HTML, Bootstrap et JavaScript.  
- Utilise l’API **Tyradex** comme base de données Pokémon.
