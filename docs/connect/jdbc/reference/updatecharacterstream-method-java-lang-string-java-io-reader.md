---
title: "Méthode updateCharacterStream (java.lang.String, java.io.Reader) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8ec22a9-4bbd-4759-9f21-957304ef3a5e
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4738e48f37f05d60f7568b3706f74396982f2c69
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="updatecharacterstream-method-javalangstring-javaioreader"></a>Méthode updateCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur de flux de caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateCharacterStream(java.lang.String columnLabel,  
                                  java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 A **chaîne** qui contient l’étiquette de colonne.  
  
 *lecteur*  
  
 Un objet de lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateCharacterStream est spécifiée par la méthode updateCharacterStream dans l’interface java.sql.ResultSet.  
  
 Cette méthode passe les caractères Unicode à partir d’un objet lecteur de texte sélectionné et les colonnes binary. Cela inclut toutes les colonnes de texte et **binaire**, **varbinary**, **varbinary (max)**, **image**, et **xml**colonnes, mais pas **udt** colonnes.  
  
 À l’aide de cette méthode pour le **image**, **texte**, et **ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] des types de données peuvent affecter les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode updateCharacterStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  