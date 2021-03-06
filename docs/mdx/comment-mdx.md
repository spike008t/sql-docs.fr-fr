---
title: Commentaire (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '*/'
- /*
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- /*...*/ (comment)
ms.assetid: 64434ae4-80ce-4634-86b8-4125dfaa7f61
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4a4c9aa5bfbb27fd208b6f418e18b1c224451f27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="comment-mdx"></a>Commentaire (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Signale un texte de commentaire inséré par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Le serveur n’évalue pas le texte entre les caractères de commentaire / * et \*/. Il est possible d'insérer des commentaires sur une ligne distincte ou à l'intérieur d'une instruction MDX. Commentaires de plusieurs lignes doivent être signalés par /\* et \*/.  
  
 Il n'y a pas de longueur maximale pour les commentaires. Les commentaires peuvent être imbriqués ; par exemple, `/* Test /*Comment*/ Text*/` est un commentaire imbriqué.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;Commentaire&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [--& #40 ; Commentaire & #41 ; & #40 ; MDX & #41 ;](../mdx/comment-mdx-operator-reference.md)   
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
