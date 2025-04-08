# 🗓️ Générateur d'Emploi du Temps en PDF

Ce projet Python génère automatiquement un **emploi du temps hebdomadaire** pour des cours (ECUs) et leurs enseignants, puis le convertit en **fichier PDF formaté** à l’aide de la bibliothèque `reportlab`.

## 📌 Fonctionnalités

- Génère un horaire hebdomadaire à partir des ECUs et de leur nombre de crédits.
- Attribue les cours à différentes séances sur 5 jours (Lundi à Vendredi).
- Formate et exporte l’emploi du temps en **fichier PDF bien présenté** .
- Permet une pagination automatique du document (1 page par 3 semaines).

## 🧠 Logique du Projet

## Modélisation CSP

- Les **enseignants** sont stockés dans le dictionnaire `Profs`.
- Les **cours (ECUs)** sont dans le dictionnaire `ECUs`, chaque ECU ayant un certain nombre de crédits (1 crédit = 5 séances).
- La **classe `Queue`** est une file héritée de `deque` avec une méthode `pop()` personnalisée pour un comportement FIFO.

***Variables :***
Chaque cours = variables → à quelles périodes il est assigné (ex: IA → Lundi P1, Lundi P2, etc.)

***Domaines :***
Les périodes disponibles, ex: Jour_Période comme Lundi_1, Lundi_2, Lundi_3, Mardi_1...

***🕒 Contraintes :***

•	3 périodes par jour.
•	Chaque enseignant enseigne **au maximum 2 périodes par jour**.
•	Un enseignant donne **un seul cours à la fois**.
•	**15 heures de TPE** par semaine (**soit 5 périodes**).
•	Réduire le nombre de **semaines → regrouper au max.**.

### Génération d'emploi du temps

- On crée une liste de séances (`Queue`) à partir des ECUs.
- On répartit les séances sur 3 créneaux par jour, 5 jours par semaine.
- Une règle spéciale empêche qu’un même cours apparaisse deux fois d’affilée dans la même demi-journée.
- L'emploi du temps est stocké dans une liste de semaines (`rows`), et converti en PDF à l'aide de `reportlab`.

## 📂 Structure du Code

- `Profs`: Dictionnaire contenant les enseignants.
- `ECUs`: Dictionnaire des cours avec crédits et affectations aux enseignants.
- `Queue`: Classe personnalisée pour gérer les séances.
- `create_pdf`: Fonction pour générer le fichier PDF.
- `main`: Génère les données et appelle `create_pdf`.

## 📦 Dépendances

Installe les bibliothèques nécessaires avec pip :

```bash
pip install reportlab
```

## ▶️ Exécution

Lance simplement le script (Pour Groupe 1 par exemple si on a navigué dans le dossier Groupe 1):

```bash
python groupe1_gestion_horaire.py
```

Un fichier `Emploi_du_temps.pdf` sera généré dans le répertoire courant.

## 🖨️ Exemple de sortie

Le PDF contient :

- Le titre "Horaire"
- Le nombre de semaines générées
- Une table par semaine avec les jours et trois séances (matin, milieu, après-midi)
- Les cours et noms des enseignants dans chaque case

