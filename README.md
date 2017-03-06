# Prise en main de ProjeQtOr

## 1. Pourquoi ProjeQtOr ?

- [Logiciel libre (licence GPLv3)](http://www.projeqtor.org/fr/product-fr/downloads-fr)
- [Produit français](http://www.projeqtor.org/fr/contact-fr)
- [Déjà utilisé par plusieurs ministères (agriculture, intérieur, santé)](http://www.projeqtor.org/fr/en-ligne/references)
- [Outil de gestion de projet complet](http://www.projeqtor.org/fr/accueil-fr/blog-gestion-de-projet/post/1/ms-project-n-est-pas-un-logiciel-de-gestion-de-projet)
- [Très actif](http://www.projeqtor.org/fr/)

### 1.1. Avantages

### 1.1.1. Pour les utilisateurs
- Outil en ligne donc accessible par tous,
- Workflow pour les projets, ...
- Notion de produits, sous-produits, projets et de liaisons entre eux,
- Listes des valeurs configurables,
- Communautaire (Nouvelles fonctionnalités...)

### 1.1.2. Technique
- Application facile à installer (WAMP/LAMP)
- Compatible postgresql ([Évolution payée par le Ministère de la Santé](http://www.projeqtor.org/fr/en-ligne/contribution-fr-2))
- Communautaire (Correction de bug, maj...)

## 2. Création et configuration d'un serveur de **test** local

### 2.1. Créer la machine virtuelle (Ubuntu 16.04 avec ProjeQtOr pré-installé)
- Installer [VirtualBox](https://www.virtualbox.org/wiki/Downloads),
- Installer [Vagrant](https://www.vagrantup.com/downloads.html),
- Installer [Git](https://git-scm.com/downloads),
- Cloner le dépôt sgalopin/projeqtor:
    - Ouvrir un Git Bash:
        - Se placer dans le répertoire dans lequel vous souhaitez installer le projet,
        - Cliquer sur le bouton droit de la souris,
        - Cliquer sur 'Git Bash',
        - Taper la ligne de commande suivante: 'git clone https://github.com/sgalopin/projeqtor.git'.
- Taper la commande 'cd projeqtor/VM_Projeqtor',
- Taper la commande 'vagrant up'.

### 2.2. Configurer la machine virtuelle
- Ouvrir la page "http://192.168.50.10",
- Configurer l'application tel que cela a été fait dans le fichier 'Conf\conf.png',
- Se loguer en admin/admin,
- Dans Parameters->User parameters->Display parameters->language, changer la langue pour 'French - Français',
- Dans Plug-ins->Plug-ins management->available plugins (local), ajouter le plugin '[translationFrench](https://www.projeqtor.net/fr/shop-fr/plugins/traductions-parametres-fr-detail)' disponible gratuitement sur le site de projeqtor,
- Ajouter la correspondance entre l'IP "192.168.50.10" et l'hôte "projeqtor.example.com" dans le fichier "hôte" de votre machine (facultatif).

## 3. Exemple d'utilisation avec certains projets

**Si cela n'est pas déjà fait:**

- Lancer la machine virtuelle,
- Se connecter à l'adresse http://192.168.50.10 de votre réseau privé,
- Se loguer en admin/admin.

### 3.1. Mise à jour des listes

#### 3.1.1. Ajout de fonctions
- Dans Paramètres->Listes de valeurs->Fonctions:
	- nom: **Chef de service**
	- ordre de tri: 8
- Dans Paramètres->Listes de valeurs->Fonctions:
	- nom: **Chef de département**
	- ordre de tri: 9
- Dans Paramètres->Listes de valeurs->Fonctions:
	- nom: **Chef de projet**
    - ordre de tri: 19

#### 3.1.2. Ajout de type d'organisation
- Dans Paramètres->Listes des types->Types d'organisations, ajouter un type:
	- nom: **Service**
    - code: SERV
    - ordre de tri: 0

### 3.2. Ajout d'organisation
- Dans Organisations, ajouter une organisation:
	- nom: **Mon service**
	- type d'organisation: Service
	- manager: Mon chef de service
- Puis dans Paramètres environnementaux->Ressources, sélectionner la ressource "Mon chef de service":
	- organisation: Mon service
- Dans Organisations, ajouter une organisation:
	- nom: **Mon département**
	- type d'organisation: Department
	- manager: Mon chef de département
- Puis dans Paramètres environnementaux->Ressources, sélectionner la ressource "Mon chef de département":
	- organisation: Mon département
- Puis dans Paramètres environnementaux->Ressources, sélectionner la ressource "Chef de projet 1":
	- organisation: Mon département

### 3.3. Création de l'environnement de travail

#### 3.3.1. Ajout de ressource
- Dans Paramètres environnementaux->Ressources, ajouter une ressource:
	- nom: **Mon chef de service**
	- nom de l'utilisateur: monchef.deservice
	- initiales: MCDS
	- profil: Superviseur
	- fonction principale: Chef de service
	- est un contact: oui
	- est un utilisateur: oui
- Dans Paramètres environnementaux->Ressources, ajouter une ressource:
	- nom: **Mon chef de département**
	- nom de l'utilisateur: monchef.dedepartement
	- initiales: MCDD
	- profil: Superviseur
	- fonction principale: Chef de département
	- est un contact: oui
	- est un utilisateur: oui
- Dans Paramètres environnementaux->Ressources, ajouter une ressource:
	- nom: **Chef de projet 1**
	- nom de l'utilisateur: chef.deprojet1
	- initiales: CDP1
	- adresse email: chef.deprojet1@gmail.com
	- profil: Chef de Projet
	- fonction principale: Chef de Projet
	- est un contact: oui
	- est un utilisateur: oui
- Dans Paramètres environnementaux->Ressources, ajouter une ressource:
	- nom: **Chef de projet 2**
	- nom de l'utilisateur: chef.deprojet2
	- initiales: CDP2
	- profil: Chef de Projet
	- fonction principale: Chef de Projet
	- est un contact: oui
	- est un utilisateur: oui
- Dans Paramètres environnementaux->Ressources, ajouter une ressource:
	- nom: **Chef de projet 3**
	- nom de l'utilisateur: chef.deprojet3
	- initiales: CDP3
	- profil: Chef de Projet
	- fonction principale: Chef de Projet
	- est un contact: oui
	- est un utilisateur: oui

#### 3.3.2. Ajout d'un produit
- Dans Paramètres environnementaux->Produits, ajouter un produit:
	- nom: **Mon produit**
	- type de produit: software
	- responsable: Mon chef de département

#### 3.3.3. Ajout d'un composant
- Dans Paramètres environnementaux->Composants, ajouter un composant:
	- nom: **MonProduitBureau**
	- responsable: Mon chef de département
	- Liste des produits utilisant ce composant: Mon produit
- Dans Paramètres environnementaux->Composants, ajouter un composant:
	- nom: **MonProduitServeur**
	- responsable: Mon chef de département
	- Liste des produits utilisant ce composant: Mon produit
- Dans Paramètres environnementaux->Composants, ajouter un composant:
	- nom: **MonProduitServices**
	- responsable: Mon chef de département
	- Liste des produits utilisant ce composant: Mon produit
- Dans Paramètres environnementaux->Composants, ajouter un composant:
	- nom: **MonProduitMeta**
	- responsable: Mon chef de département
	- Liste des produits utilisant ce composant: Mon produit
- Dans Paramètres environnementaux->Composants, ajouter un composant:
	- nom: **MonProduitNomade**
	- responsable: Mon chef de département
	- Liste des produits utilisant ce composant: Mon produit
- Dans Paramètres environnementaux->Composants, ajouter un composant:
	- nom: **MonProduitSync**
	- responsable: Mon chef de département
	- Liste des produits utilisant ce composant: Mon produit

#### 3.3.4. Ajout d'une version de produit
- Dans Paramètres environnementaux->Version de produit, ajouter une version:
	- produit: Mon produit
	- type de version du produit: Patch
	- nom: **v4.0.1**
	- responsable: Mon chef de département
	- entrée en service: initial 16/01/2017 planifié 16/01/2017 réel 13/02/2017 fait oui

#### 3.3.5. Ajout d'une équipe
- Dans Paramètres environnementaux->Equipes, ajouter une équipe:
	- nom: **Mon équipe**
	- manager: Mon chef de département
- Puis dans Paramètres environnementaux->Ressources, sélectionner la ressource "Chef de projet 1":
	- équipe: Mon équipe
- Puis dans Paramètres environnementaux->Ressources, sélectionner la ressource "Chef de projet 2":
	- équipe: Mon équipe

#### 3.3.6. Ajouter un client
- Dans Paramètres environnementaux->Clients, ajouter un client:
	- nom du client: **Mon client 1**
	- type de client: customer
- Dans Paramètres environnementaux->Clients, ajouter un client:
	- nom du client: **Mon client 2**
	- type de client: customer

### 3.4. Ajout d'un projet
- Dans Projet, ajouter un projet:
	- nom: **Mon projet 1**
	- type: Fixed Price
	- organisation: Mon département
	- client: Mon client 2
	- manager: Mon chef de département
	- état: in progress
	- situation: secured
	- niveau de qualité: conform
	- tendance: even
	- avancement global: 90%
	- Produit liés à ce projet: Mon produit 
- Dans Projet, ajouter un projet:
	- nom: **Mon projet 2**
	- type: Fixed Price
	- organisation: Mon département
	- client: Mon client 1
	- manager: Chef de projet 1
	- état: in progress
	- situation: secured
	- niveau de qualité: conform
	- tendance: even
	- avancement global: 100%
	- Produit liés à ce projet: Mon produit
- Dans Projet, ajouter un projet:
	- nom: **Mon projet 3**
	- type: Fixed Price
	- organisation: Mon département
	- client: Mon client 2
	- manager: Chef de projet 2
	- état: in progress
	- situation: secured
	- niveau de qualité: conform
	- tendance: even
	- avancement global: 100%
	- Produit liés à ce projet: Mon produit 

### 3.5. Gestion du travail

#### 3.5.1. Ajouter un tickets
- Dans Travail->Tickets, ajouter un tickets:
	- nom: **Problème 1**
	- type de ticket: Anomaly / Bug
	- projet: Mon projet 1
	- urgence: urgent
	- demandeur: Chef de projet 3
	- produit: Mon produit
	- composant: MonProduitBureau
	- version produit origine: v4.0.1
	- responsable: Mon chef de département
	- criticité: Medium
	- priorité: Medium priority

