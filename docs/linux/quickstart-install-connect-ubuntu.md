---
title: Prise en main 2017 du serveur SQL sur Ubuntu | Documents Microsoft
description: "Ce didacticiel de démarrage rapide montre comment installer SQL Server 2017 sur Ubuntu puis créer et interroger une base de données avec sqlcmd."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/24/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 052a2f0a7618c5e160d3c17a3a1efd7d7a4b3fd6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-and-create-a-database-on-ubuntu"></a>Installer SQL Server et de créer une base de données sur Ubuntu

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Dans ce didacticiel de démarrage rapide, vous d’abord installez SQL Server 2017 RC2 sur Ubuntu 16.04. Se connecter avec **sqlcmd** à créer votre première base de données et exécuter des requêtes.

> [!TIP]
> Ce didacticiel nécessite l’entrée d’utilisateur et une connexion internet. Si vous êtes intéressé par le [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline) procédures d’installation, consultez [aide à l’Installation de SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Configuration requise

Vous devez disposer d’un ordinateur Ubuntu avec **au moins 3,25 Go** de mémoire.

Pour installer Ubuntu sur votre propre ordinateur, accédez à [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server). Vous pouvez également créer des machines virtuelles de Ubuntu dans Azure. Consultez [créer et gérer les machines virtuelles Linux avec l’interface CLI Azure](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installation de SQL Server

Pour configurer SQL Server sur Ubuntu, exécutez les commandes suivantes dans un Terminal Server pour installer le **mssql-serveur** package.

1. Importer les clés GPG référentiel public :

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Enregistrer le référentiel Microsoft SQL Server Ubuntu :

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server.list)"
   ```

1. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

1. Après la fin de l’installation package, exécutez **le programme d’installation de mssql-conf** et suivez les invites pour définir le mot de passe SA et choisissez votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (Minimum longueur 8 caractères, y compris les majuscules et minuscules, chiffres en base 10 et/ou des symboles non alphanumériques).

   > [!TIP]
   > Lorsque vous installez RC2, sans licences achetées sont requis pour essayer toutes les éditions. S’agissant d’une version release candidate, le message suivant apparaît, quelle que soit l’édition que vous sélectionnez :
   >
   > `This is an evaluation version.  There are [175] days left in the evaluation period.`
   >
   > Ce message ne reflète pas l’édition que vous avez sélectionné. Il est lié à la période d’évaluation pour RC2.

1. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```

1. Si vous envisagez de vous connecter à distance, vous devrez peut-être également ouvrir le port TCP du serveur SQL (1433 par défaut) sur votre pare-feu.

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur d’Ubuntu et est prêt à utiliser !

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Importer les clés GPG référentiel public :

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Enregistrer le référentiel Microsoft Ubuntu :

   ```bash
   sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
   ```

1. Mettre à jour la liste des sources et exécutez la commande d’installation avec le package de développement unixODBC :

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-tools unixodbc-dev
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier la **chemin d’accès** des sessions de connexion et des sessions/non-connexion interactive :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

> [!TIP]
> **SQLCMD** est le seul outil pour la connexion à SQL Server pour exécuter des requêtes et d’effectuer les tâches de gestion et de développement. Incluent d’autres outils [SQL Server Management Studio](sql-server-linux-develop-use-ssms.md) et [Visual Studio Code](sql-server-linux-develop-use-vscode.md).

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]