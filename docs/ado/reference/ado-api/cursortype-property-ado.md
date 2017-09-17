---
title: "CursorType, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::CursorType
helpviewer_keywords:
- CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b7031dc9b7acd89eea8491837ec4a550f34dc1ef
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="cursortype-property-ado"></a>CursorType, propriété (ADO)
Indique le type de curseur utilisé dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) valeur. La valeur par défaut est **adOpenForwardOnly**.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CursorType** propriété pour spécifier le type de curseur qui doit être utilisé lors de l’ouverture du **Recordset** objet.  
  
 Seule la valeur **adOpenStatic** est pris en charge si le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) est définie sur **adUseClient**. Si une valeur non prise en charge est définie, aucune erreur n’est générée ; prise en charge la plus proche **CursorType** sera utilisé à la place.  
  
 Si un fournisseur ne prend pas en charge le type de curseur demandé, il peut retourner un autre type de curseur. Le **CursorType** propriété sera modifiée pour correspondre au type de curseur en cours d’utilisation lorsque le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet est ouvert. Pour vérifier les fonctionnalités spécifiques du curseur retourné, utilisez la [prend en charge](../../../ado/reference/ado-api/supports-method.md) (méthode). Après avoir fermé le **Recordset**, le **CursorType** propriété retrouve sa valeur d’origine.  
  
 Le tableau suivant indique les fonctionnalités des fournisseurs (identifiées par **prend en charge** constantes de la méthode) requis pour chaque type de curseur.  
  
|Pour un jeu d’enregistrements de ce type de curseur|La méthode doit retourner True pour toutes les constantes suivantes :|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|aucun|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Bien que **prend en charge**(**adUpdateBatch**) peut se produire pour les curseurs dynamiques et avant uniquement, pour le traitement par lots met à jour vous devez utiliser un jeu de clés ou un curseur statique. Définir le [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) propriété **adLockBatchOptimistic** et **CursorLocation** propriété **adUseClient** pour activer le curseur Service pour OLE DB, qui est nécessaire pour les mises à jour par lots.  
  
 Le **CursorType** propriété est en lecture/écriture lorsque le **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
> [!NOTE]
>  **Utilisation du Service de données à distance** lorsqu’il est utilisé sur un côté client **Recordset** objet, le **CursorType** propriété peut être définie uniquement sur **adOpenStatic**.  
  
## <a name="applies-to"></a>S'applique à  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CursorType, LockType et EditMode, propriétés-exemple (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType et EditMode, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Prend en charge (méthode)](../../../ado/reference/ado-api/supports-method.md)
