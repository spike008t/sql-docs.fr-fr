---
title: "L’insertion en bloc (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BULK_TSQL
- BULK INSERT
- BULK_INSERT_TSQL
- BULK
dev_langs:
- TSQL
helpviewer_keywords:
- tables [SQL Server], importing data into
- inserting files
- views [SQL Server], importing data into
- BULK INSERT statement
- views [SQL Server], exporting data from
- importing data, bulk import
- bulk importing [SQL Server], BULK INSERT statement
- file importing [SQL Server]
ms.assetid: be3984e1-5ab3-4226-a539-a9f58e1e01e2
caps.latest.revision: 153
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80b16fd446ff72c6a673a576d9a8deb9514be8b2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="bulk-insert-transact-sql"></a>BULK INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Importe un fichier de données dans une table ou vue de base de données dans un format spécifié par l'utilisateur dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BULK INSERT   
   [ database_name . [ schema_name ] . | schema_name . ] [ table_name | view_name ]   
      FROM 'data_file'   
     [ WITH   
    (   
   [ [ , ] BATCHSIZE = batch_size ]   
   [ [ , ] CHECK_CONSTRAINTS ]   
   [ [ , ] CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ [ , ] DATAFILETYPE =   
      { 'char' | 'native'| 'widechar' | 'widenative' } ]   
   [ [ , ] DATASOURCE = 'data_source_name' ]
   [ [ , ] ERRORFILE = 'file_name' ]
   [ [ , ] ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ [ , ] FIRSTROW = first_row ]   
   [ [ , ] FIRE_TRIGGERS ]   
   [ [ , ] FORMATFILE_DATASOURCE = 'data_source_name' ]
   [ [ , ] KEEPIDENTITY ]   
   [ [ , ] KEEPNULLS ]   
   [ [ , ] KILOBYTES_PER_BATCH = kilobytes_per_batch ]   
   [ [ , ] LASTROW = last_row ]   
   [ [ , ] MAXERRORS = max_errors ]   
   [ [ , ] ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) ]   
   [ [ , ] ROWS_PER_BATCH = rows_per_batch ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
   [ [ , ] TABLOCK ]   

   -- input file format options
   [ [ , ] FORMAT = 'CSV' ]
   [ [ , ] FIELDQUOTE = 'quote_characters']
   [ [ , ] FORMATFILE = 'format_file_path' ]   
   [ [ , ] FIELDTERMINATOR = 'field_terminator' ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
    )]   
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Est le nom de la base de données dans laquelle réside la table ou vue spécifiée. S'il n'est pas spécifié, la base de données actuelle est utilisée.  
  
 *schema_name*  
 Nom du schéma de la table ou de la vue. *schema_name* est facultatif si le schéma par défaut pour l’utilisateur qui effectue l’opération d’importation en bloc est le schéma de la table ou vue spécifiée. Si *schéma* n’est pas spécifié et le schéma par défaut de l’utilisateur qui effectue l’opération d’importation en bloc est différent de la table ou vue spécifiée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un message d’erreur et l’opération d’importation en bloc est annulée.  
  
 *table_name*  
 Nom de la table ou de la vue dans laquelle les données doivent être importées en bloc. Seules des vues dans lesquelles toutes les colonnes font référence à la même table de base peuvent être utilisées. Pour plus d’informations sur les restrictions pour le chargement des données dans les vues, consultez [INSERT &#40; Transact-SQL &#41; ](../../t-sql/statements/insert-transact-sql.md).  
  
 **'** *data_file* **'**  
 Chemin d'accès complet du fichier de données contenant les données à importer dans la table ou la vue spécifiée. BULK INSERT peut importer des données à partir d'un disque (réseau, disquette, disque dur, etc.).   
 
 *data_file* doit spécifier un chemin d’accès valide à partir du serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution. Si *data_file* est à une distance de fichiers, spécifiez le nom UNC Universal Naming Convention (). Un nom UNC présente la forme \\ \\ *Nom_système*\\*nom_partage*\\*chemin d’accès*\\*nom de fichier*. Par exemple, `\\SystemX\DiskZ\Sales\update.txt`.   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP1.1, le data_file peut être dans le stockage blob Azure.

**'** *data_source_name* **'**   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Une source de données externe nommé pointe vers l’emplacement de stockage d’objets Blob Azure du fichier qui sera importé. La source de données externe doit être créée à l’aide de la `TYPE = BLOB_STORAGE` option ajoutée dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).    
  
 BATCHSIZE  **=**  *batch_size*  
 Indique le nombre de lignes contenues dans un lot. Chaque lot est copié sur le serveur comme une transaction unique. En cas d'échec, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide ou annule la transaction pour chaque lot. Par défaut, toutes les données du fichier spécifié constituent un seul lot. Pour plus d'informations sur les performances, consultez la section « Notes » plus loin dans cette rubrique.  
  
 CHECK_CONSTRAINTS  
 Spécifie que toutes les contraintes sur la table ou vue cible doivent être vérifiées pendant l'opération d'importation en bloc. Sans l’option CHECK_CONSTRAINTS, toutes les contraintes CHECK et FOREIGN KEY sont ignorées, et après l’opération, la contrainte sur la table est marquée comme non approuvée.  
  
> [!NOTE]  
>  Contraintes UNIQUE et PRIMARY KEY sont toujours appliquées. Lors de l'importation dans une colonne de type character définie avec une contrainte NOT NULL, BULK INSERT insère une chaîne vide si aucune valeur n'est spécifiée dans le fichier texte.  
  
 À un certain moment, il devient nécessaire d'examiner les contraintes définies sur l'ensemble de la table. Si la table est vide avant l’opération d’importation en bloc, le coût de la revalidation de la contrainte peut dépasser le coût de l’application des contraintes CHECK aux données incrémentielles.  
  
 Il peut notamment convenir de désactiver les contraintes (comportement par défaut) si les données d'entrée contiennent des lignes qui violent des contraintes. Une fois les contraintes CHECK désactivées, vous pouvez importer les données, puis utiliser les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] pour supprimer les données non valides.  
  
> [!NOTE]  
>  L'option MAXERRORS ne s'applique pas à la vérification des contraintes.  
  
 Page de codes  **=**  { **'**ACP**'** | **'**OEM**'** | **'**RAW**'** | **'***code_page***'** }  
 Indique la page de codes des données dans le fichier. Page de codes s’applique uniquement si les données contiennent **char**, **varchar**, ou **texte** colonnes avec des valeurs de caractère supérieurs à **127** ou inférieur à **32**.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]recommande de spécifier un nom de classement pour chaque colonne dans un [fichier de format](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).  
  
|Valeur CODEPAGE| Description|  
|--------------------|-----------------|  
|ACP|Colonnes de **char**, **varchar**, ou **texte** type de données sont converties à partir de la [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)] / [!INCLUDE[msCoName](../../includes/msconame-md.md)] page de codes Windows (ISO 1252) à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] page de codes.|  
|OEM (valeur par défaut)|Colonnes de **char**, **varchar**, ou **texte** type de données sont converties à partir de la page de codes OEM du système pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] page de codes.|  
|RAW|Aucune conversion d'une page de codes vers une autre ne se produit ; ceci est l'option la plus rapide.|  
|*code_page*|Numéro de la page de codes, par exemple 850.<br /><br /> **\*\*Important \* \***  Versions antérieures à [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prennent pas en charge la page de codes 65001 (encodage UTF-8).|  
  
 DATAFILETYPE  **=**  { **'char'** | **'native'** | **'widechar'** | **'widenative'** }  
 Spécifie que BULK INSERT réalise l'opération d'importation en utilisant la valeur définie pour le type de fichier de données.  
  
|Valeur DATAFILETYPE|Toutes les données représentées dans :|  
|------------------------|------------------------------|  
|**char** (par défaut)|Format caractères.<br /><br /> Pour plus d’informations, consultez [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).|  
|**natif**|Types de données (base de données) natif. Créer le fichier de données en mode natif par les données à partir de l’importation en bloc [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de la **bcp** utilitaire.<br /><br /> La valeur native offre de meilleures performances que la valeur char.<br /><br /> Pour plus d’informations, consultez [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).|  
|**widechar**|Caractères Unicode.<br /><br /> Pour plus d’informations, consultez [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).|  
|**widenative**|Types de données natifs (base de données), sauf dans **char**, **varchar**, et **texte** colonnes, dans laquelle les données sont stockées au format Unicode. Créer le **widenative** fichier de données en bloc à l’importation de données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de la **bcp** utilitaire.<br /><br /> Le **widenative** valeur offre de meilleures performances pour **widechar**. Si le fichier de données contient [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)] caractères étendus, spécifiez **widenative**.<br /><br /> Pour plus d’informations, consultez [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).|  
  
  ERRORFILE **='***nom_fichier***'**  
 Fichier utilisé pour collecter les lignes comportant des erreurs de mise en forme et impossibles à convertir en un ensemble de lignes OLE DB. Ces lignes sont copiées « en l'état » du fichier de données vers ce fichier d'erreur.  
  
 Le fichier d'erreur est créé lors de l'exécution de la commande. Une erreur se produit si le fichier existe déjà. De plus, un fichier de contrôle portant l'extension .ERROR.txt est créé. Il fait référence à chacune des lignes du fichier d'erreur et propose un diagnostic. Dès que les erreurs ont été corrigées, les données peuvent être chargées.   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], le `error_file_path` peut se trouver dans le stockage d’objets blob Azure.

'errorfile_data_source_name'   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
Une source de données externe nommé pointe vers l’emplacement de stockage d’objets Blob Azure du fichier d’erreur contenant des erreurs détectées lors de l’importation. La source de données externe doit être créée à l’aide de la `TYPE = BLOB_STORAGE` option ajoutée dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
 
 FIRSTROW  **=**  *first_row*  
 Numéro de la première ligne à charger. La valeur par défaut est la première ligne du fichier de données spécifié. FIRSTROW commence à 1.  
  
> [!NOTE]  
>  L'attribut FIRSTROW n'est pas destiné à ignorer les en-têtes de colonnes. Le fait d'ignorer des en-têtes n'est pas pris en charge par l'instruction BULK INSERT. Si des lignes sont ignorées, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] examine uniquement les marques de fin de champ et ne valide pas les données figurant dans les champs des lignes ignorées.  
  
 FIRE_TRIGGERS  
 Spécifie que tous les déclencheurs d'insertion définis sur la table de destination seront exécutés au cours de l'opération d'importation en bloc. Si des déclencheurs sont définis pour les opérations INSERT réalisées sur la table cible, ils sont activés à la fin de chaque lot.  
  
 Si FIRE_TRIGGERS n’est pas spécifié, aucun déclencheur d’insertion s’exécuter.  

FORMATFILE_DATASOURCE  **=**  'data_source_name'   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 1.1.   
Une source de données externe nommé pointe vers l’emplacement de stockage d’objets Blob Azure de fichier de format qui définit le schéma de données importées. La source de données externe doit être créée à l’aide de la `TYPE = BLOB_STORAGE` option ajoutée dans [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Pour plus d’informations, consultez [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
 KEEPIDENTITY  
 Indique que la ou les valeurs d'identité figurant dans le fichier de données importé doivent être utilisées dans la colonne d'identité. Si KEEPIDENTITY n'est pas spécifié, les valeurs d'identité de cette colonne sont vérifiées mais pas importées, et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte automatiquement des valeurs uniques en fonction de la valeur initiale et d'un incrément spécifié lors de la création de la table. Si le fichier de données ne contient pas de valeurs pour la colonne d'identité de la table ou de la vue, utilisez un fichier de format pour indiquer que la colonne d'identité ne doit pas être prise en compte lors de l'importation des données ; dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attribue automatiquement des valeurs uniques à la colonne. Pour plus d’informations, consultez [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md).  
  
 Pour plus d’informations sur la conservation identifier les valeurs, consultez [conserver identité valeurs lors de l’importation des données en bloc &#40; SQL Server &#41; ](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md).  
  
 KEEPNULLS  
 Spécifie que pendant l'importation en bloc les colonnes vides doivent conserver la valeur NULL au lieu d'insérer des valeurs par défaut dans ces colonnes. Pour plus d’informations, consultez [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).  
  
 KILOBYTES_PER_BATCH  **=**  *kilobytes_per_batch*  
 Spécifie le nombre approximatif de kilo-octets (Ko) de données par lot en tant que *kilobytes_per_batch*. Par défaut, KILOBYTES_PER_BATCH est inconnu. Pour plus d'informations sur les performances, consultez la section « Notes » plus loin dans cette rubrique.  
  
 LASTROW**=***last_row*  
 Numéro de la dernière ligne à charger. La valeur par défaut est 0, c'est-à-dire la dernière ligne du fichier de données spécifié.  
  
 MAXERRORS  **=**  *max_errors*  
 Nombre maximal d'erreurs de syntaxe tolérées dans les données avant l'annulation de l'importation en bloc. Chaque ligne ne pouvant pas être importée par l'opération d'importation en bloc est ignorée et compte comme une erreur. Si *max_errors* n’est pas spécifié, la valeur par défaut est 10.  
  
> [!NOTE]  
>  L’option MAX_ERRORS ne s’applique pas aux vérifications de contraintes ou à la conversion **money** et **bigint** des types de données.  
  
 COMMANDE ({ *colonne* [ASC | DESC]} [ **,**... *n* ] )  
 Indique l'ordre de tri des données dans le fichier. Les performances de l'importation en bloc sont améliorées si les données importées sont triées en fonction de l'index cluster de la table, le cas échéant. Si le fichier de données est trié dans un autre ordre (c'est-à-dire pas dans l'ordre d'une clé d'index cluster) ou s'il n'y a pas d'index cluster dans la table, la clause ORDER est ignorée. Les noms de colonnes fournis doivent être des noms de colonnes valides dans la table de destination. Par défaut, l'opération d'insertion en bloc considère que le fichier de données n'est pas ordonné. Pour une importation en bloc optimisée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide également le fait que les données importées sont triées.  
  
 *n*  
 Espace réservé qui indique que plusieurs colonnes peuvent être spécifiées.  
  
 ROWS_PER_BATCH  **=**  *rows_per_batch*  
 Nombre approximatif de lignes de données que compte le fichier de données.  
  
 Par défaut, toutes les données du fichier de données sont envoyées au serveur en une seule transaction, et le nombre de lignes du lot est inconnu de l'optimiseur de requête. Si vous spécifiez ROWS_PER_BATCH (valeur > 0), le serveur utilise cette valeur pour optimiser l'importation en bloc. La valeur spécifiée pour ROWS_PER_BATCH devrait correspondre à peu près au nombre réel de lignes. Pour plus d'informations sur les performances, consultez la section « Notes » plus loin dans cette rubrique.  
  
 
 TABLOCK  
 Spécifie qu'un verrou de niveau table est acquis pour la durée de l'opération d'importation en bloc. Une table peut être chargée simultanément par plusieurs clients à condition qu'elle ne comporte pas d'index et que TABLOCK soit spécifié. Par défaut, le comportement du verrouillage est déterminé par l'option **table lock on bulk load**. En verrouillant la table pendant la durée de l'importation en bloc, vous réduisez la contention de verrouillage et augmentez considérablement, dans certains cas, les performances. Pour plus d'informations sur les performances, consultez la section « Notes » plus loin dans cette rubrique.  
  
 Pour les index columnstore. le comportement de verrouillage est différent, car il est divisé en interne dans plusieurs ensembles de lignes.  Chaque thread charge des données exclusivement dans chaque ensemble de lignes en prenant un verrou X sur l’ensemble de lignes permettant le chargement de données en parallèle avec les sessions de chargement de données simultanées. L’utilisation de l’option TABLOCK entraîne un thread peut prendre un verrou X sur la table (contrairement aux verrous BU pour des ensembles de lignes traditionnel), qui empêche les autres threads simultanés pour charger des données simultanément.  

### <a name="input-file-format-options"></a>Options de format de fichier d’entrée
  
FORMAT  **=**  « CSV »   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Spécifie un fichier de valeurs séparées par des virgules qui est conforme à la [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

FIELDQUOTE  **=**  'field_quote'   
**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Spécifie un caractère qui sera utilisé comme le caractère de guillemet dans le fichier CSV. Si non spécifié, le caractère guillemet (") servira en tant que le caractère guillemet tel que défini dans le [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.
  
 FORMATFILE **='***chemin_fichier_format***'**  
 Spécifie le chemin complet au fichier de format. Un fichier de format décrit le fichier de données qui contient les réponses stockées créées à l’aide de la **bcp** utilitaire sur la même table ou vue. Le fichier de format doit être utilisé dans les contextes suivants :  
  
-   Le fichier de données contient plus ou moins de colonnes que la table ou la vue.  
  
-   Les colonnes sont ordonnées différemment.  
  
-   Les délimiteurs de colonne sont différents.  
  
-   Le format des données présente d'autres changements. Fichiers de format sont généralement créées à l’aide de la **bcp** utilitaire et modifié avec un éditeur de texte en fonction des besoins. Pour plus d’informations, consultez [bcp Utility](../../tools/bcp-utility.md).  

**S’applique à :** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, la chemin_fichier_format peut être dans le stockage blob Azure.

 FIELDTERMINATOR **='***indicateur_fin_de_champ***'**  
 Indicateur de fin de champ à utiliser pour **char** et **widechar** des fichiers de données. La marque de fin de champ par défaut est le caractère de tabulation (\t). Pour plus d’informations, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  

 ROWTERMINATOR **='***indicateur_fin_de_ligne***'**  
 Indicateur de fin de ligne à utiliser pour **char** et **widechar** des fichiers de données. Fin de ligne par défaut est **\r\n** (caractère de saut de ligne).  Pour plus d’informations, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  

  
## <a name="compatibility"></a>Compatibilité  
 BULK INSERT impose une validation et un contrôle stricts des données lues dans un fichier qui pourraient faire échouer les scripts existants si ces derniers s'exécutent sur des données non valides. Par exemple, BULK INSERT vérifie que :  
  
-   La représentation native des **float** ou **réel** des types de données sont valides.  
  
-   les données Unicode comportent un nombre d'octets pair.  
  
## <a name="data-types"></a>Types de données  
  
### <a name="string-to-decimal-data-type-conversions"></a>Conversion du type de données String en type Decimal  
 Les conversions de types de données de chaîne décimal utilisées dans BULK INSERT suivent les mêmes règles que les [!INCLUDE[tsql](../../includes/tsql-md.md)] [convertir](../../t-sql/functions/cast-and-convert-transact-sql.md) fonction, qui rejette les chaînes représentant des valeurs numériques qui utilisent la notation scientifique. BULK INSERT traite donc ce genre de chaînes comme des valeurs non valides et signale des erreurs de conversion.  
  
 Pour contourner ce problème, utilisez un fichier de format pour la notation scientifique importation en bloc de **float** des données dans une colonne décimale. Dans le fichier de format, décrire de façon explicite la colonne en tant que **réel** ou **float** données. Pour plus d’informations sur ces types de données, consultez [float et real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
> [!NOTE]  
>  Fichiers de format représentent **réel** données en tant que le **SQLFLT4** type de données et **float** données en tant que le **SQLFLT8** type de données. Pour plus d’informations sur les fichiers de format non-XML, consultez [spécifier le Type de fichier de stockage à l’aide de bcp &#40; SQL Server &#41; ](../../relational-databases/import-export/specify-file-storage-type-by-using-bcp-sql-server.md).  
  
#### <a name="example-of-importing-a-numeric-value-that-uses-scientific-notation"></a>Exemple d'importation d'une valeur numérique qui utilise la notation scientifique  
 Cet exemple utilise la table suivante :  
  
```  
CREATE TABLE t_float(c1 float, c2 decimal (5,4));  
```  
  
 L'utilisateur veut importer des données en bloc dans la table `t_float`. Le fichier de données, C:\t_float-c.dat, contient la notation scientifique **float** données ; par exemple :  
  
```  
8.0000000000000002E-28.0000000000000002E-2  
```  
  
 Cependant, l'instruction BULK INSERT ne peut pas importer ces données directement dans `t_float`, car sa deuxième colonne, `c2`, utilise le type de données `decimal`. Un fichier de format est donc nécessaire, Le fichier de format doit mapper la notation scientifique **float** les données au format décimal de colonne `c2`.  
  
 Le fichier de format suivant utilise le type de données `SQLFLT8` pour établir la correspondance entre le deuxième champ de données et la deuxième colonne :  
  
 `<?xml version="1.0"?>`  
  
 `<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">`  
  
 `<RECORD>`  
  
 `<FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="30"/>`  
  
 `<FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="30"/>  </RECORD>  <ROW>`  
  
 `<COLUMN SOURCE="1" NAME="c1" xsi:type="SQLFLT8"/>`  
  
 `<COLUMN SOURCE="2" NAME="c2" xsi:type="SQLFLT8"/>  </ROW> </BCPFORMAT>`  
  
 Si vous voulez opter pour ce fichier de format (avec le nom de fichier `C:\t_floatformat-c-xml.xml`) afin d'importer les données de test dans la table de test, exécutez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante :  
  
```  
BULK INSERT bulktest..t_float  
FROM 'C:\t_float-c.dat' WITH (FORMATFILE='C:\t_floatformat-c-xml.xml');  
GO  
```  
  
### <a name="data-types-for-bulk-exporting-or-importing-sqlxml-documents"></a>Types de données pour l'importation et l'exportation en bloc de documents SQLXML  
 Pour exporter ou importer en bloc des données SQLXML, utilisez l'un des types de données ci-dessous dans votre fichier de format :  
  
|Type de données|Effet|  
|---------------|------------|  
|SQLCHAR ou SQLVARCHAR|Les données sont envoyées dans la page de codes du client ou dans la page de codes impliquée par le classement. L’effet est identique à la propriété DATAFILETYPE **= 'char'** sans spécifier un fichier de format.|  
|SQLNCHAR ou SQLNVARCHAR|Les données sont envoyées au format Unicode. L’effet est identique à la propriété DATAFILETYPE **= 'widechar'** sans spécifier un fichier de format.|  
|SQLBINARY ou SQLVARBIN|Les données sont envoyées sans être converties.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Pour obtenir une comparaison de l'instruction BULK INSERT, de l'instruction INSERT ... Sélectionnez \* OPENROWSET d’instruction et le **bcp** command, consultez [importation et exportation de données &#40; SQL Server &#41; ](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Pour plus d’informations sur la préparation des données pour l’importation en bloc, consultez [préparer des données pour l’exportation en bloc ou une importation &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 L'instruction BULK INSERT peut être exécutée dans une transaction définie par l'utilisateur pour importer des données dans une table ou une vue. Pour utiliser des correspondances multiples pour l'importation en bloc de données, une transaction peut éventuellement spécifier la clause BATCHSIZE dans l'instruction BULK INSERT. Si une transaction sur plusieurs lots est restaurée, chaque lot que la transaction a envoyé à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est restaurée.  
  
## <a name="interoperability"></a>Interopérabilité  
  
### <a name="importing-data-from-a-csv-file"></a>Importation des données d'un fichier CSV  
À partir de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, BULK INSERT prend en charge le format CSV.  
Avant de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, les fichiers de valeurs séparées par des virgules (CSV) ne sont pas gérés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] opérations d’importation en bloc. Toutefois, dans certains cas, un fichier CSV peut être utilisé comme fichier de données pour une importation en bloc de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la configuration requise pour l’importation de données à partir d’un fichier CSV, consultez [préparer des données pour l’exportation en bloc ou une importation &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
## <a name="logging-behavior"></a>Comportement de journalisation  
 Pour savoir à quel moment les opérations d’insertion de ligne effectuées par l’importation en bloc sont consignées dans le journal des transactions, consultez [Conditions requises pour une journalisation minimale dans l’importation en bloc](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
##  <a name="Limitations"></a> Restrictions  
 Lorsque vous utilisez un fichier de format avec BULK INSERT, vous pouvez spécifier jusqu'à 1 024 champs. Il s'agit du nombre maximal de colonnes autorisé dans une table. Si vous utilisez BULK INSERT avec un fichier de données qui contient plus de 1 024 champs, BULK INSERT génère l'erreur 4 822. Le [utilitaire bcp](../../tools/bcp-utility.md) ne pas avoir cette limitation, par conséquent, pour les fichiers de données qui contiennent plus de 1 024 champs, utilisez le **bcp** commande.  
  
## <a name="performance-considerations"></a>Considérations relatives aux performances  
 Si le nombre de pages à vider dans un lot unique dépasse un seuil interne, une analyse complète du pool de mémoires tampons peut s'effectuer afin d'identifier les pages à vider lors de la validation du lot. Cette analyse complète peut nuire aux performances de l'importation en bloc. Le dépassement du seuil interne se produit lorsqu'un pool de mémoires tampons de grande taille est associé à un sous-système d'E/S lent. Pour éviter tout dépassement de mémoire tampon sur les ordinateurs de grande capacité, évitez d'utiliser l'indication TABLOCK (qui entraîne la suppression des optimisations en bloc) ou utilisez une taille de lot plus petite (qui permet de conserver les optimisations en bloc).  
  
 En raison de la diversité des ordinateurs, nous vous recommandons de tester différentes tailles de lot avec votre charge de données pour trouver la solution la plus adaptée.  
  
## <a name="security"></a>Sécurité  
  
### <a name="security-account-delegation-impersonation"></a>Délégation de compte de sécurité (emprunt d'identité)  
 Si un utilisateur a recours à une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le profil de sécurité du compte du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est alors utilisé. Une connexion via l'authentification SQL Server ne peut pas être authentifiée en dehors du moteur de base de données. Par conséquence, lorsqu'une commande BULK INSERT est initiée par une connexion via l'authentification SQL Server, la connexion aux données s'effectue à l'aide du contexte de sécurité du compte du processus SQL Server (compte utilisé par le service de moteur de base de données SQL Server). Pour pouvoir lire les données sources, vous devez octroyer au compte utilisé par le moteur de base de données SQL Server l'accès aux données sources. Par opposition, si un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'est connecté via l'authentification Windows, il peut lire uniquement les fichiers accessibles par le compte d'utilisateur, indépendamment du profil de sécurité du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lors de l’exécution de l’instruction BULK INSERT à l’aide de **sqlcmd** ou **osql**, insérez des données à partir d’un ordinateur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un deuxième ordinateur et en spécifiant un *data_file* sur un troisième ordinateur à l’aide d’un chemin d’accès UNC, vous pouvez recevoir une erreur 4861.  
  
 Pour résoudre cette erreur, utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification et spécifiez un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion qui utilise le profil de sécurité de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de processus, ou configurez Windows pour activer la délégation de compte de sécurité. Pour plus d'informations sur l'activation d'un compte d'utilisateur en vue de son approbation pour la délégation, consultez l'aide de Windows.  
  
 Pour plus d’informations sur cette modification et autres considérations relatives à l’aide de BULK INSERT, consultez [importer en bloc des données par l’utilisation de BULK INSERT ou OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="permissions"></a>Permissions  
 Requiert les autorisations INSERT et ADMINISTER BULK OPERATIONS. De plus, l'autorisation ALTER TABLE est nécessaire si une ou plusieurs des conditions suivantes sont réunies :  
  
-   Des contraintes existent et l'option CHECK_CONSTRAINTS n'est pas spécifiée.  
  
    > [!NOTE]  
    >  La désactivation des contraintes est le comportement par défaut. Pour vérifier les contraintes explicitement, utilisez l'option CHECK_CONSTRAINTS.  
  
-   Des déclencheurs existent et l'option FIRE_TRIGGER n'est pas spécifiée.  
  
    > [!NOTE]  
    >  Par défaut, les déclencheurs ne sont pas activés. Pour activer les déclencheurs explicitement, utilisez l'option FIRE_TRIGGER.  
  
-   Vous utilisez l'option KEEPIDENTITY pour importer une valeur d'identité du fichier de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-pipes-to-import-data-from-a-file"></a>A. Importation des données d'un fichier à l'aide du caractère (|)  
 L'exemple suivant importe des informations détaillées de commande dans la table `AdventureWorks2012.Sales.SalesOrderDetail`, à partir du fichier de données spécifié en utilisant le caractère `|` comme marque de fin de champ et `|\n` comme marque de fin de ligne.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH   
      (  
         FIELDTERMINATOR =' |',  
         ROWTERMINATOR =' |\n'  
      );  
```  
  
### <a name="b-using-the-firetriggers-argument"></a>B. Utilisation de l'argument FIRE_TRIGGERS  
 L'exemple suivant spécifie l'argument `FIRE_TRIGGERS`.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH  
     (  
        FIELDTERMINATOR =' |',  
        ROWTERMINATOR = ':\n',  
        FIRE_TRIGGERS  
      );  
```  
  
### <a name="c-using-line-feed-as-a-row-terminator"></a>C. Utilisation du retour à la ligne comme délimiteur de ligne  
 L'exemple suivant importe un fichier qui utilise le retour à la ligne comme marque de fin de ligne, par exemple une sortie UNIX :  
  
```  
DECLARE @bulk_cmd varchar(1000);  
SET @bulk_cmd = 'BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
FROM ''<drive>:\<path>\<filename>''   
WITH (ROWTERMINATOR = '''+CHAR(10)+''')';  
EXEC(@bulk_cmd);  
```  
  
> [!NOTE]  
>  En raison de la façon dont Microsoft Windows traite les fichiers texte **(\n** qui est automatiquement remplacé par **\r\n)**.  
  
### <a name="d-specifying-a-code-page"></a>D. Spécification d’une page de codes  
 L’exemple suivant montre comment spécifier une page de codes.  
  
```  
BULK INSERT MyTable  
FROM 'D:\data.csv'  
WITH  
( CODEPAGE = '65001',  
    DATAFILETYPE = 'char',  
    FIELDTERMINATOR = ','  
);  
```  
### <a name="e-importing-data-from-a-csv-file"></a>E. L’importation de données à partir d’un fichier CSV   
L’exemple suivant montre comment spécifier un fichier CSV.   
```
BULK INSERT Sales.Invoices
FROM '\\share\invoices\inv-2016-07-25.csv'
WITH (FORMAT = 'CSV'); 
```

### <a name="f-importing-data-from-a-file-in-azure-blob-storage"></a>F. L’importation de données à partir d’un fichier dans le stockage blob Azure   
L’exemple suivant montre comment charger des données à partir d’un fichier csv dans un emplacement de stockage d’objets blob Azure, qui a été configuré en tant que source de données externe. Cela nécessite des informations d’identification d’une étendue de la base de données à l’aide d’une signature d’accès partagé.    

```tsql
BULK INSERT Sales.Invoices
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
     FORMAT = 'CSV'); 
```

Pour terminer `BULK INSERT` des exemples, y compris la configuration de source de données externe, les informations d’identification, consultez [exemples d’accès en bloc à des données dans le stockage d’objets Blob Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
  
### <a name="additional-examples"></a>Autres exemples  
 Autres `BULK INSERT` exemples sont fournis dans les rubriques suivantes :  
  
-   [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Utiliser un fichier de format pour mapper les colonnes d’une table aux champs d’un fichier de données &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Importation et exportation en bloc de données &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [Fichiers de format pour l’importation ou l’exportation de données &#40; SQL Server &#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Préparer les données pour l’exportation en bloc ou importation &#40; SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [sp_tableoption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
