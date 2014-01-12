Introduction au langage HTML
==============================================================

--------------------------------------------------------------------------------

Introduction
=============

Le langage HTML (*Hypertext Markup Language*) est un langage **de balisage** qui
permet de représenter le contenu de pages web. Il permet, principalement :

* de définir la structure sémantique du contenu
* de le mettre en forme
* de créer des liens (*hyperliens*) entre les pages

Il permet aussi :

* l'intégration de ressources multimedia
* la génération de formulaires web
* ...

Il est interprété **côté client** par le **navigateur web**.

--------------------------------------------------------------------------------

Historique
=============

Le langage HTML a été créé coinjointement au protocole HTTP pour créer le World 
Wide Web en 1989.

* 1995/1996 : Version 2.0
* 1997 : Version 3.2 et 4.0
* 2000 : XHTML (*Extensible Hypertext Markup Language*)
* 2007 : HTML 5 !

Standardisation
----------------

Le langage HTML est un **standard**: Le W3C (World Wide Web Consortium) établit 
une liste de spécifications mais en aucun cas l'implémentation du langage.

Il est à la charge des constructeurs de navigateurs web de suivre ses
recommandations.

--------------------------------------------------------------------------------

Structure d'une page HTML
==========================

    .. html

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
    <HTML>
        <HEAD>
            <TITLE>Titre de la page</TITLE>
        </HEAD>

        <BODY>
            Contenu de la page
        </BODY>
    </HTML>

--------------------------------------------------------------------------------

Les balises HTML
=================

Une balise HTML est un identifiant textuel délimité par les deux caractères
"<" et ">".

Il existe deux types de balises :

* Les balises "en paires"
* Les balises "orphelines"

--------------------------------------------------------------------------------

Les balises "en paires"
========================

Elle fonctionnent par deux : une **balise ouvrante* et une **balise fermante**.
La balise fermante se distingue par l'ajout du caractère "/".

Une balise de ce type agit sur le texte qu'elle encadre.

Exemples:

* <h1> CE TEXTE EST UN TITRE </h1>
* <b> **Ce texte est en gras** </b>
* <p> Ce texte est un paragraphe </p>

Imbrication de balises
-----------------------

Les balises HTML s'imbriquent. Exemple :

* <p> Du texte <b> **en gras** </b> dans un paragraphe. </p>

--------------------------------------------------------------------------------

Les balises "orphelines"
=========================

Les balises dites "orphlines" fonctionnent seules, elles sont utilisées pour
insérer un élément à endroit précis.

Pour les différencier d'une balise ouvrante, on ajouter le caractère "/" juste avant le ">".

Exemples :

* <br /> : saut de ligne
* <hr /> : séparation horizontale
* <img /> : insertion d'une image
* <input /> : champ de formulaire

--------------------------------------------------------------------------------

Les attributs de balises
=========================

Les **attributs** permettent de donner des informations supplémentaires sur une balise.
Il se placent à dans la déclaration de la balise, comme ceci :
``<balise attribut1="valeur1" attribut2="valeur2" />``

Certains attributs peuvent être placé sur n'importe quelle balise. Ex:

* ``id`` : identifiant unique de la balise

..
    
    ``<p id="introduction">Bienvenue au cours sur HTML</p>``
    

D'autres sont spécifiques à un type de balise. Ex :

* ``src`` : adresse de l'image à insérer pour une balises <img />

..
    
    ``<img src="/images/image.jpeg" />``

* ``href``: destination du lien pour une balises <a>...</a>

..

    ``<a href="http://www.google.fr">Lien vers Google</a>``
