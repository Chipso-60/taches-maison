# Tâches de la maison

Une petite app de to-do list pour suivre les tâches ménagères, pensée pour iPhone.
C'est une web app (PWA) : elle s'installe depuis Safari sur l'écran d'accueil et fonctionne ensuite comme une app, même hors ligne.

**Ouvrir l'app :** https://chipso-60.github.io/taches-maison/

## Fonctionnalités

- Tâches classées par pièce : Cuisine, Salle de bain, Salon, Chambres, Linge, Extérieur, Courses, Autre.
- Pour chaque tâche : la personne qui s'en charge et une échéance.
- Tâches récurrentes : chaque jour, chaque semaine, toutes les 2 semaines ou chaque mois. Quand on coche une tâche, sa prochaine échéance se calcule toute seule.
- Vue **À faire** avec les tâches rangées par échéance : en retard, aujourd'hui, cette semaine, plus tard, sans date, fait aujourd'hui.
- Vues **Toutes** (par pièce) et **Terminées**, et filtre par pièce.
- Résumé en haut de l'écran : tâches en retard, du jour et faites sur les 7 derniers jours.
- Mode clair ou sombre selon le réglage de l'iPhone.

## Installer sur iPhone

1. Ouvrez **https://chipso-60.github.io/taches-maison/** dans **Safari**. Tapez l'adresse en entier : sans `/taches-maison/`, la page affiche une erreur 404.
2. Touchez **Partager**, puis **Sur l'écran d'accueil**, puis **Ajouter**.
3. Lancez « Maison » depuis l'écran d'accueil.

## Données et sauvegarde

- Les tâches sont enregistrées **uniquement sur l'appareil** (`localStorage`). Rien n'est envoyé sur Internet, et rien n'est partagé entre plusieurs téléphones.
- **Supprimer l'icône de l'écran d'accueil efface les tâches.** Pensez à exporter régulièrement.
- Le bouton ↓ en haut à droite permet de :
  - **exporter** les tâches dans un fichier `.json`, à ranger dans Fichiers, iCloud Drive ou à envoyer par AirDrop ;
  - **importer** une sauvegarde. Les tâches importées sont fusionnées avec celles déjà présentes : une tâche qui existe déjà est remplacée par sa version importée.

## Fichiers

| Fichier | Rôle |
| --- | --- |
| `index.html` | Toute l'app : interface, styles et logique |
| `manifest.webmanifest` | Nom, icônes et affichage plein écran de l'app installée |
| `sw.js` | Service worker : garde l'app en cache pour l'utiliser hors ligne |
| `icon-180.png`, `icon-192.png`, `icon-512.png` | Icônes (écran d'accueil iPhone, Android, grande taille) |

Aucune dépendance et aucune étape de build : ce sont de simples fichiers statiques.

## Mettre à jour l'app

1. Modifiez les fichiers.
2. Changez la constante `VERSION` dans `sw.js`, par exemple `maison-v2`. Sans ce changement, l'iPhone peut continuer à utiliser l'ancienne version gardée en cache.
3. Envoyez les changements sur GitHub :
   ```
   git add .
   git commit -m "Description du changement"
   git push
   ```
4. GitHub Pages republie le site en une minute environ. Sur l'iPhone, fermez puis rouvrez l'app pour charger la nouvelle version.

Les tâches enregistrées ne sont pas touchées par une mise à jour.

## Tester en local

Il faut servir les fichiers en HTTP : ouvrir `index.html` directement depuis le disque désactive le mode hors ligne. Par exemple :

```
python -m http.server 8000
```

puis ouvrez http://localhost:8000/.
