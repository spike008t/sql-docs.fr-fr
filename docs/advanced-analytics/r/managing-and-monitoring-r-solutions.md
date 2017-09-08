---
title: "Gestion et surveillance des solutions d’apprentissage machine | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 388104730e6d8839843ce61d1c142449d9b02707
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="managing-and-monitoring-machine-learning-solutions"></a>Gestion et surveillance des solutions machine learning

Cet article décrit les fonctionnalités de SQL Server Machine Learning Services qui sont pertinents pour les administrateurs de base de données qui ont besoin pour commencer à travailler avec des solutions R et Python.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage automatique Services

## <a name="security"></a>Sécurité

Les administrateurs de base de données doivent fournir l’accès aux données non seulement aux chercheurs de données mais aussi des développeurs de rapports, les analystes d’entreprise et des consommateurs de données d’entreprise. L’intégration de R (et Python maintenant) dans SQL Server offre de nombreux avantages à l’administrateur de base de données qui prend en charge le rôle de science des données.

+ L’architecture de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] protège vos bases de données et isole l’exécution des sessions R du fonctionnement de l’instance de base de données.

+ Vous pouvez spécifier qui est autorisé à exécuter des scripts R et vous assurer que les données utilisées dans les travaux R sont gérées à l’aide des rôles de sécurité définis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

+ L’administrateur de base de données peut utiliser des rôles pour gérer l’installation des packages R et l’exécution de scripts R et Python.

Pour plus d'informations, consultez ces ressources :

+ [Considérations relatives à la sécurité du runtime R dans SQL Server](../../advanced-analytics/r/security-considerations-for-the-r-runtime-in-sql-server.md)

+ [Vue d’ensemble de la sécurité R](../r/security-overview-sql-server-r.md)

+ [Vue d’ensemble de la sécurité Python](../python/security-overview-sql-server-python-services.md)

+ [Installation et gestion des packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)

## <a name="configuration-and-management"></a>Configuration et gestion

Les administrateurs de base de données doivent intégrer des projets et priorités concurrents dans un point de contact unique : le serveur de base de données. Ils doivent prendre en charge analytique tout en conservant l’intégrité des magasins de données opérationnelles et de rapport. L’intégration d’apprentissage avec SQL Server offre de nombreux avantages à l’administrateur de base de données, qui sert de plus en plus un rôle essentiel dans le déploiement d’une infrastructure efficace pour la science des données.

+ Les sessions R et Python sont exécutées dans un processus séparé pour garantir que votre serveur continue à exécuter comme d’habitude, même si l’exécution du script externe a des problèmes.

+ Comptes d’utilisateur physique faibles sont utilisés pour contenir et isoler l’activité de script externe.

+ L’administrateur peut utiliser les outils de gestion de ressources SQL Server standard pour contrôler la quantité de ressources allouées au runtime R, afin d’éviter que des calculs massifs mettent en péril les performances globales du serveur.

Pour plus d'informations, consultez ces ressources :

+ [Gouvernance des ressources pour R Services](../r/resource-governance-for-r-services.md)

+ [Analyse de R Services](../r/monitoring-r-services.md)

+ [Configurer et gérer les Extensions d’Analytique avancée](../r/configure-and-manage-advanced-analytics-extensions.md)
