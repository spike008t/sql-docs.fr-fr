---
title: IsEmpty (MDX) | Documents Microsoft
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
- ISEMPTY
dev_langs:
- kbMDX
helpviewer_keywords:
- IsEmpty function
ms.assetid: b4a50996-61d1-4e23-8003-7d530195ea72
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6cc77efe9a3c7c3c1b9801f0545c785f6934e290
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne une valeur indiquant si l'expression évaluée est la valeur de la cellule vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>Arguments  
 *Value_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne généralement les coordonnées des cellules d'un membre ou d'un tuple.  
  
## <a name="remarks"></a>Notes  
 Le **IsEmpty** fonction renvoie **true** si l’expression évaluée est une valeur de cellule vide. Sinon, cette fonction retourne **false**.  
  
> [!NOTE]  
>  La propriété par défaut d'un membre est la valeur du membre.  
  
 Le **IsEmpty** (fonction) est la seule façon de tester de manière fiable pour une cellule vide, car la valeur de cellule vide a une signification spéciale dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Si l’évaluation de l’expression de valeur retourne une erreur, la fonction retournera **false**. Une expression de valeur peut retourner une erreur, notamment si la référence des propriétés désigne une propriété non valide ou inexistante.  
  
 Pour plus d'informations sur les cellules vides, consultez la documentation OLE DB.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne TRUE si le Montant des ventes sur Internet pour le membre actuel dans la hiérarchie Fiscal de la dimension Date retourne une cellule vide :  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des valeurs vides](../mdx/working-with-empty-values.md)   
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
