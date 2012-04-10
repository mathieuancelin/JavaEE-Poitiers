Servlet & MVC
========================

L'objectif de ce TP est de coder une application de type URL shortener en utilisant les servlets et JSP de Java EE.

Les use cases
------------------------

* http://localhost:8080/app/index : affiche la page principale de l'application. Cette page est consituée d'un formulaire simple demandant l'URL à raccourcir ainsi que d'une zone dans laquelle sera affichée l'URL raccourcie correspondante.

* http://localhost:8080/app/url : URL accessible en POST, permet d'ajouter une nouvelle URL raccourcie à l'application. Attention si l'url existe déjà, il faudra renvoyer l'url raccourcie correspondante

* http://localhost:8080/app/r/{id} : pattern d'url raccourcie. Redirige la requête courante vers l'url initiale représentée par l'id présent en fin d'url. Utilisez httpServletResponse.sendRedirect("monURLDeDepart");

* http://localhost:8080/app/url : affiche une vue contenant la liste de toutes les urls raccourcies en base ainsi que leur correspondance. Un lien sera mis à disposition sur chaque url pour l'effacer. Un lien pour l'effacement global sera également fournit

* http://localhost:8080/app/delete/all : efface toutes les urls en base

* http://localhost:8080/app/delete/{id} : efface une url donnée

Composition de l'application
----------------------------

* 2 vues sous forme de fichiers JSP, respectivement pour la page d'index et la page listant toutes les URLs
* 1 entité JPA représentant les urls raccourcies. Cette entité est très simple, elle comporte simplement un champ pour l'url de départ et un id représentant la version raccourcie
* 1 EJB session s'occupant de la gestion des urls raccourcies en base
* 5 servlets servant de contrôleurs correspondant aux actions exprimées plus haut.

Guide de survie
------------------

tout ce que vous avez besoin de savoir se trouve ici :

https://raw.github.com/mathieuancelin/JavaEE-Poitiers/master/02-JavaWeb.pdf

pour les manipulations de base de données, cet exemple devrait suffire :

```java
    public List<Truc> all() {
        return em.createQuery("select o from Truc o").getResultList();
    }
    
    public int deleteAll() {
        return em.createQuery("delete from Truc").executeUpdate();
    }

    public void delete(Truc truc) {
        em.remove(findById(truc.getId()));
    }

    public Truc findById(Long primaryKey) {
        return em.find(Truc.class, primaryKey);
    }
    
    public Shorten save(Truc truc) {
        if (em.contains(truc)) {
            return em.merge(truc);
        }
        em.persist(truc);
        return truc;
    }
```

