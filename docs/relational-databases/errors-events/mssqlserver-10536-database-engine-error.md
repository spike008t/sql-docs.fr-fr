---
title: MSSQLSERVER_10536 | Microsoft Docs
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
- 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8c48c445738488fb433f1b624358b14199cab50
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10536|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_TOO_MANY_STMTS|  
|Texte du message|Impossible de créer le repère de plan '%.\*ls', car le lot ou module correspondant au **@plan_handle** spécifié contient plus de 1000 instructions éligibles. Créez un repère de plan pour chaque instruction du lot ou module en indiquant une valeur **statement_start_offset** pour chacune.|  
  
## <a name="explanation"></a>Explication  
Le lot ou module correspondant au **@plan_handle** spécifié contient plus de 1000 instructions éligibles.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Créez un repère de plan pour chaque instruction du lot ou module en indiquant une valeur **statement_start_offset** pour chacune.  
  
## <a name="see-also"></a> Voir aussi  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
