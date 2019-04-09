---
title: Mapowanie typu danych OLE DB
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 09fab7c5df99ffdb0aef6d32a8ad5ca1ed446d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100590"
---
# <a name="ole-db-data-type-mappings"></a>Mapowanie typu danych OLE DB
W poniższej tabeli przedstawiono wywnioskowane [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu dla typów danych od dostawcy danych programu .NET Framework dla ADO i OLE DB (<xref:System.Data.OleDb>). Metody typizowane metody dostępu dla <xref:System.Data.OleDb.OleDbDataReader> są również wymienione.  
  
|Typ ADO|Typ OLE DB|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] — typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typizowane metody dostępu|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|W wersjach zapoznawczych `DataReader`. Zobacz [pobieraniu danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Wartość dziesiętna|GetDecimal()|  
|adDate|DBTYPE_DATE|DataGodzina|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DataGodzina|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DataGodzina|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DataGodzina|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Wartość dziesiętna|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DataGodzina|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Obiekt|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Obiekt|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Wartość dziesiętna|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Obiekt|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Obiekt|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString()|  
|adUserDefined|DBTYPE_UDT|Nie jest obsługiwany||  
|adVarNumeric|DBTYPE_VARNUMERIC|Nie jest obsługiwany||  
  
 \* Dla typów OLE DB `DBTYPE_IUNKNOWN` i `DBTYPE_IDISPATCH`, odwołanie do obiektu jest organizowane reprezentacji wskaźnika.  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
