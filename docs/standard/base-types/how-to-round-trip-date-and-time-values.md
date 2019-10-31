---
title: 'Porady: obustronna konwersja wartości daty i godziny'
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
ms.openlocfilehash: 2e3a58ffe8332e0afec62461f6897d673e1da09f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132007"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Porady: obustronna konwersja wartości daty i godziny

W wielu aplikacjach wartość daty i godziny jest przeznaczona do jednoznacznego identyfikowania pojedynczego punktu w czasie. W tym temacie przedstawiono sposób zapisywania i przywracania wartości <xref:System.DateTime>, wartości <xref:System.DateTimeOffset> oraz wartości daty i godziny z informacjami o strefie czasowej, tak aby przywrócona wartość wskazywała ten sam czas co zapisana wartość.

### <a name="to-round-trip-a-datetime-value"></a>Aby obustronnie konwertować wartość daty/czasu

1. Przekonwertuj wartość <xref:System.DateTime> na jej reprezentację ciągu, wywołując metodę <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> przy użyciu specyfikatora formatu "o".

2. Zapisz ciąg reprezentujący wartość <xref:System.DateTime> w pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.

3. Pobierz ciąg, który reprezentuje wartość <xref:System.DateTime>.

4. Wywołaj metodę <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość parametru `styles`.

Poniższy przykład ilustruje sposób rundy wartości <xref:System.DateTime>.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

W przypadku dwukrotnego wyzwolenia wartości <xref:System.DateTime> ta technika pomyślnie zachowuje czas dla wszystkich lokalnych i uniwersalnych czasów. Jeśli na przykład lokalna wartość <xref:System.DateTime> jest zapisywana w systemie w strefie czasowej USA w Stanach Zjednoczonych i zostanie przywrócona w systemie w strefie czasowej w Stanach Zjednoczonych (w warstwie Standardowa), przywrócona Data i godzina będą dwie godziny późniejsze od oryginalnego czasu , co odzwierciedla różnicę czasu między dwiema strefami czasowymi. Jednakże ta technika nie musi być dokładna dla nieokreślonych godzin. Wszystkie wartości <xref:System.DateTime>, których właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Unspecified>, są traktowane tak, jakby były czasami lokalnymi. W takim przypadku <xref:System.DateTime> nie będzie pomyślnie identyfikować poprawnego punktu w czasie. Obejście tego ograniczenia polega na ścisłym połączeniu wartości daty i godziny ze strefą czasową operacji zapisywania i przywracania.

### <a name="to-round-trip-a-datetimeoffset-value"></a>Aby obustronnie konwertować wartość przesunięcia daty/czasu

1. Przekonwertuj wartość <xref:System.DateTimeOffset> na jej reprezentację ciągu, wywołując metodę <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> przy użyciu specyfikatora formatu "o".

2. Zapisz ciąg reprezentujący wartość <xref:System.DateTimeOffset> w pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.

3. Pobierz ciąg, który reprezentuje wartość <xref:System.DateTimeOffset>.

4. Wywołaj metodę <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość parametru `styles`.

Poniższy przykład ilustruje sposób rundy wartości <xref:System.DateTimeOffset>.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Ta technika zawsze jednoznacznie identyfikuje wartość <xref:System.DateTimeOffset> jako pojedynczy punkt w czasie. Wartość można następnie przekonwertować na uniwersalny czas koordynowany (UTC), wywołując metodę <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> lub można ją przekonwertować na czas w określonej strefie czasowej, wywołując metodę <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> lub <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>. Głównym ograniczeniem tej metody jest to, że data i czas arytmetyczny, gdy jest wykonywane na wartości <xref:System.DateTimeOffset>, która reprezentuje czas w określonej strefie czasowej, może nie generować dokładnych wyników dla tej strefy czasowej. Wynika to z faktu, że w przypadku wystąpienia wartości <xref:System.DateTimeOffset> zostanie ona nieskojarzona ze strefą czasową. W związku z tym reguły dostosowania strefy czasowej nie mogą być stosowane podczas obliczeń daty i godziny. Ten problem można obejść, definiując typ niestandardowy, który zawiera zarówno wartość daty, jak i godzinę oraz towarzyszącą strefę czasową.

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu

1. Zdefiniuj klasę lub strukturę z dwoma polami. Pierwsze pole jest obiektem <xref:System.DateTime> lub <xref:System.DateTimeOffset>, a drugi jest obiektem <xref:System.TimeZoneInfo>. Poniższy przykład jest prostą wersją tego typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Oznacz klasę atrybutem <xref:System.SerializableAttribute>.

3. Serializacja obiektu za pomocą metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.

4. Przywróć obiekt za pomocą metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.

5. Cast (in C#) lub Convert (w Visual Basic) obiekt deserializowany do obiektu odpowiedniego typu.

Poniższy przykład ilustruje sposób rundy, który przechowuje informacje o dacie i godzinie oraz o strefie czasowej.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Ta technika powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu przed i po jego zapisaniu i przywrócenia, pod warunkiem, że wdrożenie połączonej daty i godziny i obiektu strefy czasowej nie zezwala na synchronizację wartości daty z wartość strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Te przykłady wymagają:

- Następujące przestrzenie nazw można zaimportować za C# pomocą instrukcji `using` lub instrukcji Visual Basic `Imports`:

  - <xref:System> (C# tylko).

  - <xref:System.Globalization?displayProperty=nameWithType>.,

  - <xref:System.IO?displayProperty=nameWithType>.,

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.,

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.,

- Każdy przykład kodu, inny niż Klasa `DateInTimeZone`, powinien być uwzględniony w module klasy lub Visual Basic, opakowany w metodach i wywoływany z metody `Main`.

## <a name="see-also"></a>Zobacz także

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
