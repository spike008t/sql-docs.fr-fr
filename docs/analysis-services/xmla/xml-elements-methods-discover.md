---
title: Méthode Discover (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 661d3bc1307c9a61e75c313347b1530031eb89f1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods---discover"></a>Découvrir les éléments XML de - méthodes suivantes :
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Récupère les informations, telles que la liste des bases de données disponibles ou des détails concernant un objet spécifique, à partir d’une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les données récupérées avec le **Discover** méthode varie selon les valeurs des paramètres passés à ce dernier.  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis  
  
 **Action SOAP** « urn : schemas-microsoft-com-analysis : découvrir »  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Discover>  
   <RequestType>...</RequestType>  
   <Restrictions>...</Restrictions>  
   <Properties>...</Properties>  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|Aucun|  
|Éléments enfants|[Propriétés](../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md), [RequestType](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md), [Restrictions](../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **Discover** méthode demande les métadonnées sur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instances et les objets. Métadonnées sont retournées à l’aide de la XMLA [ensemble de lignes](../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md) type de données.  
 
> [!TIP] 
> Si vous n’êtes pas familiarisé avec des commandes XML, cliquez sur le modèle de requête XMLA dans le **requête** la barre d’outils dans Management Studio, pour générer la requête et d’ajouter des paramètres. Pour plus d’informations, consultez [Utiliser des modèles Analysis Services dans SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md). 
  
## <a name="example"></a>Exemple  
 Dans l’exemple de code suivant, le client envoie le **Discover** appel pour demander une liste de cubes de la [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] exemple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données :  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>MDSCHEMA_CUBES</RequestType>  
   <Restrictions>  
      <RestrictionList>  
         <CATALOG_NAME>Adventure Works DW Multidimensional 2012</CATALOG_NAME>  
      </RestrictionList>  
   </Restrictions>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Tabular</Format>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML & #40 ; XMLA & #41 ;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [Exécuter la méthode &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)   
 [Méthodes &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods.md)   
 [Éléments XML & #40 ; XMLA & #41 ;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Ensembles de lignes de schéma de Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
