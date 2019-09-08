---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783448"
---
# <a name="ole-db-schema-collections"></a>Kolekcje schematów OLE DB
W tej sekcji omówiono obsługę kolekcji schematów dla OLE DB dostawców dla Microsoft SQL Server, Oracle i Microsoft Jet.  
  
## <a name="microsoft-sql-server-ole-db-provider"></a>Dostawca OLE DB Microsoft SQL Server  
 Sterownik OLE DB Microsoft SQL Server obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:  
  
- Tabelę  
  
- Kolumny  
  
- Procedury  
  
- ProcedureParameters  
  
- Wykaz  
  
- Zwiększa  
  
### <a name="tables"></a>Tabelę  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Guid|  
|ZHARMONIZOWAN|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
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
|ZHARMONIZOWAN|String|  
|COLUMN_LCID|Int32|  
|COLUMN_COMPFLAGS|Int32|  
|COLUMN_SORTID|Int32|  
|COLUMN_TDSCOLLATION|Byte[]|  
|IS_COMPUTED|Boolean|  
  
### <a name="procedures"></a>Procedury  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|ZHARMONIZOWAN|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PARAMETER_NAME|String|  
|ORDINAL_POSITION|Int32|  
|PARAMETER_TYPE|Int32|  
|PARAMETER_HASDEFAULT|Boolean|  
|PARAMETER_DEFAULT|String|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|ZHARMONIZOWAN|String|  
|TYPE_NAME|String|  
|LOCAL_TYPE_NAME|String|  
  
### <a name="catalog"></a>Wykaz  
  
|ColumnName|DataType|  
|----------------|--------------|  
|CATALOG_NAME|String|  
|ZHARMONIZOWAN|String|  
  
### <a name="indexes"></a>Zwiększa  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|WPROWADŹ|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚCI|Wartość dziesiętna|  
|PAGE|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="microsoft-oracle-ole-db-provider"></a>Dostawca OLE DB Microsoft Oracle  
 Sterownik programu Microsoft Oracle OLE DB obsługuje następujące wybrane kolekcje schematów oprócz wspólnych kolekcji schematów:  
  
- Tabelę  
  
- Kolumny  
  
- Procedury  
  
- ProcedureColumns  
  
- ProcedureParameters  
  
- Widoki  
  
- Zwiększa  
  
### <a name="tables"></a>Tabelę  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Guid|  
|ZHARMONIZOWAN|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
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
|ZHARMONIZOWAN|String|  
  
### <a name="procedures"></a>Procedury  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|ZHARMONIZOWAN|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="procedurecolumns"></a>ProcedureColumns  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ROWSET_NUMBER|Int64|  
|ORDINAL_POSITION|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
|CHARACTER_MAXIMUM_LENGTH|Int64|  
|CHARACTER_OCTET_LENGTH|Int64|  
|NUMERIC_PRECISION|Int32|  
|NUMERIC_SCALE|Int16|  
|ZHARMONIZOWAN|String|  
|WYSTĘPUJĄ|Int16|  
  
### <a name="views"></a>Widoki  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|ZHARMONIZOWAN|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="indexes"></a>Zwiększa  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|WPROWADŹ|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚCI|Wartość dziesiętna|  
|PAGE|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="microsoft-jet-ole-db-provider"></a>Dostawca OLE DB Microsoft Jet  
 Sterownik programu Microsoft Jet OLE DB obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:  
  
- Tabelę  
  
- Kolumny  
  
- Procedury  
  
- Widoki  
  
- Zwiększa  
  
### <a name="tables"></a>Tabelę  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|TABLE_TYPE|String|  
|TABLE_GUID|Guid|  
|ZHARMONIZOWAN|String|  
|TABLE_PROPID|Int64|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="columns"></a>Kolumny  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|ORDINAL_POSITION|Int64|  
|COLUMN_HASDEFAULT|Boolean|  
|COLUMN_DEFAULT|String|  
|COLUMN_FLAGS|Int64|  
|IS_NULLABLE|Boolean|  
|DATA_TYPE|Int32|  
|TYPE_GUID|Guid|  
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
|ZHARMONIZOWAN|String|  
  
### <a name="procedures"></a>Procedury  
  
|ColumnName|DataType|  
|----------------|--------------|  
|PROCEDURE_CATALOG|String|  
|PROCEDURE_SCHEMA|String|  
|PROCEDURE_NAME|String|  
|PROCEDURE_TYPE|Int16|  
|PROCEDURE_DEFINITION|String|  
|ZHARMONIZOWAN|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="views"></a>Widoki  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|VIEW_DEFINITION|String|  
|CHECK_OPTION|Boolean|  
|IS_UPDATABLE|Boolean|  
|ZHARMONIZOWAN|String|  
|DATE_CREATED|DataGodzina|  
|DATE_MODIFIED|DataGodzina|  
  
### <a name="indexes"></a>Zwiększa  
  
|ColumnName|DataType|  
|----------------|--------------|  
|TABLE_CATALOG|String|  
|TABLE_SCHEMA|String|  
|TABLE_NAME|String|  
|INDEX_CATALOG|String|  
|INDEX_SCHEMA|String|  
|INDEX_NAME|String|  
|PRIMARY_KEY|Boolean|  
|UNIQUE|Boolean|  
|CLUSTERED|Boolean|  
|WPROWADŹ|Int32|  
|FILL_FACTOR|Int32|  
|INITIAL_SIZE|Int32|  
|NULL — Wartości|Int32|  
|SORT_BOOKMARKS|Boolean|  
|AUTO_UPDATE|Boolean|  
|NULL_COLLATION|Int32|  
|ORDINAL_POSITION|Int64|  
|COLUMN_NAME|String|  
|COLUMN_GUID|Guid|  
|COLUMN_PROPID|Int64|  
|SORTOWANIE|Int16|  
|KARDYNALNOŚCI|Wartość dziesiętna|  
|PAGE|Int32|  
|FILTER_CONDITION|String|  
|ZINTEGROWANE|Boolean|  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
