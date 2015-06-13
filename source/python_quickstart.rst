======================
Introduction à Python
======================

Commençons par lancer l'interpréteur Python que nous avons installé lors du chapitre précédant:


.. code-block:: sh

    (workshops) ~$ python
    Python 3.4.0 (...)
    Type "copyright", "credits" or "license" for more information.

    >>>


Avant d'entrer ``python``, nous entrions nos commandes sur la ligne de commande
du système d'exploitation.

L'invite de ligne de commande (aussi appelée "prompt") était ``~$``. Une fois
la commande ``python`` entrée, l'invite de commande a changé et est désormais
``>>>``. Cela signifie qu'à partir de maintenant, nous devons uniquement utiliser
des commandes du langage Python.

Les commandes telles que ``cd`` ou ``mkdir`` ne fonctionneront pas. Il est
temps d'apprendre un nouveau langage !

Nous ne taperons pas les signes ``>>>`` (de la même manière que pour ``~$``),
l'interpréteur python le fera pour nous.

Commençons par additionner deux nombres:

    >>> 2 + 2
    4

Python est une super calculatrice:

    >>> 6 * 7
    42
    >>> 1252 - 38 * 6
    1024
    >>> (3 - 5) * 7
    -14
    >>> 21 / 7
    3.0
    >>> 3**2
    9
    >>> 5 / 2
    2.5

Faites bien attention lorsque vous entrez des nombres à virgules, utilisez des
points comme séparateurs, et non pas des virgules. Les virgules nous seront
utiles plus tard, pour définir des :ref:`tuple <lien-tuples>`, mais nous
y reviendrons.


Le temps des présentations
==========================

Chaînes de caractères (Strings)
-------------------------------

Les nombres ne sont pas suffisants pour communiquer de manière efficace, nous
avons donc besoin d'utiliser des chaînes de caractères (aussi appelées
``strings``).

Voici quelques exemples:

    >>> "Bonjour tout le monde"
    'Bonjour tout le monde'
    >>> 'Foo Bar'
    'Foo Bar'
    >>> "Rock 'n' Roll"
    "Rock 'n' Roll"
    >>> 'Mon nom est "Camille"'
    'Mon nom est "Camille"'

Vous pouvez également ajouter (on dit également concaténer) deux chaînes l'une
à l'autre:

    >>> 'Mon nom est ' + '"Camille"'
    'Mon nom est "Camille"'

Ou elles peuvent être aussi multipliés par des nombres:

    >>> 'oui ' * 3
    'oui oui oui '

Une chaîne de caractères doit toujours commencer et se terminer par le même
caractère. Il peut s'agir d'un guillemet simple (``'``), ou d'un guillemet
double (``"``). Cela n'a aucun effet sur la valeur de la chaîne de caractères.
Par exemple, si nous entrons ``"Batman"``, nous créons une chaîne de caractères
``Batman``, les guillemets ne font pas partie de la chaîne de caractères, ils
sont là uniquement pour indiquer qu'il s'agit d'une chaîne de caractères
(string) (malheureusement, Python n'est pas suffisamment brillant pour se
rendre compte de ça lui-même).


Afficher les chaînes de caractères
----------------------------------

Mais, comment afficher ces chaînes de caractères d'une manière lisible ? Il est
possible de le faire en utilisant la fonction :func:`print`.


    >>> print("Bonjour tout le monde !")
    Bonjour tout le monde !

Il est aussi possible d'afficher différentes chaînes de caractères sur une même
ligne, sans avoir à les ajouter l'une à l'autre. Elles seront séparées par des
espaces:

    >>> print("Bonjour, mon nom est", "Camille")
    Bonjour, mon nom est Camille

La fonction :func:`print` peut être utilisée de différentes manières,
puisqu'elle peut écrire à peu près n'importe quoi. Pour l'instant, le seul
type de valeurs que nous connaissons sont les nombres:

    >>> print(1)
    1
    >>> print(1, 2, 3)
    1 2 3
    >>> print("2 + 2 =", 2 + 2)
    2 + 2 = 4

Et voilà, nous avons terminé d'utiliser la console interactive de Python pour
l'instant. Pour sortir, entrez `quit()`::

    >>> quit()

Ou tapez ``Ctrl+D`` pour Linux ou ``Ctrl+Z`` pour Windows.


Fichiers de code source Python
==============================

Jusqu'à présent nous avons exécuté du code dans l'invite de commande
interactive dans laquelle nous récupérons une réponse immédiate à nos
commandes. C'est un bon moyen d'apprendre et d'expérimenter les
éléments du langage. C'est pourquoi on y retourne.

Notre premier programme pourrait ressembler à ça::

    print("Hi, my name is Lucas")


Enregistrez ce programme dans un fichier appelé ``visitingcard.py``,
et lancez-le depuis l'invite de commande ``python visitingcard.py``:

.. code-block:: sh

    (workshops) ~$ python visitingcard.py
    Hi, my name is Lucas
    (workshops) ~$

Un même programme peut contenir plusieurs commandes, chacune devant
être sur une ligne séparée, par exemple::

    print("Hi,")
    print()

    print("my name is Lucas")

    print()
    print("Bye.")

Nous pouvons ajouter des lignes vides où nous le souhaitons dans le
fichier ``visitingcard.py`` pour améliorer la lisibilité. Ici, nous
avons séparé l'entête du message d'avec son contenu et d'avec sa fin.


Envoyer du Morse grâce à Python
===============================

Essayons de créer un programme simple permettant d'envoyer des signaux en
Morse.

En cas d'urgence et de panique liée à cet ordinateur, vous pouvez avoir besoin
d'envoyer un signal de détresse.

Le signal de détresse, SOS (Save Our Soul) est en effet le signal le plus connu
pour communiquer sa situation critique par la lumière ou par le son.
Il est utilisé par les bateaux et par les naufragé•e•s en situation de
détresse.
Nous allons pour notre part commencer à afficher des signaux morse depuis
le terminal. En commencant par notre fameux signal de détresse SOS.

Pour écrire un SOS en morse :

S.O.S va se traduire en morse par (... --- ...) soit 3 signaux courts suivis de
3 signaux longs.
Le S est donc égal à "..." et le O à "---"

Nous connaissons déjà la fonction :func:`print` (pour afficher des choses).
Nous allons donc créer un '''programme''' qui stocke les deux lettres et leur
équivalent en morse dans des '''variables'''.

Pour commencer, créez un fichier ``morse.py`` puis écrivez à l'intérieur le
programme suivant :

.. testcode::

    print("...---...")

Lancez votre programme comme ceci::

    $ python morse.py

Vous obtenez:

.. testoutput::

    ...---...

Comme vous le voyez notre programme a besoin de quelques améliorations:

Si quelqu'un souhaite envoyer un autre message que "SOS", nous devons modifier
le fichier ``morse.py``.

Programmer c'est l'art de résoudre les problèmes, alors mettons nous au travail !
Cela va nous donner l'occasion d'apprendre de nouvelles fonctionnalités de Python.

Variables
=========

Pour commencer nous aimerions bien rendre notre programme plus lisible, pour
permettre au lecteur de savoir immédiatement quel code morse correspond à
quelle lettre (``...`` correspond à "S" et ``---`` correspond à "O").

C'est pourquoi nous donnons des noms à ces valeurs:

.. testcode::

    s = "..."
    o = "---"
    print(s + o + s)

Le résultat n'a pas changé:

.. testoutput::

    ...---...

.. note:: Ici on utilise l'opérateur ``+`` qui sert à concaténer (coller) deux
    chaines de caractères entre elles. Tapez par exemple dans votre console
    Python::

        >>> "Bonjour" + " a tous et a toutes"
        'Bonjour a tous et a toutes'

Pour mieux comprendre le fonctionnement des variables, revenons à l'invité
de commande (aussi nommée "console") Python et essayons d'en créer
quelques-unes :

    >>> x = 42
    >>> PI = 3.1415
    >>> name = "Amelia"
    >>> print("Quelques valeurs:", x, PI, name)
    Quelques valeurs: 42 3.1415 Amelia

Une variable peut être vue comme une boite portant une étiquette :
    * Elle contient quelque chose (on dit que la variable contient une
        ``valeur``)
    * Elle a un nom (comme l'inscription sur l'étiquette de la boite)

Deux variables (ayant des noms différent) peuvent contenir la même valeur :

    >>> y = x
    >>> print(x, y)
    42 42

Ici les deux variables ont pour noms ``y`` et ``x`` (se sont les étiquettes sur
les boites) et elles contiennent la même valeur : ``42``

On peut également modifier la valeur d'une variable (changer le contenu de la
boite). La nouvelle valeur n'a pas besoin d'être du même type
(nombre entier, nombre décimal, texte ...) que la précédente :

    >>> x = 13
    >>> print(x)
    13
    >>> x = "Scarab"
    >>> print(x)
    Scarab

Les variables sont indépendantes les unes des autres. Si on modifie la
valeur de x, la valeur de y reste la même :

    >>> print(y)
    42

Nous pouvons également mettre le résultat de calculs ou d'opérations dans des
variables et utiliser ensuite ces variables comme alias de la valeur dans
d'autres calculs.

    >>> s = "..."
    >>> o = "---"
    >>> aidez_moi = s + o + s
    >>> print(aidez_moi)
    ...---...

À noter qu'une fois que la valeur est calculée, elle n'est pas modifiée :

    >>> s = "@"
    >>> print(aidez_moi)
    ...---...

Sauf si on demande à Python de la recalculer :

    >>> aidez_moi = s + o + s
    >>> print(aidez_moi)
    @---@

Il est grand temps d'ajouter quelques commentaires à notre programme
afin de faciliter la compréhension pour les lecteurs-trices (dont nous faisons
parti).

Les commentaires nous permettent de rajouter du texte dans notre code
Python. Les commentaires seront simplement ignorés par l'interpréteur
Python lors de l'exécution du code.

En Python, un commentaire est tout ce qui se trouve entre un caractère
``#`` et la fin de la ligne::

    # Code Morse du "S"
    s = "..."

    # Code Morse du "O"
    o = "---"

    aidez_moi = s + o + s # Code Morse pour "SOS"
    print(aidez_moi)


Les fonctions
=============

Notre programme n'est pas trop mal, mais si l'utilisateur-trice souhaite
pouvoir envoyer plusieurs SOS, ou bien réutiliser ce bout de programme sans
dupliquer trop de lignes, il va falloir empaqueter notre fonctionnalité
dans ce qu'on appelle : une fonction.

Une fonction, c'est un mini moteur, un groupe d'instructions qui prend des
données en entrée, execute les instructions (calcule) en utilisant (ou pas) les
données en entrée et renvoie (ou pas) un résultat en sortie.

En Python on définie une fonction comme suit::

    def nom_de_la_fonction(argument1, argument2):
        # les instructions à executer
        # les instructions peuvent utiliser les arguments
        # pour retourner un résultat il faut utiliser le mot clef "return"
        # Si la fonction ne retourne rien, "return" est optionel
        return 42


Pour executer cette fonction (on dit "appeller" la fonction)::

    nom_de_la_fonction(argument1, argument2)

Pour récupérer la valeur de retour (résultat, sortie) de la fonction dans une
variable::

    ma_variable = nom_de_la_fonction(argument1, argument2)

Notre première fonction va se contenter d'imprimer notre signal de détresse.

On crée donc la fonction et on l'appelle à la fin du fichier::

    def print_sos():
        s = "..."
        o = "---"
        print(s+o+s)

    print_sos()

.. note:: On remarque qu'ici notre fonction ne prend aucun argument et ne
    renvoie aucune valeur (pas de mot clef ``return``).

J'ai maintenant une fonction toute simple que je peux appeler à plusieurs
reprises juste en duplicant l'appelle ``print_sos()``.

On peut aussi vouloir découper le signal et signifier que notre mot est terminé
On va donc ajouter une nouvelle variable "stop" pour découper le mot et ainsi
savoir quand le mot est terminé::

    def print_sos():
        s = "..."
        o = "---"
        stop = "|"
        print (s+o+s+stop)

    print_sos()

On peut encore simplifier notre code en remarquant que ``s`` contient 3 points
et ``o`` contient 3 tirets. Il se trouve qu'on peut dupliquer une chaine de
caractères en utilisant la syntaxe suivante::

    >>> "hello"*2
    'hellohello'

On peut donc obtenir ``"..."`` en faisant ``"." * 3``::

    def print_sos():
        s = "." * 3
        o = "-" * 3
        stop = "|"
        print(s+o+s+stop)

    print_sos()

Si maintenant on veut afficher plusieurs SOS, on peut écrire autant de fois
que nécessaire ``print_sos()`` à la fin du fichier. Mais les informaticien•ne•s
sont flemmard•e•s et la machine est là pour nous éviter de refaire la même
chose et faire le travail répétitif et ennuyeux.

On a besoin de dire à la machine combien de fois on veut imprimer notre SOS.
On va donc modifier la fonction et lui passer le nombre de fois que l'on veut
imprimer le signal SOS en argument::

    def print_sos(nb):
        s = "." * 3
        o = "-" * 3
        stop = "|"
        print((s+o+s+stop) * nb)

    print_sos(3)

Ce qui donne::

    $ python morse.py
    ...---...|...---...|...---...|

Pour qu'on puisse mieux lire les différents SOS et visualiser la fin de la
phrase on va lui ajouter un retour à la ligne (``\n``)::

    def print_sos(nb):
        s = "." * 3
        o = "-" * 3
        stop = "|"
        print((s+o+s+stop+"\n") * nb)

    print_sos(3)

Ce qui donne lorsqu'on execute ``morse.py``::

    $ python3.4 morse.py
    ...---...|
    ...---...|
    ...---...|

On a donc une fonction qui prend en entrée le nombre de fois que l'on veut
emettre le signal SOS. Pour l'instant elle ne se contente que d'afficher.
Si on veut rendre ce programme encore plus facile à utiliser, imaginons par
exemple que nous ayons un robot qui transforme le . et le - en sons différents,
ou une machine qui allume et éteigne une lampe plus ou moins longtemps.
On peut vouloir que cette fonction retourne la chaine de caractère du message
à transmettre sans l'afficher dans le terminal. On pourra ensuite mettre cette
chaine dans une variable et la passer en argument à une autre fonction dont
le rôle sera d'émettre du son ou d'allumer une lampe.
On va donc demander à la fonction de retourner (via ``return``) le message
morse et donc on va changer le nom de la fonction de ``print_sos`` à
``emit_sos``::

    def emit_sos(nb):
        s = "." * 3
        o = "-" * 3
        stop = "|"
        return (s+o+s+stop) * nb

    emit_sos(5)

Cette fois-ci lorsqu'on execute notre programme, plus rien n'est affiché.

Mais rassurez-vous, on peut toujours vérifier que celà marche en modifiant la
dernière ligne en::

    print(emit_sos(5))

En effet, :func:`emit_sos` retourne une chaine de caractère que :func:`print` va
afficher.

On a donc créé une fonction réutilisable, et que l'on peut greffer à d'autre
comme par exemple emettre un son ::

    play(emit_sos(5))

ou encore allumer et éteindre un phare ::

    flash(emit_sos(5))

Mais avant de gérer les phares et cassez les oreilles des autres,
nous allons plutôt interagir avec notre machine à sos et nous familiariser avec elle.

Un peu d'interactivité avec l'utilisateur•trice serait le bienvenu, par exemple
demander à l'utilisateur•trice de rentrer au clavier le nombre de fois qu'il
faut afficher le SOS.

Nous allons utiliser la fonction :func:`input` (fonctionne seulement avec
Python 3, si vous utilisez Python 2 remplacez :func:`input` par
:func:`raw_input`) pour ça.

La fonction :func:`input` laisse l'utilisateur•trice taper un message (terminé
par l'appuie sur la touche Entrée) puis retourne la chaine de caractère
qui a été tapée::

    >>> input()
    Bonjour a toutes et a tous
    'Bonjour a toutes et a tous'

Le résultat peut bien sûr être stoqué dans une variable afin de l'utiliser par
la suite::

    >>> message = input()
    Ceci est un test
    >>> print("Vous avez tape : " + message)
    Vous avez tape : Ceci est un test

Essayons maintenant de l'intégrer à notre machine à SOS::

    def emit_sos(nb):
        s = "." * 3
        o = "-" * 3
        stop = "|"
        return (s+o+s+stop) * nb

    print("Entrez le nombre de SOS que vous voulez: ")
    nb_sos = input()
    print(emit_sos(nb_sos))

Voici ce que le programme donne une fois executé::

    $ python morse.py
    Entrez le nombre de SOS que vous voulez:
    5
    Traceback (most recent call last):
      File "morse.py", line 9, in <module>
        print(emit_sos(nb_sos))
      File "morse.py", line 5, in emit_sos
        return (s+o+s+stop) * nb
    TypeError: can't multiply sequence by non-int of type 'str'

Ceci est une erreur Python (on dit une exception).
L'erreur vient du fait que la fonction :func:`input` retourne une chaine de
caractères et non pas un nombre entier.
En Python, ``"5"`` est différent de ``5``, le premier est une chaine de
caractère et le deuxième est un entier::

    >>> type("5")
    <class 'str'>
    >>> type(5)
    <class 'int'>

.. note:: La fonction :func:`type` permet d'afficher le type d'une expression.

Pour convertir notre chaine de caractères en entier, nous allons utiliser la
fonction :func:`int`::

    >>> a = "5"
    >>> a
    '5'
    >>> int(a)
    5

Voici le code corrigé::

    def emit_sos(nb):
        s = "." * 3
        o = "-" * 3
        stop = "|"
        return (s+o+s+stop) * nb

    print("Entrez le nombre de SOS que vous voulez: ")
    nb_sos = int(input())
    print(emit_sos(nb_sos))

Une fois lancé::

    $ python morse.py
    Entrez le nombre de SOS que vous voulez:
    5
    ...---...|...---...|...---...|...---...|...---...|



Les conditions
==============
En avant vers notre prochaine problématique.
Maintenant on a une machine à émettre des sos autant de fois qu'on le désire.
Mais il faut faire attention, trop de sos pour faire imploser le bateau
ou faire sauter l'élecricité ou encore simplement rendre fou le capitaine.

On va donc prévenir le lanceur de SOS s'il dépasse la limite autorisée.
On va modifier notre fichier morse.py pour ajouter des précautions d'usage::

    def emit_sos(nb):
        s = "." * 3
        o = "-" * 3
        stop = "|"
        return (s+o+s+stop) * nb

    print("Entrez le nombre de SOS que vous voulez: ")

    nb_sos = int(input())
    #Et maintenant nous allons vérifier que l'utilisateur n'abuse pas en nombre de sos
    #si alors
    if nb_sos == 0:
        print("Pas SOS pour toi donc.")
    #ou si alors
    elif nb_sos > 10:
        print("Trop de SOS! Stoppez ca s'il vous plait! Vous allez casser la machine!")
    # sinon alors
    else:
        print(emit_sos(nb_sos))

Maintenant l'utilisateur a peut être VRAIMENT un problème, il faut quand même envoyer un signal.
On va donc quand même envoyer le signal mais en respectant la limite::

    #si alors
    if nb_sos == 0:
        print("Pas SOS pour toi donc.")
    #ou si alors
    elif nb_sos > 10:
        print("Trop de SOS! Stoppez ca s'il vous plait! Vous allez casser la machine!")
        print(emit(10))
    # sinon alors
    else:
        print(emit_sos(nb_sos))

L'utilisateur de la machine à SOS maintenant qu'il est prevenu peu informer de l'urgence de sa situtation
en fonction du nombre de SOS qu'il envoie:

=====================   ==================    ==================
   Nombre de SOS           Type de Signal		Signification
=====================   ==================    ==================
 < 5                    Avarie mineure 	      on rentre au port rapidemment
 5 – 12              	Avarie moyenne 	      patrouille de reconnaissance demandée
 ≥ 12                   Avarie majeure 	      envoi immédiat des forces d'interventions
=====================   ==================    ==================

Exercice : Ecrire une fonction qui va afficher le type de signal en fonction du nombre de SOS envoyé
(n'oubliez pas de prendre en compte s'il n'y a pas de signal)


Conditions : vrai ou faux
-------------------------

La première chose dont nous n'avons pas encore parlé sont les conditions.
Pour les nombres, cela fonctionne exactement comme en mathématiques :

    >>> 2 > 1
    True
    >>> 1 == 2
    False
    >>> 1 == 1.0
    True
    >>> 10 >= 10
    True
    >>> 13 <= 1 + 3
    False
    >>> -1 != 0
    True

Le résultat d'une condition est toujours ``True`` ou ``False``.
On peut utiliser les opérateurs :keyword:`and` et :keyword:`or` pour
construire des conditions plus complexes:

    >>> x = 5
    >>> x < 10
    True
    >>> 2 * x > x
    True
    >>> (x < 10) and (2 * x > x)
    True
    >>> (x != 5) and (x != 4)
    False
    >>> (x != 5) and (x != 4) or (x == 5)
    True


Indentation
-----------

Une deuxième chose à laquelle il faut faire attention en Python, c'est
l'indentation du code.

Ouvrez l'interpreteur Python et entrez une combinaison simple, par
exemple:

    >>> if 2 > 1:
    ...

Pour l'instant rien ne se passe, comme le montrent les points ``...`` à
la place des habituels chevrons ``>>>``. Python s'attend à ce que
nous donnions des instructions complémentaires qui devront être
exécutées si la condition ``2 > 1`` s'avère vraie. Essayons d'afficher
"OK"::

    >>> if 2 > 1:
    ... print("OK")
      File "<stdin>", line 2
        print("OK")
            ^
    IndentationError: expected an indented block

Apparemment, ça n'a pas très bien fonctionné. En fait Python doit
savoir si l'instruction que nous avons entrée est une instruction à
exécuter uniquement si la condition est vraie ou si c'est une
instruction à exécuter sans qu'elle ne soit affectée par la condition.

C'est pourquoi nous devons indenter notre code::

    >>> if 2 > 1:
    ...  print("OK")
    ...
    OK

Tout ce que vous devez faire c'est ajouter un espace ou une tabulation
avant votre instruction pour dire qu'elle fait partie des instructions
dépendantes du :keyword:`if`. Attention, toute les lignes a exécuter
dans le if doivent être indentées de la même manière::

    >>> if -1 < 0:
    ...  print("A")
    ...   print("B")
      File "<stdin>", line 3
        print("B")
        ^
    IndentationError: unexpected indent

    >>> if -1 < 0:
    ...     print("A")
    ...   print("B")
      File "<stdin>", line 3
        print("B")
                ^
    IndentationError: unindent does not match any outer indentation level

    >>> if -1 < 0:
    ...   print("A")
    ...   print("B")
    ...
    A
    B


Pour éviter la confusion, la plupart des développeurs Python se sont
mis d'accord pour toujours utiliser quatre espaces pour chaque niveau
d'identation. Nous allons nous aussi adopter cette convention::

    >>> if 2 > 1:
    ...     if 3 > 2:
    ...         print("OK")
    ...     else:
    ...         print("ECHEC")
    ...     print("FAIT")
    OK
    FAIT


Et si ce n'est pas le cas ?
---------------------------

On pourrait se débrouiller pour écrire un programme en utilisant
uniquement des :keyword:`if` ::

    if nb_sos <= 5:
        print("Avarie Mineure")
    if nb_sos > 5:
        if nb_sos < 12:
            print("Avarie Moyenne")
    if nb_sos >= 12:
        print("Avarie Majeure")

Mais en fait, on peut aussi utiliser :keyword:`else` et
:keyword:`elif`, afin de ne pas avoir à répéter les conditions
similaires et améliorer la lisibilité du code. Dans des programmes
plus compliqués, il n'est parfois pas évident de reconnaître que la
condition lue est la condition inverse de la précédente.

En utilisant :keyword:`else` , nous avons la garantie que les
instructions données seront exécutées seulement si les instructions
données après le :keyword:`if` n'ont pas été exécutées::

    if nb_sos < 5:
        print("Avarie Mineure")
    else:
        # Si votre programme exécute ces instructions alors vous êtes
        # certains que nb_sos >= 5 !
        if nb_sos < 12:
            print("Avarie Moyenne")
        else:
            # Ici vous pouvez être certains que nb_sos >= 25.0
            # nous n'avons donc pas à le vérifier.
            print("Avarie Majeure")

Regardez bien attentivement la manière dont le code est indenté. À
chaque utilisation de :keyword:`else`, un niveau d'indentation a été
ajouté à chaque niveau du code. C'est très ennuyeux d'avoir à lire du
code avec de nombreux niveaux d'indentation.

C'est pourquoi les développeurs Python on ajouté un troisième mot clé,
:keyword:`elif`, qui permet de vérifier directement une autre
condition.

::

    if n < 1:
        # Si n est inférieur à un.
        print("inferieur à un")
    elif n < 2:
        # Si est supérieur ou égal à un, et inférieur à deux.
        print("entre un (compris) et deux")
    elif n < 3:
        # Si n est supérieur ou égal à un,
        # que n est supérieur ou égal à deux,
        # et que n est inférieur à 3
        print("entre deux et trois")
    else:
        # Si aucune des conditions précédentes n'est vérifiée
        print("supérieur ou égal à trois")


.. _lien-tuples:

Tuples
======
Nous savons déjà que nous pouvons concaténer des chaînes de
caractères, les multiplier par des nombres, vous allez voir qu'on peut
aussi les formater. Tout d'abord, nous avons besoin de découvrir un nouveau type de données (en plus des ``strings`` et des nombres, ``int`` et ``float``, que nous connaissons déjà).


Rappelez-vous, je vous disais que nous ne pouvions pas utiliser les virgules dans les nombres car nous en aurions besoin par la suite pour définir les tuples. Nous y voici

    >>> 1, 2, 3
    (1, 2, 3)
    >>> ("Ala", 15)
    ('Ala', 15)
    >>> x = 1,5
    >>> print(x)
    (1, 5)

Un tuple n'est ni plus ni moins qu'une valeur contenant un groupe de
valeurs. Les valeurs que nous souhaitons grouper doivent être séparées
par des virgules. L'ensemble peut-être entouré de parenthèses pour
rendre plus explicite le fait qu'il s'agisse bien d'un groupe, mais ce
n'est pas obligatoire. Sauf pour le cas d'un groupe vide (aussi
bizarre que cela puisse paraître).

    >>> ()
    ()

Il est possible de combiner des tuples:

    >>> names = ("Pauline", "Dupontel")
    >>> details = (27, 1.70)
    >>> names + details
    ('Pauline', 'Dupontel', 27, 1.7)

Un tuple peut aussi contenir un autre tuple, par exemple un point sur
une carte peut-être groupé comme ceci:

    >>> point = ("Pizzeria", (long, lat))

Avec ``long`` et ``lat`` des coordonnées géographiques.

On peut ensuite se référer aux valeurs d'un groupe en utilisant leurs
positions (en commençant à zéro):

    >>> p = (10, 15)
    >>> p[0]  # première valeur
    10
    >>> p[1]  # deuxième valeur
    15



En résumé
=========

Dans ce chapitre nous avons appris les bases de la syntaxe
Python. Nous avons découvert comment afficher des nombres entiers et
décimaux, des chaînes de caractères et nous avons découvert les
tuples.

Nous avons appris à utiliser la fonction :func:`print`, qui affiche
des informations à l'utilisateur et la fonction :func:`input`, qui
permet de lire les entrées de ce dernier.

Nous avons vu comment l'identation pouvait être importante, notamment
lors de l'utilisation des instructions :keyword:`if`, :keyword:`else`
et :keyword:`elif`.

Nous avons réalisé notre premier programme dans un fichier que nous pouvons lancer.

Notre programme pose quelques questions à l'utilisateur, calcule des
informations et présente les résultats dans une forme utile à
l'utilisateur.

Ça fait finalement beaucoup de choses pour un premier programme. Nous
avons encore pas mal de travail mais vous pouvez être fier de ce que
vous avez fait jusqu'à présent !
