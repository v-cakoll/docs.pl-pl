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
ms.openlocfilehash: 32217b9e681179c246560ff5b51b65b4f4e044d5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052887"
---
# <a name="datetimeinvalidlocalformat-mda"></a>dateTimeInvalidLocalFormat MDA
Zdarzenie MDA jest uaktywniane, <xref:System.DateTime> gdy wystąpienie, które jest przechowywane jako uniwersalny czas koordynowany (UTC) jest sformatowane przy użyciu formatu, który jest przeznaczony do użycia tylko dla wystąpień lokalnych <xref:System.DateTime>. `dateTimeInvalidLocalFormat` Ta wartość MDA nie została aktywowana dla wystąpień nieokreślonych lub domyślnych <xref:System.DateTime> .  
  
## <a name="symptom"></a>Objaw  
 Aplikacja ręcznie Serializowanie wystąpienia czasu UTC <xref:System.DateTime> przy użyciu formatu lokalnego:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a>Przyczyna  
 Format "z" dla <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody obejmuje przesunięcie lokalnej strefy czasowej, na przykład "+ 10:00" dla czasu Sydney. W związku z tym zostanie wygenerowane znaczące wyniki tylko wtedy, gdy wartość <xref:System.DateTime> jest lokalna. Jeśli wartość jest czasu UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> uwzględnia przesunięcie strefy czasowej, ale nie wyświetla ani nie dostosowuje specyfikatora strefy czasowej.  
  
### <a name="resolution"></a>Rozwiązanie  
 Wystąpienia <xref:System.DateTime> czasu UTC powinny być sformatowane w taki sposób, aby wskazywały czas UTC. Zalecany format czasu UTC do użycia "Z" jako "czas UTC":  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Istnieje również format "o", który serializować <xref:System.DateTime> użycie <xref:System.DateTime.Kind%2A> właściwości, która jest poprawnie serializowana bez względu na to, czy wystąpienie jest lokalne, UTC, czy nieokreślone:  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 W wyniku tego przeprowadzenia operacji MDA nie ma żadnych specjalnych danych wyjściowych. jednak stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołania, które aktywuje zdarzenie MDA.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Rozważmy aplikację, która pośrednio serializacji wartość czasu UTC <xref:System.DateTime> przy <xref:System.Xml.XmlConvert> użyciu klasy or <xref:System.Data.DataSet> , w następujący sposób.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Serializacji <xref:System.Xml.XmlConvert> i<xref:System.Data.DataSet> domyślnie używają formatów lokalnych do serializacji. Do serializacji innych rodzajów <xref:System.DateTime> wartości, takich jak UTC, są wymagane dodatkowe opcje.  
  
 Na potrzeby tego konkretnego przykładu `XmlDateTimeSerializationMode.RoundtripKind` Przekaż `ToString` do wywołania `XmlConvert`. Spowoduje to serializacji danych jako czas UTC.  
  
 Jeśli używasz <xref:System.Data.DataSet>, <xref:System.Data.DataColumn.DateTimeMode%2A> <xref:System.Data.DataColumn> Ustaw<xref:System.Data.DataSetDateTime.Utc>właściwość obiektu na.  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.DateTimeFormatInfo>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
