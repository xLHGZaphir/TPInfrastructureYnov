# TPInfrastructureYnov
TP automatisation de déploiement d'infrastructures - Ynov 2K19

Le but est de déployer une infrastructure Open source via des outils comme Vagrant, Docker, Ansible et Molécule.

Nous avons choisi de créer une infrastructure contenant : 
  - Netbox (redondé) 
  - Serveur de fichiers (redondé)
  
  Cette infrastructure contient donc quatre serveurs, les deux netbox se synchronisent, les deux serveurs de fichiers aussi.
  De plus, des sauvegardes sont configurées sur les serveurs de fichiers au cas ou. 
  
  
