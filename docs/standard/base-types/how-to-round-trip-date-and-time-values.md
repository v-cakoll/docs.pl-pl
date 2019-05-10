---
title: 'Instrukcje: Obustronne wartości daty i godziny'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eb9eabe006dd10b0c36d0fb477637a519853ef2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633836"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Instrukcje: Obustronne wartości daty i godziny
W wielu aplikacjach wartości daty i godziny jest przeznaczona do jego jednoznacznej identyfikacji pojedynczego punktu w czasie. W tym temacie pokazano, jak zapisywanie i przywracanie <xref:System.DateTime> wartość <xref:System.DateTimeOffset> wartości i wartości daty i godziny, z czasem strefy, aby wartość przywróconej identyfikuje tym samym czasie jako zapisaną wartość.  
  
### <a name="to-round-trip-a-datetime-value"></a>Aby obustronnie konwertować wartość daty/czasu  
  
1. Konwertuj <xref:System.DateTime> wartość na jego reprezentację ciągu, wywołując <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody przy użyciu specyfikatora formatu "o".  
  
2. Zapisz ciąg reprezentujący <xref:System.DateTime> do pliku lub wartości krzyż procesu, domeny aplikacji lub granic maszyny.  
  
3. Pobierz ciąg, który reprezentuje <xref:System.DateTime> wartość.  
  
4. Wywołaj <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.  
  
 Poniższy przykład ilustruje sposób przesłania danych <xref:System.DateTime> wartość.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Podczas Pełna zgodnooć wersji <xref:System.DateTime> wartość ta technika pomyślnie zachowuje czas cały czas lokalnych i uniwersalnych. Na przykład, jeśli lokalny <xref:System.DateTime> wartość jest zapisywana w systemie, w Stanach Zjednoczonych Pacyficznego standardowa strefy czasowej i zostanie przywrócony w systemie, w Stanach Zjednoczonych Środkowy czas standardowy strefy, przywróconej datę i godzinę będzie później niż pierwotny czas, który odzwierciedla różnica czasu między dwiema strefami czasowymi dwóch godzin. Ta technika nie jest jednak zawsze prawidłowe dla nieokreślonych godziny. Wszystkie <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Unspecified> są traktowane tak, są one czas lokalny. Jeśli nie jest to przypadek, <xref:System.DateTime> nie pomyślnie zidentyfikujesz prawidłowy punkt w czasie. Obejście tego ograniczenia jest ściśle Połącz wartości daty i godziny z ich strefą czasu, zapisywania i operacji przywracania.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Aby obustronnie konwertować wartość przesunięcia daty/czasu  
  
1. Konwertuj <xref:System.DateTimeOffset> wartość na jego reprezentację ciągu, wywołując <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody przy użyciu specyfikatora formatu "o".  
  
2. Zapisz ciąg reprezentujący <xref:System.DateTimeOffset> do pliku lub wartości krzyż procesu, domeny aplikacji lub granic maszyny.  
  
3. Pobierz ciąg, który reprezentuje <xref:System.DateTimeOffset> wartość.  
  
4. Wywołaj <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.  
  
 Poniższy przykład ilustruje sposób przesłania danych <xref:System.DateTimeOffset> wartość.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Ta technika zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie. Można następnie można konwertować wartości do uniwersalny czas koordynowany (UTC) przez wywołanie metody <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metodę, lub można przekonwertować na czas w strefie czasowej określonej przez wywołanie metody <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> lub <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody. Główne ograniczenia tej techniki jest tej daty i godziny operacje arytmetyczne, gdy przeprowadzane na <xref:System.DateTimeOffset> wartość, która reprezentuje czas w określonej strefie czasowej, nie może wygenerować dokładne wyniki dla tej strefy czasowej. To dlatego, gdy <xref:System.DateTimeOffset> konkretyzacji wartość, jej jest oddzielone od strefy czasowej. W związku z tym nie jest już można zastosować reguł korygowania tej strefy czasowej, kiedy można wykonywać obliczenia daty i godziny. Ten problem można obejść, definiując typ niestandardowy, który zawiera wartość typu date i wartość czasu i towarzyszące strefy czasowej.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu  
  
1. Zdefiniuj klasę lub strukturę z dwóch pól. Pierwsze pole to <xref:System.DateTime> lub <xref:System.DateTimeOffset> obiektu, a drugi jest <xref:System.TimeZoneInfo> obiektu. Poniższy przykład jest prosta wersja takiego typu.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2. Oznacz klasę za pomocą <xref:System.SerializableAttribute> atrybutu.  
  
3. Serializowanie przy użyciu obiektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.  
  
4. Przywrócić dane przy użyciu obiektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.  
  
5. Rzutowanie (C#) lub przekonwertować (w języku Visual Basic) obiektu po deserializacji obiektu odpowiedniego typu.  
  
 W poniższym przykładzie pokazano, jak przesyłania danych obiektu, który przechowuje informacje o datę i godzinę i strefę czasową.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Ta technika zawsze jednoznacznie powinny odzwierciedlać poprawne momencie zarówno przed i po jego jest zapisywany i przywracany, pod warunkiem wykonania połączonego obiektu daty i godziny i strefy czasowej nie zezwala na wartość daty zostać zsynchronizowany z wartości strefy czasowej.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj tych przykładach:  
  
- Czy następujących przestrzeni nazw można zaimportować za pomocą języka C# `using` instrukcji lub Visual Basic `Imports` instrukcji:  
  
    - <xref:System> (Tylko język C#).  
  
    - <xref:System.Globalization?displayProperty=nameWithType>.  
  
    - <xref:System.IO?displayProperty=nameWithType>.  
  
    - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
- Odwołanie do biblioteki System.Core.dll.  
  
- Przykład kodowych innych niż `DateInTimeZone` klasy, powinny być uwzględnione w klasie lub module języka Visual Basic, opakowane w metodach i wywoływane z `Main` metody.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
