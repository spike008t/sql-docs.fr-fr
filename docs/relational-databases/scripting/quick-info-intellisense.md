---
title: Infos express (IntelliSense) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology:
- database-engine
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 63d8d03156bb3d6aef313b0b33c19f81c625ca61
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="quick-info-intellisense"></a>Infos express (IntelliSense)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  L’option [!INCLUDE[msCoName](../../includes/msconame-md.md)] Info express **de** IntelliSense affiche la déclaration complète de tout identificateur présent dans votre code. Lorsque vous déplacez le pointeur de la souris sur un identificateur, sa déclaration apparaît dans une fenêtre indépendante jaune. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Info express** est disponible dans les éditeurs de requête XML et du moteur de base de données.  
  
## <a name="transact-sql-quick-info"></a>Info express (Transact-SQL)  
 **Info express** affiche deux types d’informations dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Quand l’option **Info express** n’est pas en mode débogage, elle affiche la déclaration de l’expression. En revanche, en mode débogage, **Info express** affiche le nom de l’expression et sa valeur actuelle.  
  
 Dans l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] , **Info express** n’est disponible que pour les parties de la syntaxe [!INCLUDE[tsql](../../includes/tsql-md.md)] prises en charge par IntelliSense. Par exemple, si vous déplacez le pointeur de la souris sur l’identificateur d’un objet dont le type de données n’est pas pris en charge par IntelliSense, la fenêtre indépendante **Info express** contient un message indiquant que le type de données n’est pas pris en charge.  
  
## <a name="see-also"></a> Voir aussi  
 [Syntaxe Transact-SQL prise en charge par IntelliSense](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)  
  
  
