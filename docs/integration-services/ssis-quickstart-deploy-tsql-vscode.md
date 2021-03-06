---
title: Déployer un projet SSIS avec Transact-SQL (VS Code) | Microsoft Docs
ms.date: 09/25/2017
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6c32302d499f1c8dc450d6e10451f080b30249d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-an-ssis-project-from-visual-studio-code-with-transact-sql"></a>Déployer un projet SSIS à partir de Visual Studio Code avec Transact-SQL
Ce guide de démarrage rapide montre comment utiliser Visual Studio Code pour se connecter à la base de données du catalogue SSIS, puis utiliser des instructions Transact-SQL pour déployer un projet SSIS dans le catalogue SSIS.

> [!NOTE]
> La méthode décrite dans cet article n’est pas disponible quand vous vous connectez à un serveur Azure SQL Database avec Visual Studio Code. La procédure stockée `catalog.deploy_project` attend le chemin du fichier `.ispac` dans le système de fichiers local.

Visual Studio Code est un éditeur de code pour Windows, Mac OS et Linux qui prend en charge les extensions, notamment l’extension `mssql` pour la connexion à Microsoft SQL Server, Azure SQL Database ou Azure SQL Data Warehouse. Pour plus d’informations sur VS Code, consultez [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Conditions préalables requises

Avant de commencer, vérifiez que vous avez installé la dernière version de Visual Studio Code et chargé l’extension `mssql`. Pour télécharger ces outils, consultez les pages suivantes :
-   [Télécharger Visual Studio Code](https://code.visualstudio.com/Download)
-   [Extension mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Définir SQL comme mode de langage dans VS Code

Pour activer les commandes `mssql` et T-SQL IntelliSense, définissez **SQL** comme mode de langage dans Visual Studio Code.

1. Ouvrez Visual Studio Code, puis ouvrez une nouvelle fenêtre. 

2. Cliquez sur **Texte brut** en bas à droite de la barre d’état.
 
3. Dans le menu déroulant **Sélectionner le mode de langage** qui s’affiche, sélectionnez ou entrez **SQL**, puis appuyez sur **Entrée** pour définir SQL comme mode de langage. 

## <a name="connect-to-the-ssis-catalog-database"></a>Se connecter à la base de données du catalogue SSIS

Utilisez Visual Studio Code pour établir une connexion au catalogue SSIS.

> [!IMPORTANT]
> Avant de continuer, vérifiez que vous avez vos informations de connexion, de serveur et de base de données à portée de main. Si vous modifiez le focus à partir de Visual Studio Code après avoir commencé à entrer les informations de profil de connexion, vous devez redémarrer la création du profil de connexion.

1. Dans VS Code, appuyez sur **Ctrl+Maj+P** (ou **F1**) pour ouvrir la palette de commandes.

2. Tapez **sqlcon** et appuyez sur **Entrée**.

3. Appuyez sur **Entrée** pour sélectionner **Créer un profil de connexion**. Cette étape crée un profil de connexion pour votre instance de SQL Server.

4. Suivez les invites afin de spécifier les propriétés de connexion pour le nouveau profil de connexion. Après avoir spécifié chaque valeur, appuyez sur **Entrée** pour continuer. 

   | Paramètre       | Valeur suggérée | En savoir plus |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nom du serveur** | Nom complet du serveur |  |
   | **Nom de la base de données** | **SSISDB** | Nom de la base de données avec laquelle établir une connexion. |
   | **Authentification** | Connexion SQL| Ce guide de démarrage rapide utilise l’authentification SQL. |
   | **User name** | Compte Administrateur du serveur | Il s’agit du compte que vous avez spécifié quand vous avez créé le serveur. |
   | **Mot de passe (connexion SQL)** | Mot de passe de votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié quand vous avez créé le serveur. |
   | **Enregistrer le mot de passe** | Oui ou Non | Si vous ne souhaitez pas entrer le mot de passe à chaque fois, sélectionnez Oui. |
   | **Entrez un nom pour ce profil** | Nom d’un profil, tel que **mySSISServer** | L’enregistrement du nom de profil permet d’accélérer les connexions suivantes. | 

5. Appuyez sur la touche **Échap** pour fermer le message d’information qui vous signale que le profil a été créé et connecté.

6. Vérifiez votre connexion dans la barre d’état.

## <a name="run-the-t-sql-code"></a>Exécuter le code T-SQL
Exécutez le code Transact-SQL suivant pour déployer un projet SSIS.

1. Dans la fenêtre **Éditeur**, entrez la requête suivante dans la fenêtre de requête vide.

2. Mettez à jour les valeurs de paramètres dans la procédure stockée `catalog.deploy_project` pour votre système.

3. Appuyez sur **Ctrl+Maj+E** pour exécuter le code et déployer le projet.

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary = (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Déployer un package SSIS à partir de l’invite de commandes](./ssis-quickstart-deploy-cmdline.md)
    - [Déployer un package SSIS avec PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Déployer un package SSIS avec C#](./ssis-quickstart-deploy-dotnet.md) 
- Exécutez un package déployé. Pour exécuter un package, vous pouvez choisir parmi plusieurs outils et langages. Pour plus d’informations, consultez les articles suivants :
    - [Exécuter un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécuter un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécuter un package SSIS avec C#](./ssis-quickstart-run-dotnet.md) 
