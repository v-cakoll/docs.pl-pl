---
title: Mapowanie typu danych OLE DB
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 969433b2582771a0ed57217180c2795f9359956f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783484"
---
# <a name="ole-db-data-type-mappings"></a>Mapowanie typu danych OLE DB
W poniższej tabeli przedstawiono wywnioskowany typ .NET Framework dla typów danych z .NET Framework Dostawca danych dla obiektów ADO i OLE DB (<xref:System.Data.OleDb>). Wymienione metody <xref:System.Data.OleDb.OleDbDataReader> dostępu są również wyświetlane.  
  
|Typ ADO|Typ OLE DB|Typ programu .NET Framework|Metoda dostępu typu .NET Framework|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString ()|  
|adChapter|DBTYPE_HCHAPTER|Obsługiwane przez `DataReader`. Zobacz [pobieranie danych za pomocą elementu DataReader](retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|String|GetString ()|  
|adCurrency|DBTYPE_CY|Wartość dziesiętna|GetDecimal()|  
|adDate|DBTYPE_DATE|DataGodzina|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DataGodzina|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DataGodzina|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DataGodzina|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Wartość dziesiętna|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException —|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DataGodzina|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Obiekt|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32 ()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Obiekt|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Wartość dziesiętna|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Obiekt|GetValue()|  
|adSingle|DBTYPE_R4|Single|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16 ()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Obiekt|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString ()|  
|adUserDefined|DBTYPE_UDT|nieobsługiwane||  
|adVarNumeric|DBTYPE_VARNUMERIC|nieobsługiwane||  
  
 \*W przypadku typów `DBTYPE_IUNKNOWN` OLE DB i `DBTYPE_IDISPATCH`odwołanie do obiektu jest zorganizowanym reprezentacją wskaźnika.  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Omówienie ADO.NET](ado-net-overview.md)
