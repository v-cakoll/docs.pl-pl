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
ms.openlocfilehash: 3aa615dc7d7d1d49dce4897f8508b5210b364fc0
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635137"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Instrukcje: Obustronne wartości daty i godziny

W wielu aplikacjach wartość daty i godziny jest przeznaczona do jednoznacznego identyfikowania pojedynczego punktu w czasie. W tym artykule pokazano, <xref:System.DateTime> jak <xref:System.DateTimeOffset> zapisać i przywrócić wartość, wartość oraz wartość daty i godziny z informacjami o strefie czasowej, tak aby przywrócona wartość określała ten sam czas co zapisana wartość.

## <a name="round-trip-a-datetime-value"></a>W obie strony wartość DateTime

1. Przekonwertować <xref:System.DateTime> wartość na jego <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".

2. Zapisz reprezentację ciągu <xref:System.DateTime> wartości w pliku lub przekaż ją przez obwiednię procesu, domeny aplikacji lub komputera.

3. Pobierz ciąg, który <xref:System.DateTime> reprezentuje wartość.

4. Wywołaj <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekaż jako `styles` wartość parametru.

Poniższy przykład ilustruje sposób <xref:System.DateTime> w obie strony wartości.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

Podczas zaokrąglania <xref:System.DateTime> wartości ta technika z powodzeniem zachowuje czas dla wszystkich czasów lokalnych i uniwersalnych. Jeśli na przykład <xref:System.DateTime> wartość lokalna jest zapisywana w systemie w standardowej strefie czasowej stanów Pacyfiku stanów Zjednoczonych i przywracana w systemie w centralnej standardowej strefie czasowej STANÓW Zjednoczonych, przywrócona data i godzina będą dwie godziny później niż pierwotny czas, co odzwierciedla różnicę czasu między dwiema strefami czasowymi. Jednak ta technika nie musi być dokładna dla nieokreślonych czasów. Wszystkie <xref:System.DateTime> wartości, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> których właściwość jest traktowana tak, jakby były one czas lokalny. Jeśli nie jest to czas <xref:System.DateTime> lokalny, nie pomyślnie zidentyfikować prawidłowy punkt w czasie. Obejście tego ograniczenia polega na ścisłym połączeniu wartości daty i godziny ze strefą czasową dla operacji zapisywania i przywracania.

## <a name="round-trip-a-datetimeoffset-value"></a>W obie strony wartość DateTimeOffset

1. Przekonwertować <xref:System.DateTimeOffset> wartość na jego <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".

2. Zapisz reprezentację ciągu <xref:System.DateTimeOffset> wartości w pliku lub przekaż ją przez obwiednię procesu, domeny aplikacji lub komputera.

3. Pobierz ciąg, który <xref:System.DateTimeOffset> reprezentuje wartość.

4. Wywołaj <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekaż jako `styles` wartość parametru.

Poniższy przykład ilustruje sposób <xref:System.DateTimeOffset> w obie strony wartości.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Ta technika zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie. Wartość można następnie przekonwertować na skoordynowany czas uniwersalny (UTC) przez wywołanie <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody lub można ją <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> przekonwertować na czas w określonej strefie czasowej, wywołując metodę lub. Głównym ograniczeniem tej techniki jest ta arytmetyka daty <xref:System.DateTimeOffset> i godziny, gdy jest wykonywana na wartości reprezentującej czas w określonej strefie czasowej, może nie dawać dokładnych wyników dla tej strefy czasowej. Dzieje się tak, ponieważ po wystąpieniu <xref:System.DateTimeOffset> wartości jest on adosoiczony, jest odłączony od jego strefy czasowej. W związku z tym reguły dopasowania tej strefy czasowej nie mogą być już stosowane podczas wykonywania obliczeń daty i godziny. Można obejść ten problem, definiując typ niestandardowy, który zawiera zarówno wartość daty i godziny, jak i towarzyszącą jej strefę czasową.

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a>W obie strony wartość daty i godziny ze strefą czasową

1. Zdefiniuj klasę lub strukturę z dwoma polami. Pierwsze pole jest obiektem <xref:System.DateTime> <xref:System.DateTimeOffset> lub obiektem, a <xref:System.TimeZoneInfo> drugim obiektem. Poniższy przykład jest prostą wersją takiego typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Oznacz klasę atrybutem. <xref:System.SerializableAttribute>

3. Serializuj obiekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> przy użyciu metody.

4. Przywróć <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> obiekt przy użyciu metody.

5. Rzutowanie (w języku C#) lub konwersji (w języku Visual Basic) deserialized obiektu do obiektu odpowiedniego typu.

Poniższy przykład ilustruje sposób w obie strony obiektu, który przechowuje zarówno strefy czasowej i informacji o dacie i godzinie.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Ta technika powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu zarówno przed, jak i po zapisaniu i przywróceniu, pod warunkiem że implementacja połączonego obiektu daty i godziny i strefy czasowej nie pozwala na zsynchronizowanie wartości daty z wartością strefy czasowej.

## <a name="compile-the-code"></a>Skompiluj kod

Te przykłady wymagają, aby:

- Następujące obszary nazw mają być importowane z dyrektywami języka C# `using` lub instrukcjami języka Visual Basic: `Imports`

  - <xref:System>(tylko C#)

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- Każdy przykład kodu, `DateInTimeZone` inne niż klasa, należy uwzględnić w klasie lub visual basic `Main` moduł, zawinięte w metody i wywoływane z metody.

## <a name="see-also"></a>Zobacz też

- [Wybieranie między datą, datownikami, timespan i timezoneinfo](../../../docs/standard/datetime/choosing-between-datetime.md)
- [Standardowe ciągi formatujące datę i godzinę](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
