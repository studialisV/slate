---
title: Synapse Reference

language_tabs:
  - json
  - xml
  

toc_footers:
  - <a href='#'>Demander un jeton d'accès</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - applicaton_files
  - countries
  - errors

search: true
---

# Introduction

Synapse est le module Studialis dédié aux web services de type REST.

Il permet d’exposer et de recevoir les flux d’informations entre les différentes applications du système d’informations.

Ces webservices sont disponibles en [production](https://fake.fr/synapse/version.xml) ou en [préproduction](http://fake.fr/synapse/version.xml).

Les formats XML et JSON sont disponibles pour les services de type GET.

Les paramètres sont cumulatifs sauf si plusieurs valeurs sont envoyées à un même paramètre.

Pour envoyer plusieurs valeurs à un même paramètre, il convient d’ajouter [] après le nom du paramètre. Par exemple : year[]=2011 et year[]=2012. Synapse l’interprètera alors automatiquement comme un tableau de valeurs. Cette option est disponible uniquement sur les paramètres précisés.


# Authentification

> Pour chacune de vos requêtes, ajoutez le paramètre suivant : user_credentials=XXX.

> Pensez à remplacer `XXX` par cotre propre jeton d'accès.

L’authentification et la gestion des droits liées aux web services se fait via le module Bossanova.

Pour chaque appel aux web services, il convient d’utiliser le paramètre suivant :
`user_credentials=XXX`
<aside class="notice">
XXX est le jeton d’accès (single access token) de l’utilisateur qui souhaite accéder au WS. Il est disponible dans la fiche utilisateur de Bossanova.
</aside>

Chaque WS a un code d’habilitation lié. Pour autoriser un utilisateur à accéder à un WS, il convient, au sein de Bossanova, de sélectionner la ou les écoles pour lesquelles on souhaite accréditer l’utilisateur puis d’autoriser chaque WS par école de façon directe ou d’utiliser un profil.
