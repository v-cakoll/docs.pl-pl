---
title: "Porady: obustronna konwersja wartości daty i godziny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>Porady: obustronna konwersja wartości daty i godziny
W wielu aplikacjach wartość daty i godziny ma na celu jego jednoznacznej identyfikacji pojedynczy punkt w czasie. W tym temacie pokazano, jak zapisywanie i przywracanie <xref:System.DateTime> wartość <xref:System.DateTimeOffset> wartość i wartość daty i godziny z czasem strefy informacje, aby wartość przywróconej identyfikuje jednocześnie jako zapisana wartość.  
  
### <a name="to-round-trip-a-datetime-value"></a>Aby obustronnie konwertować wartość daty/czasu  
  
1.  Konwertuj <xref:System.DateTime> wartość do reprezentacji ciągu przez wywołanie metody <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody z specyfikator formatu "o".  
  
2.  Zapisz reprezentację ciągu <xref:System.DateTime> wartość do pliku lub przekaż go za pośrednictwem procesu, domeny aplikacji lub granic maszyny.  
  
3.  Pobierz ciąg, który reprezentuje <xref:System.DateTime> wartość.  
  
4.  Wywołanie <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> — metoda i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.  
  
 Poniższy przykład ilustruje sposób przesyłania danych <xref:System.DateTime> wartość.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Gdy dwustronną komunikację <xref:System.DateTime> wartość ta technika pomyślnie zachowuje czas zawsze lokalnych i uniwersalnych. Na przykład, jeśli na komputerze lokalnym <xref:System.DateTime> wartość jest zapisana w systemie w Stanach Zjednoczonych Pacyficzny standardowa strefy czasowej i przywróceniu w systemie w Stanach Zjednoczonych Strefy Środkowa (czas standardowy), przywróconej Data i godzina będą później niż czas oryginalnego odzwierciedla odstęp czasu między dwiema strefami czasowymi dwóch godzin. Jednak ta metoda nie jest zawsze dokładne dla nieokreślonych razy. Wszystkie <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> jest właściwość <xref:System.DateTimeKind.Unspecified> są traktowane jako są godzin czasu lokalnego. Jeśli to nie jest w tym przypadku <xref:System.DateTime> zostanie nie pomyślnie zidentyfikować poprawne punktu w czasie. Obejście tego ograniczenia jest ściśle połączenie z jego strefą czasową zapisywania wartość daty i godziny, a operacja przywracania.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Aby obustronnie konwertować wartość przesunięcia daty/czasu  
  
1.  Konwertuj <xref:System.DateTimeOffset> wartość do reprezentacji ciągu przez wywołanie metody <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody z specyfikator formatu "o".  
  
2.  Zapisz reprezentację ciągu <xref:System.DateTimeOffset> wartość do pliku lub przekaż go za pośrednictwem procesu, domeny aplikacji lub granic maszyny.  
  
3.  Pobierz ciąg, który reprezentuje <xref:System.DateTimeOffset> wartość.  
  
4.  Wywołanie <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> — metoda i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.  
  
 Poniższy przykład ilustruje sposób przesyłania danych <xref:System.DateTimeOffset> wartość.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Ta metoda zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie. Następnie można przekonwertować wartość uniwersalny czas koordynowany (UTC), wywołując <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, lub można przekonwertować na czas w strefie czasowej określonej przez wywołanie metody <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> lub <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> — metoda. Główne ograniczenie tej metody jest data i czas arytmetyczne, wykonywane na <xref:System.DateTimeOffset> wartość, która reprezentuje czas, w szczególności strefie czasowej, nie może utworzyć prawidłowych wyników dla tej strefy czasowej. Jest to spowodowane podczas <xref:System.DateTimeOffset> wartość zostanie uruchomiony, jest on oddzielone od strefy czasowej. W związku z tym reguł korygowania strefy czasowej nie będzie można zastosować podczas wykonywania obliczeń daty i czasu. Ten problem można obejść przez definiowanie niestandardowego typu, który zawiera datę i godzinę i towarzyszące strefy czasowej.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu  
  
1.  Zdefiniuj klasą lub strukturą z dwoma polami. Pierwsze pole to albo <xref:System.DateTime> lub <xref:System.DateTimeOffset> obiektu, a drugi jest <xref:System.TimeZoneInfo> obiektu. Poniższy przykład jest proste wersji takiego typu.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Oznacz klasę z <xref:System.SerializableAttribute> atrybutu.  
  
3.  Serializować obiektów przy użyciu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.  
  
4.  Przywracanie obiektów przy użyciu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.  
  
5.  Rzutowanie (C#) lub konwertowania (w języku Visual Basic) zdeserializowany obiekt na obiekt odpowiedniego typu.  
  
 Poniższy przykład ilustruje sposób przesyłania danych obiektu, który przechowuje informacje o datę i godzinę i strefę czasową.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Ta metoda zawsze jednoznacznie powinien odzwierciedlać poprawne punktu zarówno przed i po jego jest zapisywany i przywracany, przeznaczony implementacji Scalonej datę i godzinę i strefę czasową obiektu nie zezwala zostać zsynchronizowany z wartości typu date wartości strefy czasowej.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj te przykłady:  
  
-   Czy następujących przestrzeni nazw można zaimportować w języku C# `using` instrukcji lub [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` instrukcji:  
  
    -   <xref:System>(C# tylko).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Odwołania do System.Core.dll.  
  
-   Przykład każdego kodu innego niż `DateInTimeZone` klasy, powinny być uwzględnione w klasie lub module języka Visual Basic, ujęte w metody i wywoływane z `Main` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Ciągi formatujące standardowa Data i godzina](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
