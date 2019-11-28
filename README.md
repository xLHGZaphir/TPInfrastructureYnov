# TPInfrastructureYnov
TP automatisation de déploiement d'infrastructures - Ynov 2K19

Le but est de déployer une infrastructure Open source via des outils comme Vagrant, Docker, Ansible et Molécule.

Nous avons choisi de créer une infrastructure contenant : 

  - Netbox (redondé) deployer automatiquement le monitoring d'un nouveau poste
  #- Serveur de fichiers (redondé)
  - Création d'un ticket automatique en cas de problème sur un hôte. 
  
  Inventaire: 
  
  Cette infrastructure contient donc quatre serveurs, les deux netbox se synchronisent, les deux serveurs de fichiers aussi.
  De plus, des sauvegardes sont configurées sur les serveurs de fichiers au cas ou. 
  
Pour la synchronisation entre les hosts nous allons utiliser rsync.

MCO = maintient en condition opérationnelle 

Monitoring 

fichier start infra 

les différentes procédures

sauvegardes -- script bash

wiki ? -> pour le maintien de la solution 

Le but est de pouvoir faire un vagrant up et que tout se monte et soit configuré (NETBOX et serveur de fichier redondés)

En second lieu viendra le serveur de ticket (GLPI) et la remontée des logs (à définir)
