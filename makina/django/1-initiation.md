# todoproject à Django

--------------------------------------------------------------------------------

> La Plateforme de développement Web pour les perfectionnistes sous pression.

<cite> — www.django-fr.org</cite>

.fx: quoteslide

--------------------------------------------------------------------------------

# Qu'est-ce-que Django

* Django est un framework en Python pour le Web qui encourage le développement rapide et propre avec une conception pragmatique
* Django permet de construite des applications web rapidement et avec peu de code
* Malgré son haut niveau d'abstraction, il est toujours possible de descendre dans les couches

## Historique

* Créé en 2003, basé sur le langage Python créé en 1990
* Rendu Open Source (BSD) en 2005
* Version actuelle : Django 1.6, sortie en novembre 2013
* Aujourd'hui utilisé par de très nombreuses entreprises : Mozilla, Instagram, Pinterest, Disqus, ...

--------------------------------------------------------------------------------

# Philosophie

## KISS (*Keep It Simple, Stupid*)

> Simplicity should be a key goal in design and unnecessary complexity should be avoided.

## DRY (*Don't Repeat Yourself*)

> Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.

## Conventions de codage

La documentation précise certaines conventions de codage spécifiques à Django. La PEP 8 fait référence pour le reste.

--------------------------------------------------------------------------------

# 10 raisons d'utiliser Django

* Facile à installer
* Fonction *out of the box*
* Excellente documentation
* Modèles en Python et ORM efficace (peu de connaissances SQL requises)
* Interface d'administration auto-générée
* Architecture *pluggable*, nombreux modules existants
* Gestion de formulaires
* Serveur de développement *standalone*
* Déploiement facile
* Excellente communauté autour du projet

--------------------------------------------------------------------------------

# Environnement

* Django 1.6
* Python : 2.6 / 2.7 / 3.2 / 3.3
* Base de données : SQLite, PostgreSQL, MySQL
* Il est préférable de travailler dans un *virtualenv*

--------------------------------------------------------------------------------

# Architecture MVC, ou plutôt MTV

L'architecture de Django s'inspire du principe MVC (*Model, View, Controller*) ou plutôt MTV (*Model, Template, View*) :

* **Model** : Les modèles sont écrits en Python et Django fournit un ORM (*Django ORM*) complet pour accéder à la base de données
* **Template** : Django possède son propre moteur de template (*Django Template Engine*)
* **View** : Les vues Django peuvent être de simples fonctions Python retournant des réponses HTTP ou être basées sur des classes

La fonction **controller** est gérée par l'*URL dispatcher* qui permet de faire correspondre des URLs sous forme d'expressions régulières à des vues.

--------------------------------------------------------------------------------

# Tutoriel fil rouge : une gestion de *Todo lists*

--------------------------------------------------------------------------------

# Installer Django

## Création et activation du *virtualenv*

    !console
    $ virtualenv --no-site-packages venv_todoproject
    $ source venv_todoproject/bin/activate

## Installation de Django

    !console
    $ pip install django==1.6

## Création du projet

    !console
    $ django-admin.py startproject todoproject

## Lancement du serveur de développement

    !console
    $ cd todoproject
    $ ./manage.py runserver

--------------------------------------------------------------------------------

# It worked !

![Page d'accueil par défaut Django](./it-worked.png)

.fx: imageslide

--------------------------------------------------------------------------------

# Le projet créé

    !console
    ├── todoproject
    │   ├── manage.py
    │   └── todoproject
    │       ├── __init__.py
    │       ├── settings.py
    │       ├── urls.py
    │       └── wsgi.py

* ``/todoproject`` : conteneur du projet (le nom est sans importance)
* ``/manage.py`` : utilitaire en ligne de commande permettant différentes action sur le projet
* ``/todoproject/todoproject`` : paquet Python effectif du projet
* ``/todoproject/settings.py`` : réglages et configuration du projet
* ``/todoproject/urls.py`` : déclaration des URLs du projet
* ``/todoproject/wsgi.py`` : point d'entrée pour déployer du projet avec WSGI

--------------------------------------------------------------------------------

# Accès à la base de données
Django propose une configuration par défaut pour une base SQLite (cf : ``settings.py``).

Voici un exemple de configuration pour une base Postgresql :

    !python
    DATABASES = {
      'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'todoproject_db',
        'USER': 'todoproject_user',
        'PASSWORD': 'Cx12%a03oa',
        'HOST': 'localhost'
      }
    }

## Création de la base de données

    !console
    $ ./manage.py syncdb

--------------------------------------------------------------------------------

# Projet vs. Application

Il est important de différencier la notion de **projet** et d'**application**.

## Une application

> Une application est une application Web qui fait quelque chose – par exemple un système de blog, une base de données publique ou une application de sondage

## Un projet

> Un projet est un ensemble de réglages et d’applications pour un site Web particulier.

## Projets et applications

> Un projet peut contenir plusieurs applications. Une application peut apparaître dans plusieurs projets.

<cite> — docs.djangoproject.com</cite>

--------------------------------------------------------------------------------

# Création d'une application

    !console
    $ ./manage.py startapp todo

## L'application créée

    !console
     ├── todo
     │   ├── admin.py
     │   ├── __init__.py
     │   ├── models.py
     │   ├── tests.py
     │   └── views.py

* ``models.py`` : déclaration des modèles de l'application
* ``views.py`` : écriture des vues de l'application
* ``admin.py`` : comportement de l'application dans l'interface d'administration
* ``tests.py`` : Il. Faut. Tester.

--------------------------------------------------------------------------------

# Les modèles

--------------------------------------------------------------------------------

# Déclaration d'un modèle

    !python
    # models.py
    from django.db import models

    class Task(models.Model):
        name = models.CharField(max_length=100)
        deadline = models.DateField(blank=True, null=True)
        done = models.BooleanField(default=False)

        def __unicode__(self):
            return self.name

--------------------------------------------------------------------------------

# Quelques options pour les modèles

L'ajout de la classe``Meta`` dans un modèle permet de déclarer des *options de métadonnées* sur le modèle. Exemple :

    !python
    class Meta:
        db_table = 'task'
        verbose_name = 'Task'
        verbose_name_plural = 'Tasks'
        ordering = ('-deadline', )

D'autres options permettent par exemple de :

* rendre le modèle abstrait
* demander à Django de ne pas gérer ce modèle en base de données
* de préciser des critères de tri
* de déclarer des permissions relatives au modèle
* ...

--------------------------------------------------------------------------------

# Quelques options pour les champs

Chaque type de champ possède ces propres propriétés. Cependant, certaines sont communes et souvent utilisées comme : 

* ``verbose_name``: label du champ
* ``null`` : valeur NULL autorisée ou non en base de données
* ``blank`` : valeur vide autorisée ou non en base de données
* ``default`` : valeur par défaut pour une nouvelle instance
* ``editable`` : le champ doit-il apparaître automatiquement dans les formulaires
* ...

--------------------------------------------------------------------------------

# Activation de l'application

## Déclaration de l'application dans les *settings*

    !python
    # settings.py
    INSTALLED_APPS = (
      'django.contrib.admin',
      ...
      'todo',
    )

## Création de la table en base de données

    !console
    $ ./manage.py syncdb

## Déclaration dans l'interface d'administration

    !python
    # admin.py
    from django.contrib import admin
    from todo.models import Task

    admin.site.register(Task)

--------------------------------------------------------------------------------

# L'interface d'administration Django

![L'interface d'administration Django](./admin.png)

.fx: imageslide

--------------------------------------------------------------------------------

# Une première vue : la liste des tâches

--------------------------------------------------------------------------------

# 1. Création de la vue

    !python
    # views.py
    from django.views.generic import ListView
    from todo.models import Task

    class TasKView(ListView):
        model = Task

--------------------------------------------------------------------------------

# 2. Création d'une template

    !html
    {# todo/templates/todo/task_list.html #}
    <h1>Liste des tâches</h1>
    <ul>
      {% for task in tasks %}
        <li>{{ task }}</li>
      {% endfor %}
    </ul>
    {% if not tasks %}
      <p>Aucune tâche !</p>
    {% endif %}


--------------------------------------------------------------------------------

# 3. Mapping de l'URL

## Création d'une URL

    !python
    # todo/urls.py
    from django.conf.urls import patterns, include, url
    from todo.views import TaskView
    urlpatterns = patterns('',
        url(r'^task_list$', TaskView.as_view(), name='task_list'),
    )

## Inclusion des URLs de l'application au projet

    !python
    # todoproject/urls.py
    ...
    urlpatterns = patterns('',
        ...
        url(r'^todo/', include('todo.urls')),
    )
    
--------------------------------------------------------------------------------

# Les vues

--------------------------------------------------------------------------------

# Function-based views

Une vue *basée sur une fonction* Django est simplement une fonction Python qui prend en entrée une **requête HTTP** et retourne une **réponse HTTP**.

Cette réponse peut être une page HTML, un document XML, une redirection, une erreur 404, ...

Ces vues doivent être écrites dans le fichier ``views.py`` de l'application.

## Un exemple tiré de la documention de Django

    !python
    # some_app/views.py
    from django.http import HttpResponse
    import datetime

    def current_datetime(request):
        now = datetime.datetime.now()
        html = "<html><body>It is now %s.</body></html>" % now
        return HttpResponse(html)

--------------------------------------------------------------------------------

# Class-based views

Une vue *basée sur une classe* Django permet de **structurer le code et le réutiliser** en exploitant notamment l'héritage et les *mixins*.

Django fournit de multiples socles plus ou moins avancés pour construire ce type de vues.

Ces vues doivent aussi être écrites dans le fichier ``views.py`` de l'application.

## Un exemple tiré de la documention de Django

    !python
    # some_app/views.py
    from django.views.generic import TemplateView

    class AboutView(TemplateView):
        template_name = "about.html"

## Les classes fournies par Django

Un excellent site permettant d'avoir un aperçu complet : http://ccbv.co.uk/

--------------------------------------------------------------------------------

# Function-based vs. Class-based views

## Class-based views

Il faut probablement une vue basée sur une classe ... 

* si une des classes de vues génériques fournies par Django s'approche vraiment du besoin
* si la vue peut être créée par héritage d'une autre en surchargeant seulement des attributs
* si la vue à créer peut être réutilisée par héritage et avec peu de modifications par la suite

## Function-based views

Il faut probablement une vue basée sur une fonction ... 

* si une implémentation basée sur une classe semble complexe
* si la vue n'a pas vocation à être réutilisée

--------------------------------------------------------------------------------

# Le moteur de template

--------------------------------------------------------------------------------

# Qu'est-ce qu'une template Django ?

C'est un simple fichier texte qui peut générer n'importe quel format de texte (HTML, XML, CSV, ...).

Une template a accès à des **variables** qui lui auront été passées via un **contexte** par la vue.

--------------------------------------------------------------------------------

# Base de la syntaxe de template

## Affichage d'une variable

    !python
    {{ ma_variable }}

## Les filtres

Il est possible de modifier l'affichage d'une variable en appliquant des **filtres**. Un filtre peut prendre (ou non) un argument. Les filtres peuvent appliqués en cascade. Quelques exemples :

    !python
    {{ name|lower }}
    {{ text|linebreaksbr }}
    {{ current_time|time:"H:i" }}
    {{ weight|floatformat:2|default_if_none:0 }}

Django fournit nativement une liste de filtres assez intéressante et il est possible d'écrire des filtres personnalisés facilement.

--------------------------------------------------------------------------------

## Les tags

Les **tags** sont plus complexes que les variables, ils peuvent créer du texte ou de la logique (boucle, condition, ...) dans la tempate.

### Une condition *if* :

    !python
    {% if condition %} .. {% else %} .. {% endif %}

### Une boucle *for* :

    !python
    {% for item in list %} .. {% endfor %}


### Cache de variable *with* :

    !python
    {% with total=list.count %} {{ total }} {% endwith %}

Django fournit aussi plusieurs tags nativement et il est possible d'écrire ses propres tags.

--------------------------------------------------------------------------------

# L'héritage de template

L'intérêt de l'héritage de template est par exemple de pouvoir créer un squelette HTML contenant tous les éléments communs du site et définir des blocs que les templates *enfants* pourront surcharger.

Dans une template *parent*, la balise ``{% block %}`` permet de définir les blocs surchargeables.

Dans une template *enfant*, la balise ``{% extends %}`` permet de préciser de quelle template celle-ci doit hériter.

--------------------------------------------------------------------------------

# Exemple de template *parent*

    !html
    {# base.html #}
    <html>
      <head>
        <title>
          {% block title %}
            ...
          {% endblock %}
        </title>
        <link href="styles.css" rel="stylesheet" />
      </head>
      <body>
        <header>Entête commune à tout le site</header>
        <section>
          {% block content %}
            ...
          {% endblock %}
        </section>
        <footer>Pied de page commun à tout le site</footer>
      </body>
    </html>

--------------------------------------------------------------------------------

# Exemple de template *enfant*

    !html
    {# todo/templates/todo/task_list.html #}

    {% extends "base.html" %}

    {% block title %}
      Liste des tâches
    {% endblock %}

    {% block content %}
      <ul>
        {% for task in tasks %}
          <li>{{ task }}</li>
        {% endfor %}
      </ul>
      {% if not tasks %}
        <p>Aucune tâche !</p>
      {% endif %}
    {% endblock %}











