# TP React Hooks - Application de Blog

Ce TP a pour objectif de mettre en pratique l'utilisation des Hooks React (useState, useEffect, useCallback, useMemo) ainsi que la création de Hooks personnalisés à travers une application de blog simple.

## Installation et configuration initiale

1. Cloner le dépôt :
```bash
git clone https://github.com/pr-daaif/tp-react-hooks-blog.git
cd tp-react-hooks-blog
```

2. Créer votre propre dépôt sur Github et changer le remote :
```bash
# Supprimer le remote origine
git remote remove origin

# Ajouter votre nouveau remote
git remote add origin https://github.com/[votre-username]/tp-react-hooks-blog.git

# Premier push
git push -u origin main
```

3. Installer les dépendances :
```bash
npm install
```

4. Lancer l'application :
```bash
npm start
```

## Instructions pour le TP

Pour chaque exercice :
1. Lisez attentivement l'énoncé
2. Implémentez la solution
3. Testez votre implémentation (pensez à faire des copies d'écran)
4. Mettez à jour la section correspondante dans ce README avec :
   - Une brève explication de votre solution
   - Des captures d'écran montrant le fonctionnement
   - Les difficultés rencontrées et comment vous les avez résolues
5. Commitez vos changements avec un message descriptif

### Exercice 1 : État et Effets 
#### Objectif : Implémenter l'affichage et la recherche de posts

- [ ] 1.1 Compléter le hook `usePosts` pour récupérer les posts depuis l'API dummyjson.com
- [ ] 1.2 Implémenter le composant `PostList` pour afficher les posts
- [ ] 1.3 Ajouter la fonctionnalité de recherche par titre ou contenu dans `PostSearch`
- [ ] 1.4 Documenter votre solution ici

## Captures d'écran :
### Capture de l'affichage des posts
![screen1](https://github.com/user-attachments/assets/e6b7fdc1-879f-4889-88d2-1522ed60566f)

### Capture de la barre de recherche fonctionnelle
![screen2](https://github.com/user-attachments/assets/bec39c93-f371-4326-bdf8-d6549e1b8587)


### Exercice 2 : Hooks Personnalisés
#### Objectif : Créer des hooks réutilisables

- [ ] 2.1 Créer le hook `useDebounce` pour optimiser la recherche
- [ ] 2.2 Créer le hook `useLocalStorage` pour persister les préférences utilisateur
- [ ] 2.3 Utiliser ces hooks dans l'application
- [ ] 2.4 Documenter votre solution ici

2.1 - J'ai créé le hook useDebounce qui utilise un délai de 500ms pour éviter d'appeler l'API à chaque frappe dans le champ de recherche. Il est utilisé dans le hook usePosts pour limiter les requêtes inutiles.

2.2 - J'ai créé le hook useLocalStorage qui permet de sauvegarder une valeur dans le localStorage. Il est utilisé dans App.jsx pour mémoriser le mode de défilement choisi par l’utilisateur.

2.3 - Les deux hooks sont utilisés dans l'application :

useDebounce : dans usePosts.js, pour attendre que l’utilisateur ait fini de taper avant de déclencher la recherche.
useLocalStorage : dans App.jsx, pour enregistrer la préférence de scroll (préparation à l'exercice 4) et dans ThemeContext.js (préparation exercice 3).
Difficulté rencontrée :
Le challenge principal a été de bien synchroniser useDebounce avec la logique de fetch. J'ai résolu cela avec un useEffect propre et bien isolé.

### Exercice 3 : Optimisation et Context
#### Objectif : Gérer le thème global et optimiser les rendus

- [ ] 3.1 Créer le `ThemeContext` pour gérer le thème clair/sombre
- [ ] 3.2 Implémenter le composant `ThemeToggle`
- [ ] 3.3 Utiliser `useCallback` et `useMemo` pour optimiser les performances
- [ ] 3.4 Documenter votre solution ici

## Captures d'écran :
### Blog page avec le bouton ThemeToggle visible
![sceen3](https://github.com/user-attachments/assets/0af3abab-b25d-4676-a9c3-7aa4524cefde)

### Blog page en mode sombre (dark mode)
![sreen4](https://github.com/user-attachments/assets/80b71664-9f54-46d2-abff-4b7e7e2e407a)

### Champ de recherche optimisé (déclenche la recherche avec un debounce)




### Exercice 4 : Fonctionnalités avancées
#### Objectif : Ajouter des fonctionnalités de chargement et détail

- [ ] 4.1 Implémenter le chargement infini des posts avec `useIntersectionObserver`
- [ ] 4.2 Créer le composant `PostDetails` pour afficher les détails d'un post
- [ ] 4.3 Ajouter la fonctionnalité de filtrage par tags
- [ ] 4.4 Documenter votre solution ici

## Captures d'écran :

### Chargement infini des posts (scroll jusqu’en bas)
![sceen6](https://github.com/user-attachments/assets/28f93091-9b0f-4639-b79e-c49162cb57e6)

### Détails d’un post sélectionné avec réactions et tags
![sreenn7](https://github.com/user-attachments/assets/2cb60317-c051-45e3-a3d1-f656ef6925ee)

### Filtrage des posts par tag sélectionné (#tech, #code...)
![screen8](https://github.com/user-attachments/assets/bcad1a61-9c2e-4b67-9e8f-2b1cd28a55b5)

## ✅  Résultat final
Une application fluide avec chargement progressif, navigation détaillée, et filtrage dynamique par tags

Une expérience optimisée côté utilisateur avec un code modulaire et réutilisable
![screen9](https://github.com/user-attachments/assets/e89d4a7b-8bed-4ad6-8dfb-8103f3f1aa56)






## Structure détaillée du projet

```
📁 ./
├─ 📄 README.md
├─ 📄 package.json
├─ 📁 public/
│  └─ 📄 index.html
└─ 📁 src/
   ├─ 📄 App.js               # Composant principal de l'application
   ├─ 📄 App.css              # Styles CSS de l'application
   ├─ 📁 components/
   │  ├─ 📄 PostList.js       # Liste des posts
   │  ├─ 📄 PostSearch.js     # Barre de recherche
   │  ├─ 📄 PostDetails.js    # Détails d'un post
   │  ├─ 📄 ThemeToggle.js    # Bouton pour changer de thème
   │  └─ 📄 LoadingSpinner.js # Indicateur de chargement
   ├─ 📁 hooks/
   │  ├─ 📄 usePosts.js       # Hook pour gérer les posts
   │  ├─ 📄 useDebounce.js    # Hook pour débouncer les valeurs
   │  ├─ 📄 useLocalStorage.js # Hook pour gérer le localStorage
   │  └─ 📄 useIntersectionObserver.js # Hook pour le chargement infini
   ├─ 📁 context/
   │  └─ 📄 ThemeContext.js   # Contexte pour le thème
   ├─ 📄 index.css
   └─ 📄 index.js
```

## Ressources utiles

- Documentation de l'API: [https://dummyjson.com/docs/posts](https://dummyjson.com/docs/posts)
- Documentation React Hooks: [https://fr.reactjs.org/docs/hooks-intro.html](https://fr.reactjs.org/docs/hooks-intro.html)
- Guide sur les hooks personnalisés: [https://fr.reactjs.org/docs/hooks-custom.html](https://fr.reactjs.org/docs/hooks-custom.html)


