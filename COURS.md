# Cours PHP - Les Bases

## Formation Web Développeur - CF2M Bruxelles

> **Classe** : 2

> **Version** : 2026

> **Prérequis** : HTML, CSS, bases en algorithmique

> **PHP** : Version 8.x

> **Auteur** : Michaël J. Pitz Pour le [CF2M](https://www.cf2m.be/formation/developpeur-web) - Centre de Formation 2 Mille

---

## Introduction

Bien que l'écosystème `PHP contemporain` soit largement dominé par la **Programmation Orientée Objet** (`POO`) et les frameworks complexes (**Symfony, Laravel, etc**), l'apprentissage initial du **paradigme procédural** ([lien](https://fr.wikipedia.org/wiki/Programmation_proc%C3%A9durale)) demeure **une étape pédagogique incontournable**. 

Il permet aux apprenants de comprendre le flux d'exécution séquentiel, la gestion d'état et la logique brute sans la surcharge cognitive liée à l'abstraction des classes et des objets. L'unique exception à cette règle procédurale sera l'utilisation de l'extension `PDO` (PHP Data Objects) et la gestion des Exceptions, qui seront introduites comme des standards industriels indispensables pour garantir la sécurité et la portabilité des interactions avec les bases de données.

---


## Table des matières

1. [Présentation de PHP](#1---présentation-de-php)
2. [Historique de PHP](#2---historique-de-php)
3. [Installation de l'environnement](#3---installation-de-lenvironnement)
4. [Algorithmique - Rappels fondamentaux](#4---algorithmique---rappels-fondamentaux)
5. [Les bases de PHP](#5---les-bases-de-php)
   - [Les fichiers PHP](#51---les-fichiers-php)
   - [Les balises PHP](#52---les-balises-php)
   - [Les commentaires](#53---les-commentaires)
   - [Placement des balises PHP](#54---placement-des-balises-php-dans-le-html)

## 1 - Présentation de PHP

![PHP Elephpant](Data/Elephpant.png)

**PHP**, acronyme récursif de **Hypertext Preprocessor**, est un langage de script utilisé le plus souvent côté serveur.

Dans cette architecture, le serveur **interprète** le code PHP des pages web demandées et génère du code (HTML, CSS, XML, JSON, JavaScript…) et/ou des données (JPEG, GIF, PNG, SVG, PDF…) pouvant être interprétés et rendus par un **navigateur web**.

`PHP` a été conçu pour permettre la création d'**applications dynamiques**, le plus souvent développées pour le Web. Étant un langage de type **script**, il n'est pas obligatoirement compilé pour être exécuté. Il est donc interprété à chaque appel de page par le serveur (sauf pour la compilation à la volée `JIT` ou par gestion des caches).

`PHP` est le plus souvent couplé à un serveur **Apache**, bien qu'il puisse être installé sur la plupart des serveurs HTTP tels que **IIS** (Microsoft), **Nginx** ou **Caddy** (langage `GO` pour une vitesse d'exécution accrue).

Ce couplage permet de récupérer des informations issues d'une **base de données**, d'un système de fichiers, ou plus simplement des données envoyées par le navigateur afin d'être interprétées ou stockées pour une utilisation ultérieure.

C'est un langage qui peut, comme au début de ce cours, être **peu typé** et souple, donc facile à apprendre par un débutant, mais de fait moins sécurisé et plus difficile à maintenir. Un typage fort est donc conseillé par la suite avec l'adoption de la **Programmation Orientée Objet** (POO), qui sera abordée dans le cours avancé.

**Caractéristiques principales :**

- **Libre et gratuit** : PHP est open source
- **Multi-plateforme** : fonctionne sur Linux, Windows et macOS
- **Simple d'installation** et d'utilisation pour un débutant
- **Améliorations constantes** : nouvelles fonctionnalités et optimisations régulières ([lien](https://endoflife.date/php))
- **Grande communauté** : documentation abondante, forums actifs
- **Utilisé massivement** : WordPress, Magento, Laravel, Symfony, Drupal, Joomla, etc.
- Nécessite une **connaissance aiguë des problèmes de sécurité**

📖 **Documentation officielle** : [https://www.php.net/manual/fr/](https://www.php.net/manual/fr/)

📖 **Documentation W3C** : [PHP Tutorial](https://www.w3schools.com/php/default.asp)

---

[Retour à la table des matières](#table-des-matières)

---

## 2 - Historique de PHP

| Année | Version | Événement clé |
|-------|---------|---------------|
| 1994 | - | Création par **Rasmus Lerdorf** (Personal Home Page) |
| 1995 | PHP 1 | Annonce officielle comme langage de script côté serveur |
| 1996-97 | PHP/FI 2 | Support des formulaires web, bases de données, sessions |
| 1998 | PHP 3 | Moteur remanié, modules, module Apache, début de la POO |
| 2000 | PHP 4 | Améliorations de la POO, performances accrues (Zend Engine 1) |
| 2004 | **PHP 5** | **POO native**, exceptions, espaces de noms, Zend Engine 2 |
| 2015 | **PHP 7** | **Performances x2** (Zend Engine 3), types de retour scalaires |
| 2020 | **PHP 8.0** | Attributs, arguments nommés, **JIT compiler**, `match`, union types |
| 2021 | **PHP 8.1** | Enums, propriétés `readonly`, fibres |
| 2022 | **PHP 8.2** | Classes readonly, types DNF, constantes dans les traits |
| 2023 | **PHP 8.3** | Constantes typées dans les classes, `json_validate()`, `#[Override]` |
| 2024 | **PHP 8.4** | Hooks de propriétés, visibilité asymétrique, nouvelle API DOM |
| 2025-2026 | **PHP 8.5** | En cours de développement, opérateur Pipe, Clone With, nouvelles fonctions de manipulation de tableaux |

> ⚠️ **PHP 6 n'a jamais existé** officiellement — le projet a été abandonné.

📖 [Historique complet sur php.net](https://www.php.net/manual/fr/history.php.php)

---

[Retour à la table des matières](#table-des-matières)

---

## 3 - Installation de l'environnement

Pour développer en PHP, nous avons besoin de trois composants :

1. **Un serveur web** (Apache ou Nginx)
2. **PHP** (interpréteur)
3. **Un serveur de base de données** (MySQL ou MariaDB)

### 3.1 - Packages tout-en-un

| OS | Package | Lien |
|----|---------|------|
| Windows | **WAMP** | [wampserver.com](https://www.wampserver.com/) |
| Windows | WAMP + add-ons | [wampserver.aviatechno.net](https://wampserver.aviatechno.net/) - **Conseillé sous Windows** |
| macOS | **XAMPP** | [apachefriends.org](https://www.apachefriends.org/fr/index.html) |
| Linux | **LAMP** | Installation manuelle via apt/yum, vaut pour WSL2 sous Windows |
| Tous | **Docker** | [docker.com](https://www.docker.com/) |

### 3.2 - Installation de WAMP (Windows)

Téléchargez WAMP sur [wampserver.aviatechno.net](https://wampserver.aviatechno.net/) et suivez les instructions.

📖 Tutoriel d'installation : [README.md#installation-de-wamp-sous-windows](README.md#installation-de-wamp-sous-windows)

### 3.3 - Installation de XAMPP (macOS)

Nous préférons XAMPP à MAMP, car MAMP (version gratuite) pose des problèmes de droits d'accès.

📖 Tutoriel : [https://www.ionos.fr/digitalguide/serveur/outils/tutoriel-xampp-creer-un-serveur-de-test-local/](https://www.ionos.fr/digitalguide/serveur/outils/tutoriel-xampp-creer-un-serveur-de-test-local/)

### 3.4 - Vérification de l'installation

Créez un fichier `01-info.php` dans votre dossier `Stagiaires\{Prenom}`  avec le contenu suivant :

```php
<?php
phpinfo();
```

Ouvrez cette page dans votre navigateur en passant par un `hôte virtuel` (WAMP) ou `www`, `htdocs`, etc . Vous devriez voir une page détaillant la configuration PHP.

> ⚠️ **Supprimez ce fichier en production** : il révèle des informations sensibles sur votre serveur.

---

[Retour à la table des matières](#table-des-matières)

---

## 4 - Algorithmique - Rappels fondamentaux

Avant de coder en PHP, il est **fondamental** de comprendre les bases de l'algorithmique. La programmation n'est que la **traduction d'un algorithme** dans un langage donné.

### 4.1 - Qu'est-ce qu'un algorithme ?

Un algorithme est une suite d'instructions **finies**, **ordonnées** et **non ambiguës**, permettant de résoudre un problème ou d'accomplir une tâche.

**Exemple quotidien** : une recette de cuisine est un algorithme.

### 4.2 - Les briques fondamentales

Tout programme informatique repose sur **trois structures** de base :

1. **Les séquences** : instructions exécutées l'une après l'autre
2. **Les conditions** (structures de sélection) : choix entre plusieurs chemins
3. **Les boucles** (structures de répétition) : répétition d'instructions

### 4.3 - Les variables en algorithmique

Une variable est un **conteneur nommé** qui stocke une valeur en mémoire.

```
ALGORITHME calculSomme
VARIABLES
    a : ENTIER
    b : ENTIER
    somme : ENTIER
DÉBUT
    a ← 5
    b ← 3
    somme ← a + b
    AFFICHER somme
FIN
```

### 4.4 - Les conditions en algorithmique

```
SI condition ALORS
    instruction(s)
SINON SI autre_condition ALORS
    instruction(s)
SINON
    instruction(s)
FIN SI
```

### 4.5 - Les boucles en algorithmique

**Boucle POUR** (nombre d'itérations connu) :
```
POUR i DE 0 À 10
    AFFICHER i
FIN POUR
```

**Boucle TANT QUE** (nombre d'itérations inconnu) :
```
TANT QUE condition
    instruction(s)
FIN TANT QUE
```

### 4.6 - Les fonctions en algorithmique

```
FONCTION addition(a : ENTIER, b : ENTIER) : ENTIER
    RETOURNER a + b
FIN FONCTION
```

📖 **Ressources algorithmique** :
- [Cours d'algorithmique - France IOI](http://www.france-ioi.org/)
- [Algorithmique pour l'apprenti programmeur - OpenClassrooms](https://openclassrooms.com/fr/courses/7527306-decouvrez-le-fonctionnement-des-algorithmes)
- [Exercices d'algorithmique - Prologin](https://prologin.org/)

> 💡 **Conseil** : Avant d'écrire du code PHP, écrivez d'abord votre algorithme en pseudo-code !

---

[Retour à la table des matières](#table-des-matières)

---

## 5 - Les bases de PHP

### 5.1 - Les fichiers PHP

Les fichiers PHP sont des fichiers texte enregistrés avec l'extension `.php`. Le code PHP est exécuté **sur le serveur**, et le résultat est renvoyé au navigateur sous forme de code HTML (ou autre).

### 5.2 - Les balises PHP

Le code PHP est écrit entre les balises `<?php` et `?>`.

```php
<?php
echo "Hello World";
?>
```

Il existe une **balise courte** `<?= ?>` équivalente à `<?php echo ?>` :

```php
<?= "Hello World" ?>
```

**Règles importantes :**

- Le `;` termine chaque instruction (première cause d'erreur pour les débutants !)
- Le `;` est **facultatif** juste avant `?>`
- Si le fichier ne contient **que du PHP**, on **ne ferme pas** la balise `?>` (bonne pratique)

```php
<?php
echo "Hello World";
echo "<br>Hello friends";
// Pas de ?> en fin de fichier = bonne pratique
```

📖 [Documentation : Balises PHP](https://www.php.net/manual/fr/language.basic-syntax.phptags.php)

#### ✏️ Exercice 01
> Créez un fichier `01-hello-world.php` qui affiche **"Hello World"** dans le navigateur.

#### ✏️ Exercice 02
> Créez un fichier `02-hello-world-short.php` qui affiche **"Hello World"** en utilisant la balise courte `<?= ?>`.

#### ✏️ Exercice 03
> Créez un fichier `03-hello-friends.php` qui affiche **"Hello World"** suivi de **"Hello friends"** sur la ligne suivante.

---

### 5.3 - Les commentaires

Les commentaires sont des lignes **non exécutées** par le serveur. Ils servent à documenter et rendre le code lisible.

```php
<?php
// Commentaire sur une ligne

# Commentaire sur une ligne (style shell)

/*
Commentaire
sur plusieurs lignes
*/
```

📖 [Documentation : Commentaires](https://www.php.net/manual/fr/language.basic-syntax.comments.php)

#### ✏️ Exercice 04
> Créez un fichier `04-commentaires.php` qui **n'affiche rien** dans le navigateur, mais contient les trois types de commentaires.

---

### 5.4 - Placement des balises PHP dans le HTML

Les balises PHP peuvent être placées **n'importe où** dans un document HTML :

```php
<?php
  // Code PHP en début de fichier
  $date = date("Y-m-d H:i:s");
?>
<!DOCTYPE html>
<html lang="fr">
<head>
  <title>Ma page - <?= date("H:i") ?></title>
</head>
<body>
  <h1>Date : <?= $date ?></h1>
  <p>Il est <?= date("H:i:s") ?></p>
</body>
</html>
```

Nous avons utilisé la fonction native `date()` et stocké le résultat dans une **variable** `$date`.

📖 [Documentation : date()](https://www.php.net/manual/fr/function.date.php) | [Formats de date](https://www.php.net/manual/fr/datetime.format.php)

#### ✏️ Exercice 05
> Créez un fichier `05-php-placement.php` qui affiche la date et l'heure du serveur dans une page HTML complète.

---

[Retour à la table des matières](#table-des-matières)

---