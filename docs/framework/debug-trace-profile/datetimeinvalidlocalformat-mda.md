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
ms.openlocfilehash: b01f030c474e426cb87fb907f99f241eeb76a7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174761"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
MdA `dateTimeInvalidLocalFormat` jest aktywowany, <xref:System.DateTime> gdy wystąpienie, które jest przechowywane jako uniwersalny czas skoordynowany (UTC) jest <xref:System.DateTime> sformatowany przy użyciu formatu, który jest przeznaczony do użycia tylko dla wystąpień lokalnych. To narzędzie MDA nie jest aktywowane <xref:System.DateTime> dla wystąpienia nieokreślone lub domyślne.  
  
## <a name="symptom"></a>Objaw  
 Aplikacja ręcznie serializuje wystąpienie <xref:System.DateTime> UTC przy użyciu formatu lokalnego:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Przyczyna  
 Format "z" dla <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody zawiera przesunięcie lokalnej strefy czasowej, na przykład "+10:00" dla czasu Sydney. Jako takie będzie produkować znaczący wynik tylko <xref:System.DateTime> wtedy, gdy wartość jest lokalny. Jeśli wartość jest czas <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> UTC, zawiera przesunięcie lokalnej strefy czasowej, ale nie wyświetla ani nie dostosowuje specyfikatora strefy czasowej.  
  
### <a name="resolution"></a>Rozwiązanie  
 Wystąpienia <xref:System.DateTime> UTC powinny być sformatowane w sposób, który wskazuje, że są one UTC. Zalecany format czasu UTC do używania "Z" do oznaczania czasu UTC:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Istnieje również format "o", który serializuje <xref:System.DateTime> korzystanie <xref:System.DateTime.Kind%2A> z właściwości, która serializuje poprawnie, niezależnie od tego, czy wystąpienie jest lokalne, UTC lub nieokreślony:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 Ten mda nie wpływa na środowisko wykonawcze.  
  
## <a name="output"></a>Dane wyjściowe  
 Nie ma żadnych specjalnych danych wyjściowych w wyniku tego aktywowania MDA., Jednak stos <xref:System.DateTime.ToString%2A> wywołań może służyć do określenia lokalizacji wywołania, które aktywowało MDA.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę aplikację, która <xref:System.DateTime> jest pośrednio serializacji wartości UTC przy użyciu <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> klasy, w następujący sposób.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 I <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> serializacji używać formatów lokalnych do serializacji domyślnie. Dodatkowe opcje są wymagane do serializacji innych rodzajów <xref:System.DateTime> wartości, takich jak UTC.  
  
 W tym konkretnym `XmlDateTimeSerializationMode.RoundtripKind` przykładzie `ToString` przekaż `XmlConvert`do wywołania na . To serializuje dane jako czas UTC.  
  
 Jeśli <xref:System.Data.DataSet>używasz , <xref:System.Data.DataColumn.DateTimeMode%2A> ustaw <xref:System.Data.DataColumn> właściwość <xref:System.Data.DataSetDateTime.Utc>na obiekcie na .  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
