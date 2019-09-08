---
title: Mapowanie typu danych ODBC
ms.date: 03/30/2017
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
ms.openlocfilehash: 6611ca35ab5e5b44fa9adacfe25593bb4a5b9c44
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783509"
---
# <a name="odbc-data-type-mappings"></a>Mapowanie typu danych ODBC
W poniższej tabeli przedstawiono wywnioskowany typ .NET Framework dla typów danych z .NET Framework Dostawca danych dla ODBC (<xref:System.Data.Odbc>). Wymienione metody <xref:System.Data.Odbc.OdbcDataReader> dostępu są również wyświetlane.  
  
|Typ ODBC|Typ programu .NET Framework|Metoda dostępu typu .NET Framework|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte[]|GetBytes()|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|String<br /><br /> Char []|GetString ()<br /><br /> GetChars()|  
|SQL_DECIMAL|Wartość dziesiętna|GetDecimal()|  
|SQL_DOUBLE|Double|GetDouble()|  
|SQL_GUID|Guid|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32 ()|  
|SQL_LONG_VARCHAR|String<br /><br /> Char []|GetString ()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte[]|GetBytes()|  
|SQL_NUMERIC|Wartość dziesiętna|GetDecimal()|  
|SQL_REAL|Single|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16 ()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DataGodzina|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DataGodzina|GetDateTime()|  
|SQL_VARBINARY|Byte[]|GetBytes()|  
|SQL_WCHAR|String<br /><br /> Char []|GetString ()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|String<br /><br /> Char []|GetString ()<br /><br /> GetChars()|  
|SQL_WVARCHAR|String<br /><br /> Char []|GetString ()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Omówienie ADO.NET](ado-net-overview.md)
