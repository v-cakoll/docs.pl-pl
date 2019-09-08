---
title: Mapowanie typu danych Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783424"
---
# <a name="oracle-data-type-mappings"></a>Mapowanie typu danych Oracle
Poniższa tabela zawiera listę typów danych Oracle i ich mapowania na <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Typ danych Oracle|Typ danych .NET Framework zwracany przez OracleDataReader. GetValue|OracleClient typ danych zwrócony przez OracleDataReader. GetOracleValue|Uwagi|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**DOTYCZĄCE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**DELIKATN**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Ciąg**|<xref:System.Data.OracleClient.OracleLob>||  
|**DNIU**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem dla typu danych **Number** i został zaprojektowany tak, <xref:System.Data.OracleClient.OracleDataReader> aby zwracał wartość **System. Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast wartości zmiennoprzecinkowej. Użycie .NET Frameworkgo typu danych może spowodować przepełnienie.|  
|**CAŁKOWITĄ**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem dla typu danych **Number (38)** i został zaprojektowany tak, <xref:System.Data.OracleClient.OracleDataReader> aby zwracał wartość **System. Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast wartości całkowitej. Użycie .NET Frameworkgo typu danych może spowodować przepełnienie.|  
|**INTERWAŁ OD ROKU DO MIESIĄCA**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERWAŁ OD DNIA DO SEKUNDY**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**DŁUGO**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**DŁUGI NIEPRZETWORZONY**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Ciąg**|<xref:System.Data.OracleClient.OracleLob>||  
|**LICZBA**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Użycie .NET Frameworkgo typu danych może spowodować przepełnienie.|  
|**NVARCHAR2**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**WSKAŹNIK REF**|||Typ danych **kursora ref** firmy Oracle nie jest obsługiwany przez <xref:System.Data.OracleClient.OracleDataReader> obiekt.|  
|**WŁAŚCIWOŚĆ**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**ZNACZNIK CZASU**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SYGNATURA CZASOWA Z LOKALNĄ STREFĄ CZASOWĄ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SYGNATURA CZASOWA ZE STREFĄ CZASOWĄ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**LICZBA CAŁKOWITA BEZ ZNAKU**|**Liczba**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem dla typu danych **Number (38)** i został zaprojektowany tak, <xref:System.Data.OracleClient.OracleDataReader> aby zwracał wartość **System. Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast niepodpisanej wartości całkowitej. Użycie .NET Frameworkgo typu danych może spowodować przepełnienie.|  
|**VARCHAR2**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
  
 W poniższej tabeli przedstawiono typy danych Oracle i typy danych .NET Framework (**System. Data. DbType** i <xref:System.Data.OracleClient.OracleType>), które mają być używane podczas wiązania ich jako parametry.  
  
|Typ danych Oracle|Wyliczenie DbType do powiązania jako parametr|Wyliczenie OracleType do powiązania jako parametr|Uwagi|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**DOTYCZĄCE**||**BFile**|W **przypadku programu Oracle** można powiązać **tylko parametr bInformacje** . Program .NET Dostawca danych for Oracle nie konstruuje się automatycznie, jeśli spróbujesz powiązać wartość inną niż**bInformacje** , taką jak **Byte []** lub <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Obiekt blob**|Oracle pozwala tylko na powiązanie **obiektu BLOB** jako parametru **obiektu BLOB** . Program .NET Dostawca danych for Oracle nie konstruuje się automatycznie, jeśli spróbujesz powiązać wartość inną niż**obiekt BLOB** , taką jak **Byte []** lub <xref:System.Data.OracleClient.OracleBinary>.|  
|**DELIKATN**|**AnsiStringFixedLength**|**Delikatn**||  
|**CLOB**||**Clob**|Firma Oracle umożliwia powiązanie **obiektów CLOB** jako parametru **obiektów CLOB** . Program .NET Dostawca danych for Oracle nie konstruuje go automatycznie, jeśli podejmiesz próbę powiązania wartości innej niż**obiektów CLOB** , takiej jak **System. String** lub <xref:System.Data.OracleClient.OracleString>.|  
|**DNIU**|**DateTime**|**DateTime**||  
|**FLOAT**|**Pojedyncza, podwójna, dziesiętna**|**Float, Double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Określa **System. Data. DbType** i <xref:System.Data.OracleClient.OracleType>.|  
|**CAŁKOWITĄ**|**Wartość =, Int16, Int32, Int64, Decimal**|**Wartość =, Int16, Int32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Określa **System. Data. DbType** i <xref:System.Data.OracleClient.OracleType>.|  
|**INTERWAŁ OD ROKU DO MIESIĄCA**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType>jest dostępny tylko w przypadku korzystania z oprogramowania klienckiego Oracle 9i i serwera.|  
|**INTERWAŁ OD DNIA DO SEKUNDY**|**Obiekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType>jest dostępny tylko w przypadku korzystania z oprogramowania klienckiego Oracle 9i i serwera.|  
|**DŁUGO**|**AnsiString**|**LongVarChar**||  
|**DŁUGI NIEPRZETWORZONY**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Firma Oracle umożliwia powiązanie **NCLOB** jako parametru **NCLOB** . Program .NET Dostawca danych for Oracle nie konstruuje go automatycznie, jeśli podejmiesz próbę powiązania wartości innej niż**NCLOB** , takiej jak **System. String** lub <xref:System.Data.OracleClient.OracleString>.|  
|**LICZBA**|**VarNumeric**|**Liczba**||  
|**NVARCHAR2**|**Ciąg**|**NVarChar**||  
|**RAW**|**Binary**|**Surowców**||  
|**WSKAŹNIK REF**||**Kursor**|Aby uzyskać więcej informacji, zobacz [kursory ref Oracle](oracle-ref-cursors.md).|  
|**WŁAŚCIWOŚĆ**|**AnsiString**|**Właściwość**||  
|**ZNACZNIK CZASU**|**DateTime**|**Znacznik czasu**|<xref:System.Data.OracleClient.OracleType>jest dostępny tylko w przypadku korzystania z oprogramowania klienckiego Oracle 9i i serwera.|  
|**SYGNATURA CZASOWA Z LOKALNĄ STREFĄ CZASOWĄ**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType>jest dostępny tylko w przypadku korzystania z oprogramowania klienckiego Oracle 9i i serwera.|  
|**SYGNATURA CZASOWA ZE STREFĄ CZASOWĄ**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType>jest dostępny tylko w przypadku korzystania z oprogramowania klienckiego Oracle 9i i serwera.|  
|**LICZBA CAŁKOWITA BEZ ZNAKU**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>Określa **System. Data. DbType** i <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Wartości InputOutput**, **Output**i **ReturnValue** **ParameterDirection** używane przez <xref:System.Data.OracleClient.OracleParameter.Value%2A> Właściwość obiektusą.NETFrameworktypamidanych,chybażewartośćwejściowajesttypemdanychOracle(dla<xref:System.Data.OracleClient.OracleParameter> <xref:System.Data.OracleClient.OracleNumber> przykład lub<xref:System.Data.OracleClient.OracleString>). Nie ma to zastosowania do typów danych **kursora ref**, **bInformacje**i **LOB** .  
  
## <a name="see-also"></a>Zobacz także

- [Oracle i ADO.NET](oracle-and-adonet.md)
- [Omówienie ADO.NET](ado-net-overview.md)
