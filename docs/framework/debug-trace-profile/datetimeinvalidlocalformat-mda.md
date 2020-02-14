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
ms.openlocfilehash: 2fdace8a9c7bcc090fd801be3bd717e4a2b34a87
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217549"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
`dateTimeInvalidLocalFormat` MDA jest uaktywniany, gdy wystąpienie <xref:System.DateTime>, które jest przechowywane jako uniwersalny czas koordynowany (UTC) jest sformatowane przy użyciu formatu, który jest przeznaczony do użycia tylko dla lokalnych wystąpień <xref:System.DateTime>. To zdarzenie MDA nie jest aktywowane dla nieokreślonych lub domyślnych wystąpień <xref:System.DateTime>.  
  
## <a name="symptom"></a>Objaw  
 Aplikacja ręcznie Serializowanie wystąpienia <xref:System.DateTime> UTC przy użyciu formatu lokalnego:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Przyczyna  
 Format "z" dla metody <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> obejmuje przesunięcie lokalnej strefy czasowej, na przykład "+ 10:00" dla czasu Sydney. W związku z tym zostanie wygenerowane znaczące wyniki tylko wtedy, gdy wartość <xref:System.DateTime> jest lokalna. Jeśli wartość jest czasu UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> obejmuje przesunięcie lokalnej strefy czasowej, ale nie wyświetla ani nie dostosowuje specyfikatora strefy czasowej.  
  
### <a name="resolution"></a>Rozwiązanie  
 Wystąpienia <xref:System.DateTime> UTC powinny być sformatowane w sposób, który wskazuje, że są czas UTC. Zalecany format czasu UTC do użycia "Z" jako "czas UTC":  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Istnieje również format "o", który serializacji <xref:System.DateTime> przy użyciu właściwości <xref:System.DateTime.Kind%2A>, która jest poprawnie serializowana bez względu na to, czy wystąpienie jest lokalne, UTC lub nieokreślone:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 W wyniku tego przeprowadzenia operacji MDA nie ma żadnych specjalnych danych wyjściowych. można jednak użyć stosu wywołań do określenia lokalizacji wywołania <xref:System.DateTime.ToString%2A>, które aktywuje zdarzenie MDA.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Rozważmy aplikację, która pośrednio Serializowanie wartości <xref:System.DateTime> UTC przy użyciu klasy <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> w następujący sposób.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Serializacja <xref:System.Xml.XmlConvert> i <xref:System.Data.DataSet> domyślnie używa formatów lokalnych do serializacji. Do serializacji innych rodzajów wartości <xref:System.DateTime>, takich jak UTC, są wymagane dodatkowe opcje.  
  
 W tym konkretnym przykładzie Przekaż `XmlDateTimeSerializationMode.RoundtripKind` do wywołania `ToString` na `XmlConvert`. Spowoduje to serializacji danych jako czas UTC.  
  
 W przypadku używania <xref:System.Data.DataSet>ustaw właściwość <xref:System.Data.DataColumn.DateTimeMode%2A> obiektu <xref:System.Data.DataColumn> na <xref:System.Data.DataSetDateTime.Utc>.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
