---
title: Type de données ProactiveCachingObjectNotificationBinding (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 82c176201804e555f4e844ea38541fcbf20d9446
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="proactivecachingobjectnotificationbinding-data-type-assl"></a>Type de données ProactiveCachingObjectNotificationBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit un type de données dérivé abstrait qui fournit à l'élément [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md) des informations sur les modifications de source de données, soit dans les tables et les vues spécifiées, soit dans les tables et les vues identifiées par le biais de liaisons de données existantes qui exigent une reconstruction du cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCachingObjectNotificationBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingObjectNotificationBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Types de données dérivés|[ProactiveCachingInheritedBinding](../../../analysis-services/scripting/data-type/proactivecachinginheritedbinding-data-type-assl.md), [ProactiveCachingTablesBinding](../../../analysis-services/scripting/data-type/proactivecachingtablesbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[NotificationTechnique](../../../analysis-services/scripting/properties/notificationtechnique-element-assl.md)|  
|Éléments dérivés|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la **ProactiveCachingBinding** type, y compris une table de la hiérarchie d’héritage de **ProactiveCachingBinding** types, consultez [données ProactiveCachingBinding Type &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md).  
  
 Pour plus d’informations sur la **liaison** type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la **liaison** type et la hiérarchie d’héritage de **de liaison**  types, consultez [Type de données de liaison &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et liaisons & #40 ; SSAS multidimensionnel & #41 ; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ProactiveCachingObjectNotificationBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
