---
title: TERTIARY_WEIGHTS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TERTIARY_WEIGHTS_TSQL
- TERTIARY_WEIGHTS
dev_langs:
- TSQL
helpviewer_keywords:
- weights [SQL Server]
- SQL tertiary collations
- TERTIARY_WEIGHTS function
ms.assetid: 7e1f5350-260b-4c61-8c84-69bb1a214f1f
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7414f60414c14457dddc6f860201fd84409f1cb1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="collation-functions---tertiaryweights-transact-sql"></a>Fonctions de classement - TERTIARY_WEIGHTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne une chaîne binaire de poids pour chaque caractère d'une expression de chaîne non-Unicode définie avec un classement SQL tertiaire.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
TERTIARY_WEIGHTS( non_Unicode_character_string_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*non_Unicode_character_string_expression*  
Est une chaîne [expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **char**, **varchar**, ou **varchar (max)** définies sur un classement SQL tertiaire. Pour obtenir la liste de ces classements, consultez Remarques.
  
## <a name="return-types"></a>Types de retour
TERTIARY_WEIGHTS retourne **varbinary** lorsque *non_Unicode_character_string_expression* est **char** ou **varchar**et retourne **varbinary (max)** lorsque *non_Unicode_character_string_expression* est **varchar (max)**.
  
## <a name="remarks"></a>Notes  
TERTIARY_WEIGHTS retourne NULL lorsque *non_Unicode_character_string_expression* n’est pas défini avec un classement SQL tertiaire. Le tableau suivant montre les classements SQL tertiaires.
  
|ID d'ordre de tri|classement SQL|  
|---|---|
|33|SQL_Latin1_General_Pref_CP437_CI_AS|  
|34|SQL_Latin1_General_CP437_CI_AI|  
|43|SQL_Latin1_General_Pref_CP850_CI_AS|  
|44|SQL_Latin1_General_CP850_CI_AI|  
|49|SQL_1xCompat_CP850_CI_AS|  
|53|SQL_Latin1_General_Pref_CP1_CI_AS|  
|54|SQL_Latin1_General_CP1_CI_AI|  
|56|SQL_AltDiction_Pref_CP850_CI_AS|  
|57|SQL_AltDiction_CP850_CI_AI|  
|58|SQL_Scandinavian_Pref_CP850_CI_AS|  
|82|SQL_Latin1_General_CP1250_CI_AS|  
|84|SQL_Czech_CP1250_CI_AS|  
|86|SQL_Hungarian_CP1250_CI_AS|  
|88|SQL_Polish_CP1250_CI_AS|  
|90|SQL_Romanian_CP1250_CI_AS|  
|92|SQL_Croatian_CP1250_CI_AS|  
|94|SQL_Slovak_CP1250_CI_AS|  
|96|SQL_Slovenian_CP1250_CI_AS|  
|106|SQL_Latin1_General_CP1251_CI_AS|  
|108|SQL_Ukrainian_CP1251_CI_AS|  
|113|SQL_Latin1_General_CP1253_CS_AS|  
|114|SQL_Latin1_General_CP1253_CI_AS|  
|130|SQL_Latin1_General_CP1254_CI_AS|  
|146|SQL_Latin1_General_CP1256_CI_AS|  
|154|SQL_Latin1_General_CP1257_CI_AS|  
|156|SQL_Estonian_CP1257_CI_AS|  
|158|SQL_Latvian_CP1257_CI_AS|  
|160|SQL_Lithuanian_CP1257_CI_AS|  
|183|SQL_Danish_Pref_CP1_CI_AS|  
|184|SQL_SwedishPhone_Pref_CP1_CI_AS|  
|185|SQL_SwedishStd_Pref_CP1_CI_AS|  
|186.|SQL_Icelandic_Pref_CP1_CI_AS|  
  
TERTIARY_WEIGHTS est destiné à utiliser dans la définition d’une colonne calculée qui est définie sur les valeurs d’une **char**, **varchar**, ou **varchar (max)** colonne. Définition d’un index sur la colonne calculée et **char**, **varchar**, ou **varchar (max)** colonne peut améliorer les performances lors de la **char**, **varchar**, ou **varchar (max)** colonne est spécifiée dans la clause ORDER BY d’une requête.
  
## <a name="examples"></a>Exemples  
L'exemple suivant crée, dans une table, une colonne calculée qui applique la fonction `TERTIARY_WEIGHTS` aux valeurs d'une colonne de type `char`.
  
```sql
CREATE TABLE TertColTable  
(Col1 char(15) COLLATE SQL_Latin1_General_Pref_CP437_CI_AS,  
Col2 AS TERTIARY_WEIGHTS(Col1));  
GO   
```  
  
## <a name="see-also"></a>Voir aussi
[ORDER BY, clause for &#40; Transact-SQL &#41;](../../t-sql/queries/select-order-by-clause-transact-sql.md)
  
  
