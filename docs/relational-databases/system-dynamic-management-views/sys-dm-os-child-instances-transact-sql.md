---
title: Sys.dm_os_child_instances (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs: TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d13a86c17d95f31d2ffe99fa6675a0e0fe877ecd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmoschildinstances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque instance utilisateur qui a été créée à partir de l'instance de serveur parente.  
  
> **IMPORTANT !** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Les informations retournées par **sys.dm_os_child_instances** peut être utilisé pour déterminer l’état de chaque Instance de l’utilisateur (heart_beat) et pour obtenir le nom du canal (instance_pipe_name) qui peut être utilisé pour créer une connexion à l’Instance utilisateur à l’aide [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou SQLCmd. Vous pouvez vous connecter à une instance utilisateur uniquement lorsque cette dernière a été démarrée par un processus externe, tel qu'une application cliente. Les outils de gestion de SQL Server ne peuvent pas démarrer une instance utilisateur.  
  
> **Remarque :** les Instances utilisateur sont une fonctionnalité de [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] uniquement.  
  
> **Remarque** à appeler à partir [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_os_child_instances**.  
  
|Colonne|Data type| Description|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar (256)**|Nom de l'utilisateur pour lequel cette instance utilisateur a été créée.|  
|owning_principal_sid|nvarchar (256)|SID (Security-Identifier) du principal propriétaire de cette instance utilisateur. Elle correspond au SID Windows.|  
|owning_principal_sid_binary|varbinary(85)|Version binaire du SID de l'utilisateur propriétaire de l'instance utilisateur.|  
|**nom_instance**|**nvarchar (128)**|Nom de cette instance utilisateur.|  
|**instance_pipe_name**|**nvarchar (260)**|Lors de la création d'une instance utilisateur, un canal nommé est créé auquel les applications peuvent se connecter. Ce nom peut s'utiliser dans une chaîne de connexion pour se connecter à cette instance utilisateur.|  
|**os_process_id**|**Int**|Numéro du processus Windows pour cette instance utilisateur.|  
|**os_process_creation_date**|**DateTime**|Date et heure du dernier démarrage du processus de cette instance utilisateur.|  
|**heart_beat**|**nvarchar (5)**|État actuel de cette instance utilisateur ; ALIVE ou DEAD.|  
|**pdw_node_id**|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la vue de gestion dynamique, consultez [les fonctions et vues de gestion dynamique &#40; Transact-SQL &#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Instances d’utilisateur pour les non-administrateurs](http://msdn.microsoft.com/en-us/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  


