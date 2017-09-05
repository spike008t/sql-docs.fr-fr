---
title: "Mappage des schémas d’Oracle aux schémas SQL Server (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2ca4fbcf3a49ccaf289bab39e3dbd15493fe08bb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>Mappage des schémas d’Oracle aux schémas SQL Server (OracleToSQL)
Dans Oracle, chaque base de données a un ou plusieurs schémas. Par défaut, SSMA migre tous les objets dans un schéma Oracle pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nommé pour le schéma de base de données. Toutefois, vous pouvez personnaliser le mappage entre les schémas Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] bases de données.  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle et schémas SQL Server  
Une base de données Oracle contient des schémas. Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] contient plusieurs bases de données, chacune d’elles peut comporter plusieurs schémas.  
  
Le concept d’Oracle d’un schéma est mappé à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] concept d’une base de données et d’un de ses schémas. Par exemple, Oracle peut avoir un schéma nommé **HR**. Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] peut avoir une base de données nommée **HR**, et dans cette base de données, des schémas. Un schéma est la **dbo** (ou le propriétaire de la base de données) schéma. Par défaut, le schéma Oracle **HR** seront mappées à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données et le schéma **HR.dbo**. SSMA fait référence à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] combinaison de la base de données et le schéma en tant que schéma.  
  
Vous pouvez modifier le mappage entre Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schémas.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modification de la base de données cible et le schéma  
Dans SSMA, vous pouvez mapper un schéma Oracle pour éventuellement [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schéma.  
  
**Pour modifier la base de données et le schéma**  
  
1.  Dans l’Explorateur de métadonnées d’Oracle, sélectionnez **schémas**.  
  
    Le **schéma de mappage** onglet est disponible lorsque vous sélectionnez une base de données individuel, le **schémas** dossier ou les schémas individuels. La liste dans le **schéma de mappage** onglet personnalisé pour l’objet sélectionné.  
  
2.  Dans le volet droit, cliquez sur le **schéma de mappage** onglet.  
  
    Vous verrez une liste de tous les schémas Oracle, suivi d’une valeur cible. Cette cible est représentée dans une notation de deux parties (*database.schema*) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] où vos objets et données seront migrées.  
  
3.  Sélectionnez la ligne qui contient le mappage que vous souhaitez modifier, puis cliquez sur **modifier**.  
  
    Dans le **choisir un schéma cible** boîte de dialogue, vous pourrez consulter pour la base de données cible disponible et de schéma ou de type de la base de données et le schéma de nom dans la zone de texte dans une notation de deux parties (database.schema), puis **OK**.  
  
4.  La cible est modifiée sur le **schéma de mappage** onglet.  
  
**Modes de mappage**  
  
-   Mappage à SQL Server  
  
Vous pouvez mapper la base de données source vers une base de données cible. Par défaut la base de données source est mappé à la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données avec laquelle vous vous êtes connecté à l’aide de SSMA. Si la base de données cible en cours de mappage est inexistant sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], puis vous serez invité avec un message **« la base de données et/ou un schéma n’existe pas dans la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] métadonnées. Il est créé lors de la synchronisation. Voulez-vous continuer ? »** Cliquez sur Oui. De même, vous pouvez mapper le schéma non existants de schéma sous la cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données qui sera créé pendant la synchronisation.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Retour à la base de données par défaut et le schéma  
Si vous personnalisez le mappage entre un schéma Oracle et un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] schéma, vous pouvez rétablir les valeurs par défaut le mappage.  
  
**Pour rétablir la base de données par défaut et le schéma**  
  
1.  Sous l’onglet mappage de schéma, sélectionnez n’importe quelle ligne, puis cliquez sur **rétablir par défaut** pour rétablir la base de données par défaut et le schéma.  
  
## <a name="next-steps"></a>Étapes suivantes  
Si vous souhaitez analyser la conversion des objets Oracle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] des objets, vous pouvez [créer un rapport de conversion](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357). Dans le cas contraire, vous pouvez [convertir les définitions d’objets de base de données Oracle](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] définitions d’objets.  
  
## <a name="see-also"></a>Voir aussi  
[Connexion à SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Migration bases de données Oracle pour SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
