---
title: "Kolekcje schematów OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a>Kolekcje schematów OLE DB
W tej sekcji omówiono obsługi kolekcji schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Dostawca programu Microsoft SQL Server OLE DB  
 Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureParameters  
  
-   Katalogu  
  
-   Indeksy  
  
### <a name="tables"></a>Tabele  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identyfikator GUID|  
|OPIS ELEMENTU|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|OPIS ELEMENTU|String|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte]|  
|IS_COMPUTED|Boolean|  
  
### <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|NAZWA_PARAMETRU|String|  
|ORDINAL_POSITION|Int32|  
|TYP_PARAMETRU|Int32|  
|PARAMETER_HASDEFAULT|Boolean|  
|PARAMETER_DEFAULT|String|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|OPIS ELEMENTU|String|  
|TYPE_NAME|String|  
|LOCAL_TYPE_NAME|String|  
  
### <a name="catalog"></a>Katalogu  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|CATALOG_NAME|String|  
|OPIS ELEMENTU|String|  
  
### <a name="indexes"></a>Indeksy  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIKATOWE|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚĆ|Wartość dziesiętna|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Dostawca programu Microsoft Oracle OLE DB  
 Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   ProcedureColumns  
  
-   ProcedureParameters  
  
-   Widoki  
  
-   Indeksy  
  
### <a name="tables"></a>Tabele  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identyfikator GUID|  
|OPIS ELEMENTU|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|OPIS ELEMENTU|String|  
  
### <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|OPIS ELEMENTU|String|  
|PRZECIĄŻENIA|Int16|  
  
### <a name="views"></a>Widoki  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="indexes"></a>Indeksy  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIKATOWE|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚĆ|Wartość dziesiętna|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Dostawca programu Microsoft Jet OLE DB  
 Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:  
  
-   Tabele  
  
-   Kolumny  
  
-   Procedury  
  
-   Widoki  
  
-   Indeksy  
  
### <a name="tables"></a>Tabele  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Identyfikator GUID|  
|OPIS ELEMENTU|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Identyfikator GUID|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|DATETIME_PRECISION|Int64|  
|CHARACTER_SET_CATALOG|String|  
|CHARACTER_SET_SCHEMA|String|  
|CHARACTER_SET_NAME|String|  
|COLLATION_CATALOG|String|  
|COLLATION_SCHEMA|String|  
|COLLATION_NAME|String|  
|DOMAIN_CATALOG|String|  
|DOMAIN_SCHEMA|String|  
|DOMAIN_NAME|String|  
|OPIS ELEMENTU|String|  
  
### <a name="procedures"></a>Procedury  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="views"></a>Widoki  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|OPIS ELEMENTU|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="indexes"></a>Indeksy  
  
|Element columnName|Typ danych|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIKATOWE|Boolean|  
|CLUSTERED|Boolean|  
|TYP|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Identyfikator GUID|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚĆ|Wartość dziesiętna|  
|STRONY|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
