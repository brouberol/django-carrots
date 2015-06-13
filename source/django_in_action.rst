=====================
Introduction à Django
=====================


Django, qu'est-ce que c'est ?
=============================

Nous avons jusqu'ici appris des rudiments de Python, mais Python est juste un langage -- accompagné de bibliothèques de code assez basiques -- permettant de créer des programmes. La création d'un site web interactif en Python demande un travail considérable, c'est pourquoi nous allons utiliser Django, qui nous fournit un ensemble d'outils, fonctions (comme celles que nous avons étudiées précédemment, mais plus élaborées) et classes qui facilitent beaucoup la création de sites.

Pour mettre en place un site web pleinement interactif, il nous faut ces quelques éléments :

* Un serveur d'application - ici nous allons utiliser Django.
* Des fichiers HTML et CSS, qui vont décrire l'apparence du site.
* Une base de données pour stocker les questions et réponses à nos sondages.

Commençons par créer le serveur d'application.


Création du projet
==================

Installation
------------

Installez Django en exécutant la commande suivante dans la console : ``pip install django==1.8.2``.

.. code-block:: sh

   (workshops) ~$ pip install django==1.8.2
   Downloading/unpacking django==1.8.2
   Downloading Django-1.8.2-py2.py3-none-any.whl (6.2MB): 6.2MB downloaded
   Installing collected packages: django
   Successfully installed django
   Cleaning up...

Le paquet adéquat est alors téléchargé depuis `PyPI <http://pypi.python.org>`_ - un dépôt centralisé de paquets de code où sont disponibles de nombreuses bibliothèques.


Démarrage du projet
-------------------

Django fournit le script d'administration ``django-admin.py`` qui permet entre autres choses de créer l'arborescence initiale du site. Pour démarrer le nouveau projet, exécutez la commande suivante : ``django-admin.py startproject carrots``

.. code-block:: sh

   # Linux

   (workshops) ~$ django-admin.py startproject carrots
   (workshops) ~$ tree carrots
   carrots/
   ├── carrots
   │   ├── __init__.py
   │   ├── settings.py
   │   ├── urls.py
   │   └── wsgi.py
   └── manage.py

   1 directory, 5 files

.. code-block:: bat

   # Windows

   (workshops) C:\Users\Alex> python -m django-admin startproject carrots
   (workshops) C:\Users\Alex> tree /f carrots
   Folder PATH listing
   Volume serial number is 00FA-07FF
   C:\USERS\ALEX\DOCUMENTS\CARROTS
   │   manage.py
   │
   └───carrots
           settings.py
           urls.py
           wsgi.py
           __init__.py


Structure du projet
-------------------

Le projet que nous venons de créer contient un répertoire ``carrots`` et quelques fichiers de base.

Le fichiers ``carrots/settings.py`` contient des paramètres de configurations tels que le langage, la connexion à la base de données ou encore la liste des applications installées dans le projet. Vous pouvez modifier ce fichier vous-même, il contient un paramétrage par défaut ainsi que des commentaires explicatifs.

Le fichier ``manage.py`` nous permet d'administrer le site web, créer ou effacer la base de données, démarrer un simple serveur d'application, etc... Nous verrons par la suite comment l'utiliser.

Le fichier ``carrots/urls.py`` contient des informations sur les chemins d'accès aux différentes pages du site.

Les autres fichiers présentent moins d'intérêt dans l'immédiat. De manière générale, on n'a pas besoin de les ouvrir ou de les modifier. Si ces fichiers vous intriguent, n'hésitez pas à rechercher sur Internet des informations supplémentaires à leur sujet.


Réglages de l'application
-------------------------

Modifiez ainsi dans le fichier ``carrots/settings.py`` les lignes suivantes pour régler la langue et le fuseau horaire utilisés par l'application ::

   LANGUAGE_CODE = 'fr_fr'

   TIME_ZONE = 'Europe/Paris'

Pour simplifier les choses nous allons désactiver la gestion avancée des fuseaux horaires dans la base de données car nous n'en aurons pas besoin pour ce projet. Localisez le paramètre ``USE_TZ`` et positionnez-le à ``False`` ::

   USE_TZ = False

La section ``INSTALLED_APPS`` contient des informations sur les applications installées. Un projet Django est en effet conposé de plusieurs applications, comme ici l'application ``auth`` qui sert à authentifier les utilisateurs, l'application ``sessions`` qui permet de gérer les sessions des utilisateurs, et ainsi de suite.

Comme vous pouvez le voir, ``INSTALLED_APPS`` est tout simplement un tuple de noms d'applications. En décommentant les deux dernières chaînes de caractères (c'est-à-dire en supprimant le caractère ``#`` en début de ligne), vous pouvez activer l'interface d'administration fournie par Django. Nous allons voir plus tard comment l'utiliser.


Base de données
---------------

Le moment est maintenant venu d'utiliser le fichier ``manage.py`` pour créer la base de données de notre site. Pour ce faire, nous allons utiliser l'option ``migrate``. Lancez donc la commande ``python manage.py migrate`` depuis le répertoire du projet

.. code-block:: sh

    (workshops) ~$ cd carrots
    (workshops) ~/carrots$ python manage.py migrate
    Operations to perform:
      Synchronize unmigrated apps: staticfiles, messages
      Apply all migrations: admin, contenttypes, auth, sessions
    Synchronizing apps without migrations:
      Creating tables...
        Running deferred SQL...
      Installing custom SQL...
    Running migrations:
      Rendering model states... DONE
      Applying contenttypes.0001_initial... OK
      Applying auth.0001_initial... OK
      Applying admin.0001_initial... OK
      Applying contenttypes.0002_remove_content_type_name... OK
      Applying auth.0002_alter_permission_name_max_length... OK
      Applying auth.0003_alter_user_email_max_length... OK
      Applying auth.0004_alter_user_username_opts... OK
      Applying auth.0005_alter_user_last_login_null... OK
      Applying auth.0006_require_contenttypes_0002... OK
      Applying sessions.0001_initial... OK
    (workshops) ~/carrots$ python manage.py createsuperuser
    Username (leave blank to use 'br'): admin
    Email address: admin@admin.com
    Password:
    Password (again):
    Superuser created successfully.


Si tout se passe bien, Django vous demande alors de fournir quelques informations pour créer un compte administrateur pour l'application. Vous pouvez laisser le nom d'utilisateur qui vous est proposé et saisir n'importe quelle adresse email. Retenez bien ces informations, en particulier le nom d'utilisateur et le mot de passe ; elles vous seront nécessaires pour vous connecter à l'interface d'administration. Dans l'exemple décit ci-dessus, le nom d'utilisateur sera ``admin``.

Si vous voulez en apprendre davantage au sujet de ``manage.py``, vous pouvez exécuter la commande ``python manage.py help``.

.. code-block:: sh

    (workshops) ~/carrots$ python manage.py help

 Vous verrez alors la liste de toutes les commandes et options proposées par ``manage.py``. Pour obtenir de l'aide sur l'une de ces commandes, il suffit alors de taper ``python manage.py help``, suivi du nom de la commande en question -- par exemple

.. code-block:: sh

    (workshops) ~/carrots$ python manage.py help migrate


Interface d'administration
--------------------------

Nous pouvons maintenant lancer notre application. Démarrez le serveur en tapant la commande ``python manage.py runserver``

.. code-block:: sh

   (workshops) ~/carrots$ python manage.py runserver
   Validating models...

   0 errors found
   April 19, 2013 - 20:14:37
   Django version 1.8.2, using settings 'carrots.settings'
   Development server is running at http://127.0.0.1:8000/
   Quit the server with CTRL-BREAK.

Notre site web est dès lors disponible à l'adresse http://127.0.0.1:8000/ ou encore http://localhost:8000/.

L'interface d'administration, quant à elle, peut être consultée au chemin ``admin/``, c'est pourquoi nous y accédons par l'adresse http://localhost:8000/admin/.


Créons une nouvelle application pour nos sondages
-------------------------------------------------

Nous avons jusqu'à présent créé un projet appelé ``carrots``. Les projets Django sont divisés en applications qui fournissent chacune des fonctions spécifiques.

Nous voulons publier des sondages sur notre site, nous allons donc créer une application nommée ``polls`` (ce qui signifie ``sondages`` en anglais -- l'anglais étant la langue la plus fréquemment utilisée au sein des projets informatiques).

Depuis l'invite de commandes, tapez ``python manage.py startapp polls``
::

   (workshops) ~/carrots$ python manage.py startapp polls
   (workshops) ~/carrots$ tree .
   .
   ├── carrots
   │   ├── __init__.py
   │   ├── settings.py
   │   ├── urls.py
   │   ├── wsgi.py
   ├── db.sqlite3
   ├── manage.py
   └── polls
       ├── __init__.py
       ├── admin.py
       ├── models.py
       ├── tests.py
       └── views.py

   2 directories, 14 files

Une fois l'application créée, elle doit être activée dans notre projet. Ajoutez-la donc dans la section ``INSTALLED_APPS`` du fichier ``carrots/settings.py``. Vous devriez parvenir à un résultat similaire à celui-ci ::

    INSTALLED_APPS = (
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'polls'
    )

Les applications Django sont constituées de plusieurs fichiers :

* ``admin.py`` - permet de configurer l'interface d'administration,
* ``models.py`` - contient la définition des modèles de la base de données,
* ``tests.py`` - contient l'ensemble des tests permettant de valider le bon fonctionnement de l'application,
* ``views.py`` - contient le code des différentes vues de l'application.


En résumé
---------

Pour installer Django

.. code-block:: sh

   (workshops) ~$ pip install django==1.8.2

Pour créer un projet Django

.. code-block:: sh

   # Linux

   (workshops) ~$ django-admin.py startproject carrots

.. code-block:: bat

   # Windows

   (workshops) C:\Users\TeddyBear> python -m django-admin startproject carrots

Pour régler le langage et le fuseau horaire, dans le fichier ``carrots/settings.py``

.. code-block:: sh

   LANGUAGE_CODE = 'fr_fr'

   TIME_ZONE = 'Europe/Paris'

   USE_TZ = False

Pour créer ou mettre à jour la base de données, il faut lancer cette commande après avoir ajouté un nouveau modèle de données

.. code-block:: sh

   (workshops) ~/carrots$ python manage.py migrate

Pour créer un compte administrateur permettant d'accéder à l'interface d'administration

.. code-block:: sh

   (workshops) ~/carrots$ python manage.py createsuperuser

Pour démarrer le serveur d'application

.. code-block:: sh

   (workshops) ~/carrots$ python manage.py runserver

Pour créer une nouvelle application, par exemple nommée ``polls``

.. code-block:: sh

   (workshops) ~/carrots$ python manage.py startapp polls

N'oubliez alors pas de rajouter cette nouvelle application à la section ``INSTALLED_APPS``!
