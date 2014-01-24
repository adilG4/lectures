# 3 - Créer une mise en page

--------------------------------------------------------------------------------

# Un exemple de mise en page simple

![Un exemple de mise en page simple](./layout1.jpg)

.fx: imageslide

--------------------------------------------------------------------------------

# La propriété CSS float

Rappel : Pour réaliser la mise en page, nous utilisons des balises de type ``display: block``.

## La propriété CSS ``float``

Permet de spécifier si les éléments HTML suivants sont adjacents (et non les uns en dessous les autres)

    !css
    div {
        float: left | right | none;
    }

## Attention

Quand un élément a une propriété ``float``, on dit qu'il *sort du flux*: sa présence
n'est pas prise en compte par les autres éléments.

Pour éviter que l'élément suivant se superspose, il faut lui appliquer une marge.

--------------------------------------------------------------------------------

# La propriété CSS float

    !html
    <div id="image"><img src="chat.jpg" /></div>
    <div id="texte">Bonjour le chat !</div>

<style type="text/css">
.exfloat div {margin: 3px; padding: 3px; border: 1px solid blue;}
.exfloat .image {margin: 3px; padding: 3px; border: 1px solid red;}
.exfloat .image img {display: inline;};
</style>
<div class="exfloat">
  <div class="image"><img src="catcenter.jpg" /></div>
  <div>Bonjour le chat !</div>
</div>

## À noter

* Les deux blocs sont l'un en dessous de l'autre.
* Les deux blocs prennent 100% de la largeur disponible

--------------------------------------------------------------------------------

# La propriété CSS float

    !html
    <div id="image"><img src="chat.jpg" /></div>
    <div id="texte">Bonjour le chat !</div>

&nbsp;

    !css
    #image {float: left;}
    #texte {margin-left: 200px;}

<div class="exfloat">
  <div class="image" style="float: left"><img src="catleft.jpg" /></div>
  <div style="margin-left: 200px;">Bonjour le chat !</div>
</div>
<br style="clear: both" />

## À noter

* Le bloc ``#image`` flotte à gauche ;
* Le bloc ``#texte`` doit avoir une marge à gauche pour ne pas se superposer au bloc ``#image``.

--------------------------------------------------------------------------------

# La propriété CSS float

    !html
    <div id="image"><img src="chat.jpg" /></div>
    <div id="texte">Bonjour le chat !</div>

&nbsp;

    !css
    #image {float: right;}
    #texte {margin-right: 200px;}

<div class="exfloat">
  <div class="image" style="float: right"><img src="catright.jpg" /></div>
  <div style="margin-right: 200px;">Bonjour le chat !</div>
</div>
<br style="clear: both" />


## À noter

* Le bloc ``#image`` flotte à gauche ;
* Le bloc ``#texte`` doit avoir une marge à droite pour ne pas se superposer au bloc ``#image``.

--------------------------------------------------------------------------------

# La propriété CSS clear

Rappel: la propriété ``float`` permet de rendre tous les éléments HTML suivants adjacents.

## La propriété CSS ``clear``

Permet de spécifier les côtés d'un ou des éléments qui ne doivent pas être adjacents.

    !css
    div {
        float: left | right | both | none;
    }

Elle va notamment de mettre fin à l'effet d'une propriété ``float``.


--------------------------------------------------------------------------------

# La propriété CSS ``clear``

    !html
    <div id="image"><img src="chat.jpg" /></div>
    <div class="texte">Bonjour le chat !</div>
    <div class="texte">Comment ça va le chat ?</div>
    <div id="suite">Passons à une discussion plus sérieuse ...</div>

&nbsp;

    !css
    #image {float: left;}
    .texte {margin-left: 200px;}
    #suite {clear: both;}

<div class="exfloat">
  <div class="image" style="float: left"><img src="catleft.jpg" /></div>
  <div style="margin-left: 200px;">Bonjour le chat !</div>
  <div style="margin-left: 200px;">Comment ça va le chat ?</div>
  <div style="clear: both">Passons à une discussion plus sérieuse ...</div>
</div>

--------------------------------------------------------------------------------

# Revenons à notre exemple

![Un exemple de mise en page simple](./layout1.jpg)

.fx: imageslide

--------------------------------------------------------------------------------

# Réalisation de ce premier exemple

## Méthodologie

1. Écrire le code HTML
2. Mettre en place le conteneur global (largeur)
3. Mettre en place l'affichage en deux colonnes pour la partie centrale
4. Dimensionner chaque bloc (largeur, hauteur si besoin)
5. Ajuster les marges

Conseil : Ajouter une bordure sur chaque bloc le temps du développement pour bien visualiser le rendu.

--------------------------------------------------------------------------------

# 1. Écriture du code HTML

Conseil : Encapsuler le tout dans un conteneur global.


    !html
    <html>
      <head>
        <title>Un premier layout</title>
        <link rel="stylesheet" href="stylesheet.css" />
      </head>
      <body>
        <div id="global">
          <div id="header">HEADER</div>
          <div id="menu">MENU</div>
          <div id="content">CONTENT</div>
          <div id="footer">FOOTER</div>
        </div>  
      </div>

--------------------------------------------------------------------------------

# 2. Mise en place du conteneur global 

    !css
    #global {
      width: 1000px;
      margin: 0 auto 0 auto; 
    }

Note : Grâce aux marges gauche et droite en ``auto``, le conteneur global sera centré dans la fenêtre du navigateur.

--------------------------------------------------------------------------------

# 3. Mise en place de l'affichage en deux colonnes

    !css
    #menu {
      float: left;
      width: 300px; 
    }
    #content {
      margin-left: 310px;
    }
    #footer {
      clear: both;
    }


--------------------------------------------------------------------------------

# 4. Dimensionnement des différents blocs

    !css
    #header {
      height: 100px; 
    }
    #menu {
      height: 400px;
    }
    #footer {
      height: 100px;
    }

Note : On ne précise pas les largeurs de ``#header`` et ``#footer`` car ils prendront automatiquement toute la largeur disponible.

--------------------------------------------------------------------------------

# 5. Ajustement des marges

    !css
    #header {
      margin-bottom: 10px;
    }
    #footer {
      margin-top: 10px;
    }

--------------------------------------------------------------------------------

# Feuille de styles complète

    !css
    #global {
      width: 1000px; margin: 0 auto 0 auto;
    }
    #header {
      height: 100px; margin-bottom: 10px;
    }
    #menu {
      float: left; width: 300px; height: 400px;
    }
    #content {
      margin-left: 310px; height: 400px;
    }
    #footer {
      clear: both; height: 100px;
    }

--------------------------------------------------------------------------------

# Rendu

<style type="text/css">
#exlayout #global div {
  border: 1px solid white;
}
#exlayout #global {
  width: 600px; margin: 20px auto 0 auto;
}
#exlayout #header {
  height: 75px; margin-bottom: 10px;
}
#exlayout #menu {
  float: left; width: 200px; height: 350px;
}
#exlayout #content {
  margin-left: 210px; height: 350px;
}
#exlayout #footer {
  clear: both; height: 75px; margin-top: 10px;
}
</style>

<div id="exlayout">
  <div id="global">
    <div id="header">HEADER</div>
    <div id="menu">MENU</div>
    <div id="content">CONTENT</div>
    <div id="footer">FOOTER</div>
  </div>  
</div>

--------------------------------------------------------------------------------

# TP : À vous !

![Une mise en page 3 colonnes](./layout2.jpg)

.fx: imageslide

--------------------------------------------------------------------------------

# Mise en page fixe VS. Mise en page fluide

--------------------------------------------------------------------------------

## Mise en page fixe

Pour la première version de notre mise en page, nous avons dimensionné blocs et marges en **pixels**. Le résultat est une mise en page dite **fixe**, c'est à dire que la largeur ne s'adapte pas en fonction de la taille de la fenêtre.

## Mise en page fluide

En dimensionnant les largeurs de blocs et de marges en **pourcentages**, la mise en page sera **fluide**, elle s'adaptera à la largeur de la fenêtre. 

## Pixels vs. poucentages

Utiliser une combinaison de pixels et de pourcentages est fortement déconseillé. Exemples de ce qu'il ne faut pas faire :

* largeurs de blocs en pixels et marges en pourcentages ;
* largeurs des barres latérales en pourcentages et largeur du contenu central en pixels.

--------------------------------------------------------------------------------

# TP : À vous !

![Une mise en page 3 colonnes](./layout2.jpg)

.fx: imageslide
