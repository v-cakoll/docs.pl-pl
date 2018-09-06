---
title: Mappings1 typu danych Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 9057a19abb1abc22924b5542f06e21a57a36ed94
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856338"
---
# <a name="oracle-data-type-mappings"></a>Mapowanie typu danych Oracle
W poniższej tabeli przedstawiono typy danych Oracle i ich mapowań <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Typ danych Oracle|Typ danych .NET framework zwracanych przez OracleDataReader.GetValue|Typ danych programu OracleClient zwracanych przez OracleDataReader.GetOracleValue|Uwagi|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BPLIK**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Ciąg**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATA**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem dla **numer** typu danych i został zaprojektowany tak, aby <xref:System.Data.OracleClient.OracleDataReader> zwraca **System.Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast wartości zmiennoprzecinkowych. Za pomocą typu danych .NET Framework może spowodować przepełnienie.|  
|**LICZBA CAŁKOWITA**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem dla **NUMBER(38)** typu danych i został zaprojektowany tak, aby <xref:System.Data.OracleClient.OracleDataReader> zwraca **System.Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast wartość całkowitą. Za pomocą typu danych .NET Framework może spowodować przepełnienie.|  
|**INTERWAŁU ROKU DO MIESIĄCA**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERWAŁU DNIA DO SEKUNDY**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**DŁUGI**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**DŁUGI NIEPRZETWORZONE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Ciąg**|<xref:System.Data.OracleClient.OracleLob>||  
|**NUMER**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Za pomocą typu danych .NET Framework może spowodować przepełnienie.|  
|**NVARCHAR2**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** typ danych nie jest obsługiwany przez <xref:System.Data.OracleClient.OracleDataReader> obiektu.|  
|**ROWID**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
|**ZNACZNIK CZASU:**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SYGNATURA CZASOWA PRZY UŻYCIU LOKALNEJ STREFY CZASOWEJ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SYGNATURA CZASOWA ZE STREFĄ CZASOWĄ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**LICZBA CAŁKOWITA BEZ ZNAKU**|**Numer**|<xref:System.Data.OracleClient.OracleNumber>|Ten typ danych jest aliasem dla **NUMBER(38)** typu danych i został zaprojektowany tak, aby <xref:System.Data.OracleClient.OracleDataReader> zwraca **System.Decimal** lub <xref:System.Data.OracleClient.OracleNumber> zamiast nieoznaczoną wartość całkowitą. Za pomocą typu danych .NET Framework może spowodować przepełnienie.|  
|**VARCHAR2**|**Ciąg**|<xref:System.Data.OracleClient.OracleString>||  
  
 W poniższej tabeli przedstawiono typy danych Oracle i typy danych programu .NET Framework (**System.Data.DbType** i <xref:System.Data.OracleClient.OracleType>) do użycia podczas tworzenia powiązania je jako parametry.  
  
|Typ danych Oracle|Wyliczenie DbType powiązać jako parametr|Wyliczenie typu OracleType powiązać jako parametr|Uwagi|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BPLIK**||**BFile**|Oracle umożliwia tylko tworzenie powiązań **BPLIK** jako **BPLIK** parametru. .NET Data Provider for Oracle nie automatycznie utworzyć go dla Ciebie, jeśli próba powiązania innej niż**BPLIK** wartości, takich jak **byte []** lub <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle umożliwia tylko tworzenie powiązań **BLOB** jako **BLOB** parametru. .NET Data Provider for Oracle nie automatycznie utworzyć go dla Ciebie, jeśli próba powiązania innej niż**BLOB** wartości, takich jak **byte []** lub <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**Clob**|Oracle umożliwia tylko tworzenie powiązań **CLOB** jako **CLOB** parametru. .NET Data Provider for Oracle nie automatycznie utworzyć go dla Ciebie, jeśli próba powiązania innej niż**CLOB** wartości, takich jak **System.String** lub <xref:System.Data.OracleClient.OracleString>.|  
|**DATA**|**DateTime**|**DateTime**||  
|**FLOAT**|**Pojedyncza, Double, dziesiętna**|**Przestawianie, dwukrotnie, liczba**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Określa **System.Data.DBType** i <xref:System.Data.OracleClient.OracleType>.|  
|**LICZBA CAŁKOWITA**|**SByte, Int16, Int32, Int64, dziesiętnych**|**SByte, Int16, Int32, liczba**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Określa **System.Data.DBType** i <xref:System.Data.OracleClient.OracleType>.|  
|**INTERWAŁU ROKU DO MIESIĄCA**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy za pomocą oprogramowania obu Oracle w 9i klienta i serwera.|  
|**INTERWAŁU DNIA DO SEKUNDY**|**obiekt**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy za pomocą oprogramowania obu Oracle w 9i klienta i serwera.|  
|**DŁUGI**|**AnsiString**|**LongVarChar**||  
|**DŁUGI NIEPRZETWORZONE**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle umożliwia tylko tworzenie powiązań **NCLOB** jako **NCLOB** parametru. .NET Data Provider for Oracle nie automatycznie utworzyć go dla Ciebie, jeśli próba powiązania innej niż**NCLOB** wartości, takich jak **System.String** lub <xref:System.Data.OracleClient.OracleString>.|  
|**NUMER**|**VarNumeric**|**Numer**||  
|**NVARCHAR2**|**Ciąg**|**NVarChar**||  
|**RAW**|**Binary**|**nieprzetworzone**||  
|**REF CURSOR**||**Kursor**|Aby uzyskać więcej informacji, zobacz [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**RowId**||  
|**ZNACZNIK CZASU:**|**DateTime**|**Znacznik czasu:**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy za pomocą oprogramowania obu Oracle w 9i klienta i serwera.|  
|**SYGNATURA CZASOWA PRZY UŻYCIU LOKALNEJ STREFY CZASOWEJ**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy za pomocą oprogramowania obu Oracle w 9i klienta i serwera.|  
|**SYGNATURA CZASOWA ZE STREFĄ CZASOWĄ**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> jest dostępna tylko wtedy, gdy za pomocą oprogramowania obu Oracle w 9i klienta i serwera.|  
|**LICZBA CAŁKOWITA BEZ ZNAKU**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> Określa **System.Data.DBType** i <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Wejścia/wyjścia**, **dane wyjściowe**, i **ReturnValue** **ParameterDirection** wartości używane przez <xref:System.Data.OracleClient.OracleParameter.Value%2A> właściwość <xref:System.Data.OracleClient.OracleParameter> obiektu są typy danych .NET Framework, chyba że wartość wejściowa jest typu danych Oracle (na przykład <xref:System.Data.OracleClient.OracleNumber> lub <xref:System.Data.OracleClient.OracleString>). Dotyczy to **REF CURSOR**, **BPLIK**, lub **LOB** typów danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
