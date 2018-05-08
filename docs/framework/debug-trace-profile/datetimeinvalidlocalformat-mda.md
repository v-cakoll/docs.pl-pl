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
ms.openlocfilehash: bb5777e275fd7c48f7125b9e0315b08d3095c373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` MDA została aktywowana po <xref:System.DateTime> wystąpienie, które są przechowywane jako uniwersalny czas koordynowany (UTC) sformatowany przy użyciu formatu, który ma być używana tylko w przypadku lokalnego <xref:System.DateTime> wystąpień. To zdarzenie MDA nie została aktywowana dla nieokreślonych lub domyślna <xref:System.DateTime> wystąpień.  
  
## <a name="symptom"></a>Objaw  
 Aplikacja jest ręcznie serializacji UTC <xref:System.DateTime> wystąpienia przy użyciu lokalnego formatu:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Przyczyna  
 Format 'z' <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda zawiera przesunięcie strefy czasu lokalnego, na przykład "10:00" dla czasu Sydney. W efekcie powoduje tylko wygenerowanie znaczącego wyniku Jeśli wartość <xref:System.DateTime> jest lokalny. Jeśli wartość jest czas UTC <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> obejmuje czas lokalny przesunięcia strefy, ale nie wyświetlanie lub Dostosuj specyfikator strefy czasowej.  
  
### <a name="resolution"></a>Rozwiązanie  
 Czas UTC <xref:System.DateTime> wystąpień powinien być sformatowany w taki sposób, który wskazuje, że są one w formacie UTC. Zalecanym formatem dla czasu UTC do użycia Z określający czas UTC:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Istnieje również format "e", który serializuje <xref:System.DateTime> korzystające z <xref:System.DateTime.Kind%2A> właściwości, który serializuje prawidłowo, niezależnie od tego, czy wystąpienie lokalne, UTC, lub nieokreślona:  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 Brak żadne specjalne dane wyjściowe w wyniku tego aktywowanie MDA., jednak stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołaniu, które są aktywowane MDA.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę aplikacji, która wykonuje serializację pośrednio UTC <xref:System.DateTime> wartość przy użyciu <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> klasy, w następujący sposób.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <xref:System.Xml.XmlConvert> i <xref:System.Data.DataSet> serializations użyć lokalnego formatów serializacji domyślnie. Dodatkowe opcje są wymagane do serializacji innymi rodzajami z <xref:System.DateTime> wartości, takich jak czas UTC.  
  
 W tym przykładzie określonych przekazywanie `XmlDateTimeSerializationMode.RoundtripKind` do `ToString` wywołać `XmlConvert`. To serializuje dane jako czas UTC.  
  
 Jeśli przy użyciu <xref:System.Data.DataSet>ustaw <xref:System.Data.DataColumn.DateTimeMode%2A> właściwość <xref:System.Data.DataColumn> do obiektu <xref:System.Data.DataSetDateTime.Utc>.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
