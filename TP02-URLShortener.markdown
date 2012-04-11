Play! Framework
========================

L'objectif de ce TP est de coder une application de type URL shortener en utilisant le framework Play!

Les use cases
------------------------

* http://localhost:9000/ : affiche la page principale de l'application. Cette page est consituée d'un formulaire simple demandant l'URL à raccourcir ainsi que d'une zone dans laquelle sera affichée l'URL raccourcie correspondante.

* http://localhost:9000/url : URL accessible en POST, permet d'ajouter une nouvelle URL raccourcie à l'application. Attention si l'url existe déjà, il faudra renvoyer l'url raccourcie correspondante

* http://localhost:9000/{id} : pattern d'url raccourcie. Redirige la requête courante vers l'url initiale représentée par l'id présent en fin d'url. Utilisez httpServletResponse.sendRedirect("monURLDeDepart");

* http://localhost:8080/url : affiche une vue contenant la liste de toutes les urls raccourcies en base ainsi que leur correspondance. Un lien sera mis à disposition sur chaque url pour l'effacer. Un lien pour l'effacement global sera également fournit

* http://localhost:8080/url/delete : efface toutes les urls en base

* http://localhost:8080/url/{id}/delete : efface une url donnée

Composition de l'application
----------------------------

* 2 vues sous forme de fichiers html, respectivement pour la page d'index et la page listant toutes les URLs
* 1 entité JPA représentant les urls raccourcies. Cette entité est très simple, elle comporte simplement un champ pour l'url de départ et un id représentant la version raccourcie
* 1 contrôleur Play contenant les diverses méthodes executant la logique métier de l'application.

Guide de survie
------------------

installation de Play! Framework :

http://www.playframework.org/documentation/1.2.4/install

configuration de l'IDE : 

http://www.playframework.org/documentation/1.2.4/ide

utilisation de la ligne de commande :

http://www.playframework.org/documentation/1.2.4/cheatsheet/commandLine

utilisation des contrôleurs :

http://www.playframework.org/documentation/1.2.4/cheatsheet/controllers

utilisation des templates :

http://www.playframework.org/documentation/1.2.4/cheatsheet/templates

http://www.playframework.org/documentation/1.2.4/index : section built-in tags

utilisation des modèles :

http://www.playframework.org/documentation/1.2.4/cheatsheet/model

documentation complète : 

http://www.playframework.org/documentation/1.2.4/home



