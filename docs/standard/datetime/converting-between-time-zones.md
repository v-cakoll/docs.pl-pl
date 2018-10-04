---
title: Konwertowanie godzin między strefami czasowymi
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f5a70a01937c52197978db776b90028e1fcb7c6
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580160"
---
# <a name="converting-times-between-time-zones"></a>Konwertowanie godzin między strefami czasowymi

Staje się coraz ważniejsze dla każdej aplikacji, która współdziała z datami i godzinami, aby obsłużyć różnic między strefami czasowymi. Aplikacji nie jest już można założyć, że cały czas mogą być wyrażone według czasu lokalnego, który jest czas dostępny z <xref:System.DateTime> struktury. Na przykład strony sieci Web, która wyświetla bieżący czas w części Wschodniej Stanów Zjednoczonych będzie brakuje wiarygodności do klientów w Azji Wschodniej. W tym temacie wyjaśniono, jak przekonwertować godzin między strefami czasowymi, a także sposób konwertowania <xref:System.DateTimeOffset> wartości, które ma ograniczone rozpoznawanie strefy czasowej.

## <a name="converting-to-coordinated-universal-time"></a>Konwertowanie na uniwersalny czas koordynowany

Uniwersalny czas koordynowany (UTC) jest wysokiej precyzji, atomic czasu standardowego. Stref czasowych na świecie są wyrażane jako dodatnie lub ujemne przesunięcie względem czasu UTC. W związku z tym UTC zawiera rodzaj strefy czasowej bezpłatne lub strefy czasowej neutralne godzina. Użycie czasu UTC jest zalecane, gdy wartość typu date i ważne jest, przenośność czasu na komputerach. (Szczegóły i inne najlepsze rozwiązania przy użyciu daty i godziny można znaleźć [kodowania najlepszych rozwiązań za pomocą daty/godziny w programie .NET Framework](https://msdn.microsoft.com/library/ms973825.aspx).) Konwertowanie poszczególnych stref czasowych UTC ułatwia porównania czas.

> [!NOTE]
> Można również wykonać serializację <xref:System.DateTimeOffset> strukturę, aby jednoznacznie reprezentują pojedynczy punkt w czasie. Ponieważ <xref:System.DateTimeOffset> obiektów przechowywanie wartości daty i godziny, wraz z jego przesunięcie względem czasu UTC, zawsze reprezentują określonego punktu w czasie w relacji na czas UTC.

Najprostszym sposobem konwersji czasu UTC jest wywołać `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> metody. Dokładne konwersji, wykonywane przez metodę zależy od wartości `dateTime` parametru <xref:System.DateTime.Kind%2A> właściwości, jak pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Konwertuje czas lokalny na czas UTC.                                                    |
| `DateTimeKind.Unspecified` | Przyjęto założenie, `dateTime` parametr jest czasem lokalnym i Konwertuje czas lokalny na czas UTC. |
| `DateTimeKind.Utc`         | Zwraca `dateTime` parametru bez zmian.                                    |

Poniższy kod konwertuje bieżącego czasu lokalnego na UTC i wyświetla wynik do konsoli.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Jeśli wartość daty i godziny nie reprezentuje czas lokalny lub czasu UTC, <xref:System.DateTime.ToUniversalTime%2A> metoda zwróci prawdopodobnie błędne wyniki. Można jednak użyć <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metodę, aby przekonwertować datę i godzinę z określonej strefy czasowej. (Aby uzyskać szczegółowe informacje dotyczące pobierania <xref:System.TimeZoneInfo> obiekt, który reprezentuje docelowa strefa czasowa, zobacz [znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Poniższy kod używa <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metodę, aby przekonwertować wschodni czas standardowy względem czasu UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Należy zauważyć, że ta metoda wyrzuca <xref:System.ArgumentException> Jeśli <xref:System.DateTime> obiektu <xref:System.DateTime.Kind%2A> właściwości i strefy czasowej są niezgodne. Występuje niezgodność, jeśli <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> obiekt nie reprezentuje lokalnej strefy czasowej, lub jeśli <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ale <xref:System.TimeZoneInfo> obiektu nie jest równa <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.

Podjąć wszystkie te metody <xref:System.DateTime> wartości jako parametrów i zwrotu <xref:System.DateTime> wartość. Dla <xref:System.DateTimeOffset> wartości <xref:System.DateTimeOffset> ma strukturę <xref:System.DateTimeOffset.ToUniversalTime%2A> wystąpienia metody, która konwertuje datę i godzinę bieżącego wystąpienia względem czasu UTC. Poniższy przykład wywołuje <xref:System.DateTimeOffset.ToUniversalTime%2A> metodę konwersji czasu lokalnego oraz kilka innych razy uniwersalnego czasu koordynowanego (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Konwertowanie wyznaczonym strefy czasowej UTC

Aby dokonać konwersji czasu UTC na czas lokalny, zobacz sekcję "konwersji czasu UTC na czas lokalny", poniżej. Aby dokonać konwersji czasu UTC na czas w dowolnej strefie czasowej, wyznaczony, należy wywołać <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> metody. Ta metoda przyjmuje dwa parametry:

* UTC do przekonwertowania. Musi to być <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na `Unspecified` lub `Utc`.

* Strefa czasowa UTC, aby przekonwertować.

Poniższy kod konwertuje UTC Środkowa (czas standardowy).

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Konwertowanie UTC na czas lokalny

Aby dokonać konwersji czasu UTC na czas lokalny, należy wywołać <xref:System.DateTime.ToLocalTime%2A> metody <xref:System.DateTime> obiektu którego ma zostać przekonwertowany. Dokładne zachowanie metody zależy od wartości obiektu <xref:System.DateTime.Kind%2A> właściwości, jak pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Zwraca <xref:System.DateTime> wartości bez zmian.                                      |
| `DateTimeKind.Unspecified` | Zakłada się, że <xref:System.DateTime> wartość jest czasem UTC i konwertuje UTC na czas lokalny. |
| `DateTimeKind.Utc`         | Konwertuje <xref:System.DateTime> wartość na czas lokalny.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Metody zachowuje się tak samo `DateTime.ToLocalTime` metody. Trwa jeden parametr, czyli wartość daty i godziny do przekonwertowania.

Czas, w dowolnym wyznaczonym strefie czasowej można przekonwertować na czas lokalny, używając `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> metody. Ta technika jest omówiona w następnej sekcji.

## <a name="converting-between-any-two-time-zones"></a>Konwertowanie pomiędzy wszelkie dwie strefy czasowe

Można wykonywać konwersje między wszystkie dwóch stref czasowych przy użyciu jednej z następujących dwóch `static` (`Shared` w języku Visual Basic) metody <xref:System.TimeZoneInfo> klasy:

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  Ta metoda parametry mają wartość daty i godziny, aby dokonać konwersji, `TimeZoneInfo` obiekt, który reprezentuje strefy czasowej w wartości daty i godziny i `TimeZoneInfo` obiekt, który reprezentuje strefy czasowej można przekonwertować wartości daty i godziny do.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Ta metoda parametry są daty i czasu wartość do przekonwertowania, identyfikator daty i strefy czasowej z wartości godziny oraz identyfikator strefy czasowej można przekonwertować wartości daty i godziny, aby.

Obie metody wymagają, aby <xref:System.DateTime.Kind%2A> właściwości wartości daty i godziny, aby przekonwertować i <xref:System.TimeZoneInfo> identyfikator obiektu lub strefy czasowej, który reprezentuje jego strefa czasowa odnoszą się do siebie nawzajem. W przeciwnym razie <xref:System.ArgumentException> zgłaszany. Na przykład jeśli `Kind` właściwości wartości daty i godziny `DateTimeKind.Local`, jest zgłaszany wyjątek, jeśli `TimeZoneInfo` obiekt przekazany jako parametr do metody nie jest równa `TimeZoneInfo.Local`. Również jest zgłaszany wyjątek, jeśli identyfikator, który został przekazany jako parametr do metody nie jest równa `TimeZoneInfo.Local.Id`.

W poniższym przykładzie użyto <xref:System.TimeZoneInfo.ConvertTime%2A> metod konwertowania z Hawaje (czas standardowy) na czas lokalny.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Konwertowanie wartości DateTimeOffset

Wartości daty i godziny, które są reprezentowane przez <xref:System.DateTimeOffset> obiekty nie są w pełni strefy czasowej wiedzieć, ponieważ obiekt jest oddzielone od strefy czasowej w momencie konkretyzacji. Jednak w wielu przypadkach aplikacji po prostu musi przekonwertować datę i czas oparty na dwa różne przesunięcia względem czasu UTC, a nie na godzinę w szczególności stref czasowych. Aby wykonać tę konwersję, należy wywołać bieżącego wystąpienia <xref:System.DateTimeOffset.ToOffset%2A> metody. Pojedynczy parametr metody jest przesunięcie nowe wartość daty i godziny, metoda jest do zwrócenia.

Na przykład, jeśli data i godzina użytkownika żądanie dla strony sieci Web jest znany i jest serializowana jako ciąg w formacie MM/dd/rrrr hh: mm: zzzz, następujące `ReturnTimeOnServer` metoda konwertuje tej wartości daty i godziny na datę i godzinę na serwerze sieci Web.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Jeśli metoda jest przekazywany ciąg "1/9/2007 5:32:07-05: 00", która reprezentuje datę i godzinę w strefie czasowej pięć godziny wcześniejszy niż w formacie UTC, zwraca 1/9/2007 3:32:07: 00 -07:00 serwerem znajdującym się w Stanach Zjednoczonych Pacyficznego standardowa strefy czasowej.

<xref:System.TimeZoneInfo> Klasa zawiera także przeciążenia <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metodę, która wykonuje konwersjami stref czasowych przy użyciu <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> wartości. Parametry metody są <xref:System.DateTimeOffset> wartość i odwołania do strefy czasowej, do której ma być przekonwertowany czasu. Wywołanie metody zwraca <xref:System.DateTimeOffset> wartość. Na przykład `ReturnTimeOnServer` metody w poprzednim przykładzie można dopasować w następujący sposób, aby wywołać <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> metody.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Zobacz także

* <xref:System.TimeZoneInfo>
* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
* [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
