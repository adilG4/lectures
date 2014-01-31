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

# Comment styler une liste ?

Todo

--------------------------------------------------------------------------------

# Créer un menu vertical

--------------------------------------------------------------------------------

# Créer un menu horizontal

--------------------------------------------------------------------------------

# Retour de la propriété ``display``

La propriété ``display`` permet de placer des éléments de type ``block`` côte à côte grâce à la valeur ``inline-block``.