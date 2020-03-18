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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132007"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Porady: obustronna konwersja wartości daty i godziny

W wielu aplikacjach wartość daty i godziny ma na celu jednoznaczne zidentyfikowanie pojedynczego punktu w czasie. W tym temacie pokazano, <xref:System.DateTime> jak <xref:System.DateTimeOffset> zapisać i przywrócić wartość, wartość i wartość daty i godziny z informacjami o strefie czasowej, dzięki czemu przywrócona wartość identyfikuje ten sam czas co zapisana wartość.

### <a name="to-round-trip-a-datetime-value"></a>Aby obustronnie konwertować wartość daty/czasu

1. Konwertuj wartość na <xref:System.DateTime> <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> jego reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".

2. Zapisz reprezentację ciągu <xref:System.DateTime> wartości do pliku lub przekaż ją przez granicę procesu, domeny aplikacji lub komputera.

3. Pobierz ciąg reprezentujący <xref:System.DateTime> wartość.

4. Wywołać <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekazać jako `styles` wartość parametru.

W poniższym przykładzie przedstawiono sposób <xref:System.DateTime> w obie strony wartości.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Podczas rundy potknięcia <xref:System.DateTime> wartości, ta technika z powodzeniem zachowuje czas dla wszystkich lokalnych i uniwersalnych czasów. Jeśli na przykład <xref:System.DateTime> wartość lokalna zostanie zapisana w systemie w standardowej strefie czasowej Stany Zjednoczonego Pacyfiku i zostanie przywrócona w systemie w strefie czasowej standardu centralnego usa, przywrócona data i godzina będą dwie godziny później spożące niż czas pierwotny, który odzwierciedla różnicę czasu między dwiema strefami czasowymi. Jednak ta technika nie musi być dokładna dla nieokreślonych czasów. Wszystkie <xref:System.DateTime> wartości, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> których właściwość jest traktowana tak, jakby były czasami lokalnymi. Jeśli tak nie jest, <xref:System.DateTime> nie zidentyfikuje pomyślnie prawidłowego punktu w czasie. Obejściem tego ograniczenia jest ścisłe sparowanie wartości daty i godziny ze strefą czasową dla operacji zapisywania i przywracania.

### <a name="to-round-trip-a-datetimeoffset-value"></a>Aby obustronnie konwertować wartość przesunięcia daty/czasu

1. Konwertuj wartość na <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> jego reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".

2. Zapisz reprezentację ciągu <xref:System.DateTimeOffset> wartości do pliku lub przekaż ją przez granicę procesu, domeny aplikacji lub komputera.

3. Pobierz ciąg reprezentujący <xref:System.DateTimeOffset> wartość.

4. Wywołać <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekazać jako `styles` wartość parametru.

W poniższym przykładzie przedstawiono sposób <xref:System.DateTimeOffset> w obie strony wartości.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Ta technika zawsze jednoznacznie <xref:System.DateTimeOffset> identyfikuje wartość jako pojedynczy punkt w czasie. Wartość można następnie przekonwertować na skoordynowany czas <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> uniwersalny (UTC) przez wywołanie metody lub można ją <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> przekonwertować na czas w określonej strefie czasowej, wywołując lub metody. Głównym ograniczeniem tej techniki jest to, że data i godzina arytmetyka, gdy wykonywane na <xref:System.DateTimeOffset> wartość, która reprezentuje czas w określonej strefie czasowej, może nie dawać dokładne wyniki dla tej strefy czasowej. Dzieje się tak, ponieważ gdy <xref:System.DateTimeOffset> wartość jest tworzone, jest odłączony od jego strefy czasowej. W związku z tym reguły korekty tej strefy czasowej nie mogą być już stosowane podczas wykonywania obliczeń daty i godziny. Można obejść ten problem, definiując typ niestandardowy, który zawiera zarówno wartość daty i godziny, jak i towarzyszącą jej strefę czasową.

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu

1. Zdefiniuj klasę lub strukturę z dwoma polami. Pierwsze pole to <xref:System.DateTime> <xref:System.DateTimeOffset> obiekt lub obiekt, a <xref:System.TimeZoneInfo> drugie jest obiektem. Poniższy przykład jest prostą wersją takiego typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Oznacz klasę <xref:System.SerializableAttribute> atrybutem.

3. Serializowania obiektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> przy użyciu metody.

4. Przywróć obiekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> za pomocą metody.

5. Rzutować (w języku C#) lub konwertować (w języku Visual Basic) obiekt zdeserializowany do obiektu odpowiedniego typu.

W poniższym przykładzie pokazano, jak w obie strony obiektu, który przechowuje zarówno daty i godziny i informacji o strefie czasowej.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Technika ta powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu zarówno przed, jak i po jego zapisaniu i przywróceniu, pod warunkiem, że implementacja połączonego obiektu daty i godziny oraz strefy czasowej nie pozwala, aby wartość daty nie była zsynchronizowana z obiektem wartości strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Poteki wymagają:

- Zaimportowanie następujących obszarów nazw `using` z instrukcjami Języka C# lub instrukcjami języka Visual Basic: `Imports`

  - <xref:System>(tylko C#).

  - <xref:System.Globalization?displayProperty=nameWithType>.

  - <xref:System.IO?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>.

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.

- Każdy przykład kodu, `DateInTimeZone` inne niż klasa, powinny być zawarte w klasie lub Visual Basic `Main` moduł, opakowane w metody i wywoływane z metody.

## <a name="see-also"></a>Zobacz też

- [Wykonywanie operacji formatowania](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Wybieranie między datetime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
