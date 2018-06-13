---
title: Mapowanie typu danych bazy danych OLE
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 4287b125b26bc0c7233f59322c84e2ac27c0c594
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758935"
---
# <a name="ole-db-data-type-mappings"></a>Mapowanie typu danych bazy danych OLE
W poniższej tabeli przedstawiono wnioskowany [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu dla typów danych z dostawcy danych programu .NET Framework dla ADO i OLE DB (<xref:System.Data.OleDb>). Metody dostępu typu dla <xref:System.Data.OleDb.OleDbDataReader> są także wyświetlone.  
  
|Typ ADO|Typ OLE DB|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Typ|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typizowane metody dostępu|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|Obsługiwane za pośrednictwem `DataReader`. Zobacz [pobierania danych przy użyciu elementu DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Wartość dziesiętna|GetDecimal()|  
|adDate|DBTYPE_DATE|DataGodzina|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DataGodzina|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DataGodzina|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DataGodzina|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Wartość dziesiętna|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|Externalexception —|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DataGodzina|GetDateTime()|  
|adGUID|DBTYPE_GUID|Identyfikator GUID|GetGuid()|  
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
|adUserDefined|DBTYPE_UDT|Nieobsługiwane||  
|adVarNumeric|DBTYPE_VARNUMERIC|Nieobsługiwane||  
  
 \* Dla typów OLE DB `DBTYPE_IUNKNOWN` i `DBTYPE_IDISPATCH`, odwołanie do obiektu jest zorganizowanym reprezentacja wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
