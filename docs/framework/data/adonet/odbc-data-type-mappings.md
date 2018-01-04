---
title: Mapowanie typu danych ODBC
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43c35d32-831d-480f-a150-78f7e869d17f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f6f4e63b731f4e8088e86766e258f77cdd0eeff9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-data-type-mappings"></a>Mapowanie typu danych ODBC
W poniższej tabeli przedstawiono wnioskowany [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu dla typów danych z dostawcy danych programu .NET Framework dla ODBC (<xref:System.Data.Odbc>). Metody dostępu typu dla <xref:System.Data.Odbc.OdbcDataReader> są także wyświetlone.  
  
|Typ ODBC|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]Typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]typizowane metody dostępu|  
|---------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|SQL_BIGINT|Int64|GetInt64()|  
|SQL_BINARY|Byte]|Metody GetBytes()|  
|SQL_BIT|Boolean|GetBoolean()|  
|SQL_CHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_DECIMAL|Wartość dziesiętna|GetDecimal()|  
|SQL_DOUBLE|Double|GetDouble()|  
|SQL_GUID|Identyfikator GUID|GetGuid()|  
|SQL_INTEGER|Int32|GetInt32()|  
|SQL_LONG_VARCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_LONGVARBINARY|Byte]|Metody GetBytes()|  
|SQL_NUMERIC|Wartość dziesiętna|GetDecimal()|  
|SQL_REAL|Single|GetFloat()|  
|SQL_SMALLINT|Int16|GetInt16()|  
|SQL_TINYINT|Byte|GetByte()|  
|SQL_TYPE_TIMES|DataGodzina|GetDateTime()|  
|SQL_TYPE_TIMESTAMP|DataGodzina|GetDateTime()|  
|SQL_VARBINARY|Byte]|Metody GetBytes()|  
|SQL_WCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_WLONGVARCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
|SQL_WVARCHAR|String<br /><br /> CHAR]|GetString()<br /><br /> GetChars()|  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
