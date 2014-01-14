# Les tableaux

--------------------------------------------------------------------------------

# Introduction

L'objectif des tableaux est de présenter des *données tabulaires* structurées en lignes et colonnes, comme dans un tableur tel qu'OpenOffice Calc ou Microsoft Excel.

# Les balises relatives aux tableaux

* ``<table>`` : Définit un tableau
* ``<caption>`` : Encadre le titre du tableau
* ``<tr>`` : Crée une nouvelle ligne dans un tableau (tr = *table row*)
* ``<th>`` : Crée une cellule d'entête dans une ligne de tableau (th = *table header*)
* ``<td>`` : Crée une cellule classique dans une ligne de tableau (td = *table data*)

--------------------------------------------------------------------------------

# Exemple

    !html
    <table>
      <caption>Communes de la métropole nantaise</caption>
      <tr>
        <th>Commune</th>
        <th>Code postal</th>
        <th>Population (2009)</th>
      </tr>
      <tr>
        <td>Nantes</td>
        <td>44000</td>
        <td>282 047</td>
      </tr>
      <tr>
        <th>Carquefou</th>
        <td>44470</td>
        <td>17 772</td>
      </tr>
    </table>

--------------------------------------------------------------------------------

## Un peu de CSS pour la mise en forme

    !css
    caption {
        font-style: italic;
    }
    td, th {
        border: 1px solid white;
        padding: 2px;
    }

## Rendu

<style type="text/css">
#extable { width: 80%; margin: 3px auto;}
#extable caption {font-style: italic;}
#extable td, #extable th { border: 1px solid white; padding: 2px;}
</style>

<table id="extable">
  <caption>Liste des communes de la métropole nantaise</caption>
  <tr>
    <th>Commune</th>
    <th>Code postal</th>
    <th>Population (2009)</th>
  </tr>
  <tr>
    <td>Nantes</td>
    <td>44000</td>
    <td>282 047</td>
  </tr>
  <tr>
    <td>Carquefou</td>
    <td>44470</td>
    <td>17 772</td>
  </tr>
</table>

