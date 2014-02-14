# 5 - Les listes

--------------------------------------------------------------------------------

# Introduction

Une liste HTML est une sorte de paragraphe structuré permettant d'énumérer des informations.

## 3 types de liste

Il existe trois de types de listes distincts :

* Les listes ordonnées
* Les listes non ordonnées
* Les listes de définitions

--------------------------------------------------------------------------------

# Les listes ordonnées

Ce type de liste permet d'énumérer des informations ordonnées, préfixées par un numéro. Une liste ordonnée s'écrit avec les balises ``<ol>`` et ``<li>``.

## Exemple
    !html
    <ol>
      <li>Éteindre la télévision</li>
      <li>Faire chauffer un café</li>
      <li>S'exercer à HTML et CSS</li>
    </ol>

## Rendu

1. Éteindre la télévision
2. Faire chauffer un café
3. S'exercer à HTML et CSS

--------------------------------------------------------------------------------

# Les listes non-ordonnées

Ce type de liste permet d'énumérer des informations non ordonnées, préfixées par une puce. Une liste non-ordonnée s'écrit avec les balises ``<ul>`` et ``<li>``.

## Exemple
    !html
    <ul>
      <li>Travailler les mises en page en tableau</li>
      <li>Réviser le cours d'HTML</li>
      <li>Bien comprendre l'architecture client / serveur</li>
    </ul>

## Rendu

* Travailler les mises en page en tableau
* Réviser le cours d'HTML
* Bien comprendre l'architecture client / serveur

--------------------------------------------------------------------------------

# Les listes de définitions

Elles permettent de présenter une liste de termes associés à une description. Une liste de définitions utilise trois balises spécifiques : ``<dl>``, ``<dt>`` et ``<dd>``.

## Exemple
    !html
    <dl>
      <dt>HTML</dt><dd>Hypertext Markup Language</dd>
      <dt>CSS</dt><dd>Cascading Stylesheet</dd>
    </dl>

## Rendu

HTML : 
    
&nbsp;&nbsp;&nbsp;&nbsp;Hypertext Markup Language

CSS  :
    
&nbsp;&nbsp;&nbsp;&nbsp;Cascading Stylesheet

--------------------------------------------------------------------------------

# Créer un menu vertical

--------------------------------------------------------------------------------

# Utiliser les listes

Toujours dans l'objectif de respecter la sémantique HTML, on utilise généralement
une liste pour créer un menu (``<ul>`` par exemple). 

Cette liste contiendra bien sûr des liens (``<a>``).

## Exemple

    !html
    <ul id="menu">
      <li><a href="..." title="aller à la page 1">Page 1</a></li>
      <li><a href="..." title="aller à la page 2">Page 2</a></li>
      <li><a href="..." title="aller à la page 3">Page 3</a></li>
      <li><a href="..." title="aller à la page 4">Page 4</a></li>
    </ul>

Il est très utile de donner un identifiant à la balise ``<ul>`` pour agir facilement
sur les différents composants de la liste en CSS.

--------------------------------------------------------------------------------

# Menu vertical : la balise ``<ul>``

Quelques actions CSS nécessaires sur la balise ``<ul>`` :

* Supprimer les marges intérieures et extérieures (différences entre les navigateurs)
* Supprimer les puces

&nbsp;

    !css
    #menu {
      margin: 0;
      padding: 0;
      list-style: none;
    }

Éventuellement, il peut être nécessaire de fixer la largeur de la liste (selon
le dimensionnement du conteneur de la liste).

--------------------------------------------------------------------------------

# Menu vertical : la balise ``<li>``

Quelques actions CSS possibles sur la balise ``<li>`` :

* Changer la couleur de fond
* Ajouter une bordure
* Éventuellement ajouter une marge

&nbsp;

    !css
    #menu li {
      background-color: #00627F;
      border: 1px solid #000;
    }

--------------------------------------------------------------------------------

# Menu vertical : la balise ``<a>``

Un directive très importante ici: il est intéressant de modifier le ``display``
de la balise ``<a>`` en ``block`` pour qu'elle occupe toute la place du ``<li>``. 
C'est ce qui permettra que toute la ligne soit clickable et pas seulement le texte.

Quelques autres actions CSS possibles :

* Gérer la hauteur de la ligne
* Changer la couleur de la police
* Changer la police
* ...

&nbsp;

    !css
    #menu li a {
      display: block;
      line-height: 1.1em;
      color: #fff;
    }

--------------------------------------------------------------------------------

# Menu vertical : la balise ``<a>``

Pour rendre ce menu un petit plus interactif, on utilise les *pseudo-classes*
CSS ``:hover`` et ``:active``.

* ``hover`` : Les règles s'appliquent à l'élément si l'utilisateur passe sa souris dessus
* ``active`` : Les règles s'appliquent à l'élément si l'utilisateur clique dessus

&nbsp;

    !css
    #menu li a:hover {
      background-color: #C9F2FF;
      color: #00627F;
    }

    #menu li a:active {
      border: 1px solid #000;
    }

--------------------------------------------------------------------------------

# À vous : Ajouter un menu vertical à votre mise en page précédente

--------------------------------------------------------------------------------

# Créer un menu horizontal

--------------------------------------------------------------------------------

# Créer un menu horizontal

Pour garder la même structure HTML logique et afficher un menu horizontalement,
il faut utiliser une nouvelle valeur de la propriété ``display`` : ``inline-block``.

## Retour de la propriété ``display``

La valeur ``inline-block`` permet de placer des éléments ayant les propriétés
des éléments blocks (dimensionnables largeur, hauteur, marges, ...) côte à côte.

    !css
    div {
      display: inline-block;
    }

--------------------------------------------------------------------------------

# Menu horizontal : Adaptations de la balise ``<li>``

## Exemple

    !html
    <ul id="menu-horizontal">
      <li><a href="..." title="aller à la page 1">Page 1</a></li>
      <li><a href="..." title="aller à la page 2">Page 2</a></li>
      <li><a href="..." title="aller à la page 3">Page 3</a></li>
      <li><a href="..." title="aller à la page 4">Page 4</a></li>
    </ul>

Pour les menus, elle va permettre de rendre adjacents et sur la même ligne
les éléments ``<li>``.

    !css
    #menu-horizontal li {
      display: inline-block;
    }

--------------------------------------------------------------------------------

# À vous : Ajouter un menu horizontal à votre mise en page précédente

--------------------------------------------------------------------------------

# Menu déroulant

Pour réaliser un menu déroulant, la structure HTML évolue sous la forme de listes
imbriquées

## Exemple

    !html
    <ul id="menu-rolling">
      <li>
        <a href="#">Section A</a>
        <li><a href="..." title="aller à la page 1">Page 1</a></li>
        <li><a href="..." title="aller à la page 2">Page 2</a></li>
        <li><a href="..." title="aller à la page 3">Page 3</a></li>
      </li>
      <li>
        <a href="#">Section B</a>
        <li><a href="..." title="aller à la page 4">Page 4</a></li>
        <li><a href="..." title="aller à la page 5">Page 5</a></li>
        <li><a href="..." title="aller à la page 6">Page 6</a></li>
      </li>
    </ul>

--------------------------------------------------------------------------------

# Utilisation du sélecteur d'enfant

Pour créer un menu déroulant en CSS, il faut pouvoir agir différemment sur
la liste principale et les listes imbriquées.

Par exemple: il faut que les ``<li>`` de premier niveau soient ``inline-block`` (adjacents)
alors que ceux de second niveau doivent être ``block`` (les uns en dessous des autres).

On utilise pour cela le **sélecteur d'enfant** qui permet de sélectionner les éléments du niveau
directement inférieur, sans descendre plus loin dans l'arborescence.

## Exemple

* ``#menu-rolling li`` : agit sur tous les ``<li>`` présents dans ``#menu-rolling`` (ceux du menu principal et ceux des sous-menus)
* ``#menu-rolling > li`` : agit seulement sur les ``<li>`` du menu principal
* ``#menu-rolling ul > li`` : agit seulement sur les ``<li>`` des sous-menus


--------------------------------------------------------------------------------

# Montrer/Cacher les sous-menus

Pour cacher les sous-menus, on utilise une astuce
CSS qui consiste à mettre la hauteur de la liste à 0 et à s'assurer que le contenu
qui dépasse soit bien caché avec les directives ``max-height`` et ``overflow``.

    !css
    #menu-rolling ul {
      max-height: 0;
      overflow: hidden;
    }

Pour montrer le sous-menu correspondant, on utilise la pseudo classe ``:hover``
sur la balise ``<li>`` et on corrige la hauteur fixée à 0 avec une valeur largement
importante.

    !css
    #menu-rolling li:hover ul {
      max-height: 15em;
    }

--------------------------------------------------------------------------------

# Faire en sorte que les sous-menus passent au dessus du contenu

Quand un sous-menu s'affiche, il ne faut pas que le reste de la page se décale vers le bas.
Pour cela, on utilise la propriété ``position`` avec la valeur ``absolute`` qui permet de **sortir un élément du flux** et de le **positionner manuellement**.

    !css
    #menu-rolling ul {
      position: absolute;
      top: 0;
      left: 0;
    }

Quand un élément est positionné en ``absolute``, il se positionne par rapport
à son premier parent positionné en ``relative``, ou par rapport à ``<body>`` en dernier recours. Ici, il faut que les balises ``<li>`` du menu principal soient positionnés en 
``relative`` pour que chaque sous-menu se place correctement par rapport à son élément
de menu principal.

    !css
    #menu-rolling > li {
      position: relative;
    }

--------------------------------------------------------------------------------

# À vous : Faire évoluer le menu horizontal en menu déroulant
