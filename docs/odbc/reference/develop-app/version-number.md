---
title: "Numéro de version | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2d075df527e85173d0e3ca7c0a7f22ad5b27e6ac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="version-number"></a>Numéro de version
Il existe plusieurs versions d’ODBC, chacun avec différentes fonctionnalités. Une application détermine qui prennent en charge ODBC version du Gestionnaire de pilotes et un pilote spécifique en appelant **SQLGetInfo** avec les options SQL_ODBC_VER et SQL_DRIVER_ODBC_VER.