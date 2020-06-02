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
ms.openlocfilehash: 60483a6e29c65fc0c5803e8084053d53d9fc3c37
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290451"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Instrukcje: Obustronne wartości daty i godziny

W wielu aplikacjach wartość daty i godziny jest przeznaczona do jednoznacznego identyfikowania pojedynczego punktu w czasie. W tym artykule przedstawiono sposób zapisywania i przywracania <xref:System.DateTime> wartości, <xref:System.DateTimeOffset> wartości oraz wartości daty i godziny z informacjami o strefie czasowej, tak aby przywrócona wartość wskazywała ten sam czas co zapisana wartość.

## <a name="round-trip-a-datetime-value"></a>Runda wartość daty i godziny

1. Przekonwertuj <xref:System.DateTime> wartość na jej reprezentację w postaci ciągu, wywołując <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodę ze specyfikatorem formatu "o".

2. Zapisz ciąg reprezentujący <xref:System.DateTime> wartość do pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.

3. Pobierz ciąg, który reprezentuje <xref:System.DateTime> wartość.

4. Wywołaj <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.

Poniższy przykład ilustruje sposób rundy <xref:System.DateTime> wartości.

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

W przypadku rundy <xref:System.DateTime> wartości, ta technika pomyślnie zachowuje czas dla wszystkich lokalnych i uniwersalnych czasów. Jeśli na przykład lokalna <xref:System.DateTime> wartość jest zapisywana w systemie w strefie czasowej USA w Stanach Zjednoczonych i przywrócona w systemie w strefie czasowej w Stanach Zjednoczonych (USA), przywrócona Data i godzina będą miały dwie godziny późniejsze niż pierwotny czas, który odzwierciedla różnicę czasu między dwiema strefami czasowymi. Jednakże ta technika nie musi być dokładna dla nieokreślonych godzin. Wszystkie <xref:System.DateTime> wartości <xref:System.DateTime.Kind%2A> , których właściwość jest <xref:System.DateTimeKind.Unspecified> traktowana jako czas lokalny. Jeśli nie jest to czas lokalny, <xref:System.DateTime> nie zidentyfikuje prawidłowo punktu w czasie. Obejście tego ograniczenia polega na ścisłym połączeniu wartości daty i godziny ze strefą czasową operacji zapisywania i przywracania.

## <a name="round-trip-a-datetimeoffset-value"></a>Przerundy wartość DateTimeOffset

1. Przekonwertuj <xref:System.DateTimeOffset> wartość na jej reprezentację w postaci ciągu, wywołując <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodę ze specyfikatorem formatu "o".

2. Zapisz ciąg reprezentujący <xref:System.DateTimeOffset> wartość do pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.

3. Pobierz ciąg, który reprezentuje <xref:System.DateTimeOffset> wartość.

4. Wywołaj <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.

Poniższy przykład ilustruje sposób rundy <xref:System.DateTimeOffset> wartości.

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

Ta technika zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie. Wartość można następnie przekonwertować na uniwersalny czas koordynowany (UTC) przez wywołanie <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody lub można ją przekonwertować na czas w określonej strefie czasowej przez wywołanie <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody lub. Głównym ograniczeniem tej metody jest to, że data i czas arytmetyczny, gdy jest wykonywane na <xref:System.DateTimeOffset> wartości, która reprezentuje czas w określonej strefie czasowej, może nie generować dokładnych wyników dla tej strefy czasowej. Wynika to z faktu <xref:System.DateTimeOffset> , że w przypadku wystąpienia wartości jest ona nieskojarzona ze strefą czasową. W związku z tym reguły dostosowania strefy czasowej nie mogą być stosowane podczas obliczeń daty i godziny. Ten problem można obejść, definiując typ niestandardowy, który zawiera zarówno wartość daty, jak i godzinę oraz towarzyszącą strefę czasową.

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a>Wartość daty i godziny w postaci dwukierunkowej dla strefy czasowej

1. Zdefiniuj klasę lub strukturę z dwoma polami. Pierwsze pole jest albo <xref:System.DateTime> <xref:System.DateTimeOffset> obiektem, a drugi jest <xref:System.TimeZoneInfo> obiektem. Poniższy przykład jest prostą wersją tego typu.

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. Oznacz klasę <xref:System.SerializableAttribute> atrybutem.

3. Serializacja obiektu za pomocą <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.

4. Przywróć obiekt za pomocą <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.

5. Cast (w języku C#) lub Convert (w Visual Basic) obiekt deserializowany do obiektu odpowiedniego typu.

Poniższy przykład ilustruje sposób rundy, który przechowuje zarówno informacje o strefie czasowej, jak i dacie i godzinie.

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

Ta technika powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu przed i po jego zapisaniu i przywracania, pod warunkiem, że wdrożenie połączonej daty i godziny i obiektu strefy czasowej nie zezwala na synchronizację wartości daty z wartością strefy czasowej.

## <a name="compile-the-code"></a>Kompiluj kod

Te przykłady wymagają:

- Następujące przestrzenie nazw można zaimportować przy użyciu dyrektyw języka C# `using` lub `Imports` instrukcji Visual Basic:

  - <xref:System>(Tylko w języku C#)

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- Każdy przykład kodu, inny niż `DateInTimeZone` Klasa, jest uwzględniony w module klasy lub Visual Basic, opakowany w metodach i wywoływany z `Main` metody.

## <a name="see-also"></a>Zobacz także

- [Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../datetime/choosing-between-datetime.md)
- [Standardowe ciągi formatujące datę i godzinę](standard-date-and-time-format-strings.md)
