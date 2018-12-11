---
title: dateTimeInvalidLocalFormat MDA
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54ce0f75ddfbf9f3b62917aa67f4d97140bbdc42
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153348"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` Zdarzenie MDA jest aktywowane podczas <xref:System.DateTime> wystąpienie, które są przechowywane jako uniwersalny czas koordynowany (UTC) jest formatowana przy użyciu formatu, który jest przeznaczony do użycia tylko w przypadku lokalnego <xref:System.DateTime> wystąpień. To zdarzenie MDA nie została aktywowana, nie określono tego parametru lub domyślna <xref:System.DateTime> wystąpień.  
  
## <a name="symptom"></a>Objaw  
 Aplikacja jest ręczne serializacji formatu UTC <xref:System.DateTime> wystąpienia przy użyciu lokalnego formatu:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Przyczyna  
 Format "z" <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda zawiera przesunięcie strefy czasu lokalnego, na przykład "10:00" dla czasu Sydney. W efekcie powoduje tylko wygenerowanie znaczący wynik przypadku wartość <xref:System.DateTime> jest lokalny. Jeśli wartość jest czas UTC <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> obejmuje czas lokalny przesunięcia strefy, ale nie wyświetlić lub dostosować specyfikator strefy czasowej.  
  
### <a name="resolution"></a>Rozwiązanie  
 UTC <xref:System.DateTime> wystąpień powinny być sformatowane w sposób sugerujący, że są one UTC. Zalecany format czasu UTC na potrzeby "Z" oznaczają czas UTC:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Dostępna jest również formatu "o", który serializuje <xref:System.DateTime> korzystające z <xref:System.DateTime.Kind%2A> właściwości, który serializuje prawidłowo, niezależnie od tego, czy wystąpienie jest lokalnym, UTC, lub nieokreślony:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowiska uruchomieniowego.  
  
## <a name="output"></a>Dane wyjściowe  
 Istnieje żadne specjalne dane wyjściowe w wyniku tego MDA aktywowanie., natomiast stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołania, które aktywowano MDA.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Rozważmy aplikację, która jest pośrednio serializacji formatu UTC <xref:System.DateTime> wartości za pomocą <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> klasy, w następujący sposób.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> i <xref:System.Data.DataSet> serializations formaty lokalne serializacji domyślnie używają. Dodatkowe opcje są wymagane do wykonywania serializacji innych typów z <xref:System.DateTime> wartości, takich jak UTC.  
  
 W tym przykładzie określonych przekazać `XmlDateTimeSerializationMode.RoundtripKind` do `ToString` wywołanie na `XmlConvert`. To serializuje dane jako czas UTC.  
  
 Jeśli przy użyciu <xref:System.Data.DataSet>ustaw <xref:System.Data.DataColumn.DateTimeMode%2A> właściwość <xref:System.Data.DataColumn> obiekt <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
