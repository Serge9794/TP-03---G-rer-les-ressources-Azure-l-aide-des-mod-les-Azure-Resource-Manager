# TP-03---G-rer-les-ressources-Azure-l-aide-des-mod-les-Azure-Resource-Manager
Ce TP présente l'utilisation des modèles Azure Resource Manager (ARM) pour gérer les ressources Azure de manière automatisée et cohérente. Vous apprendrez à créer, modifier et déployer des templates afin d'assurer une gestion standardisée, reproductible et fiable des environnements cloud.


## TP 03– Déploiement & Gestion des Ressources Azure avec ARM Templates & Bicep
## 🎯Objectif du TP

Ce TP a pour but de vous apprendre à automatiser le déploiement des ressources Azure grâce aux modèles ARM Templates, aux fichiers Bicep, ainsi qu’aux outils Azure Portal, PowerShell, Azure CLI et Cloud Shell.

## 🏢 Scénario

L’entreprise **TechNova** souhaite automatiser la création d’environnements cloud pour renforcer la cohérence et réduire les risques d’erreurs.
Votre mission est de créer, exporter, modifier et déployer des ressources Azure à l’aide de modèles ARM et Bicep.

## 📂 Contenu du TP
## 🔶 Étape 1 — Créer un modèle ARM à partir du portail Azure
**🔹 Objectif**

Créer un compte de stockage et exporter le modèle ARM généré automatiquement.

**🔹 Actions**

1-Se connecter au Portail Azure

2-Créer un Resource Group nommé :tng-rg3

3-Créer un Storage Account avec les paramètres suivants :

_Nom : storage-nv01

_Région : West Europe

_Redondance : LRS

Une fois la ressource créée, se rendre dans :Automatisation → Export Template

4-Télécharger les fichiers :template.json ;parameters.json

📸 Capture d’écran à insérer ici

(Portail Azure → Export Template)

## 🔶 Étape 2 — Modifier un modèle ARM et le redéployer
**🔹 Objectif**

Comprendre la structure d’un ARM Template et déployer une version modifiée.

**🔹 Actions**

1-Ouvrir template.json

2-Modifier le nom de la ressource pour :
storage-nv02

3-Enregistrer votre fichier

4-Déployer la ressource depuis Azure Portal :

5-Créer un déploiement personnalisé

6-Charger template.json et parameters.json

📸 Capture d’écran à insérer ici

(Portail Azure → Custom Deployment avec template.json)

## 🔶 Étape 3 — Déployer ARM Template avec PowerShell
**🔹 Objectif**

Utiliser Cloud Shell PowerShell pour déployer un ARM Template.

**🔹 Actions**

1-Ouvrir Cloud Shell → mode PowerShell

2-Importer votre template.json

3-Lancer le déploiement :

New-AzResourceGroupDeployment `-ResourceGroupName tng-rg3 `-TemplateFile template.json ` -storageAccountName storage-nv03

📸 Capture d’écran à insérer ici

(Cloud Shell PowerShell avec la commande exécutée)

## 🔶 Étape 4 — Déployer ARM Template avec Azure CLI
**🔹 Objectif**

Utiliser Cloud Shell (Bash) pour déployer le modèle ARM.

**🔹 Actions**

1-Ouvrir Cloud Shell → mode Bash

2-Importer template.json

3-Lancer le déploiement :az deployment group create \ --resource-group tng-rg3 \--template-file template.json \--parameters storageAccountName=storage-nv04

📸 Capture d’écran à insérer ici

(Cloud Shell Bash avec la commande exécutée)

## 🔶 Étape 5 — Déployer une ressource via un fichier Bicep
**🔹 Objectif**

Découvrir le langage Bicep et déployer une ressource Azure via un fichier .bicep.

**🔹 Exemple de fichier main.bicep**
resource stg 'Microsoft.Storage/storageAccounts@2023-01-01' = 
{
  name: 'storage-nv05'
  location: resourceGroup().location
  sku: {
    name: 'Standard_LRS'
  }
  kind: 'StorageV2'
}

**🔹 Actions**

Créer un fichier : main.bicep

Coller le code ci-dessus

Déployer avec Azure CLI :

az deployment group create \
  --resource-group tng-rg3 \
  --template-file main.bicep

📸 Capture d’écran à insérer ici

(Déploiement Bicep)

**🧹 Nettoyage des ressources (IMPORTANT)**

Pour éviter les coûts Azure :

az group delete --name tng-rg3

📸 Capture d’écran à insérer ici

(Suppression du resource group)

## Points clés à retenir

ARM Templates = Infrastructure as Code en JSON

Bicep = Langage moderne simplifié pour ARM

Supports de déploiement :

Azure Portal

PowerShell

Azure CLI

Cloud Shell

Avantages : cohérence, automatisation, réduction des erreurs humaines
