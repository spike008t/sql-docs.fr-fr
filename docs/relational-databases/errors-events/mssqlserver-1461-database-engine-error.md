---
title: MSSQLSERVER_1461 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db041bd22b068dc43bc922003675f0cece338aba
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver1461"></a>MSSQLSERVER_1461
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1461|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_SAFETY_MISMATCH|  
|Texte du message|Plusieurs niveaux de sécurité de mise en miroir de bases de données ont été détectés pour la base de données « %.*ls ». Le niveau de sécurité FULL sera utilisé.|  
  
## <a name="explanation"></a>Explication  
Les connexions de mise en miroir ont été interrompues lorsque le niveau de sécurité des transactions a été modifié car les paramètres de sécurité des transactions étaient incohérents entre la base de données principale et la base de données miroir. Le paramètre de sécurité par défaut, à savoir la sécurité totale des transactions, sera utilisé. La session sera exécutée en mode haute sécurité.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour désactiver la sécurité des transactions, réexécutez l’instruction ALTER DATABASE *nom_base_de_données* SET PARTNER SAFETY OFF sur la base de données principale.  
  
