---
title: "Konwertowanie godzin między strefami czasowymi"
ms.custom: 
ms.date: 04/10/2017
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
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eabe0c1511e6fd42798f1a879e9e8d526d543a29
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="converting-times-between-time-zones"></a>Konwertowanie godzin między strefami czasowymi

Staje się coraz bardziej ważne dla każdej aplikacji, która współdziała z daty i godziny do obsługi różnic między strefami czasowymi. Aplikacji nie będzie można założyć, że zawsze może zostać wyrażona w czasie lokalnym czyli czas dostępne z <xref:System.DateTime> struktury. Na przykład strony sieci Web, który wyświetla bieżący czas wschodni części Stanów Zjednoczonych będzie braku wiarygodności z klientem w Azja Wschodnia. W tym temacie wyjaśniono, jak przekonwertować godzin między strefami czasowymi, a także sposób konwertowania <xref:System.DateTimeOffset> wartości, które mają ograniczoną świadomości strefy czasowej.

## <a name="converting-to-coordinated-universal-time"></a>Konwertowanie na uniwersalny czas koordynowany

Uniwersalny czas koordynowany (UTC) jest wysokiej precyzji, atomic czasu standardowego. Strefy czasowe na świecie są wyrażane jako dodatnie lub ujemne przesunięcie od czasu UTC. W związku z tym UTC zapewnia rodzaj strefy czasowej wolnego lub strefy czasowej niezależnym od czasu. Użycie czasu UTC jest zalecane w przypadku Data i przenośność czasu na komputerach jest ważna. (Szczegółowe informacje i innych najlepszych rozwiązań za pomocą dat i godzin, zobacz [kodowania najlepszych rozwiązań za pomocą daty/godziny w programie .NET Framework](https://msdn.microsoft.com/library/ms973825.aspx).) Konwertowanie poszczególnych stref czasowych UTC ułatwia czas porównania.

> [!NOTE]
> Można również serializować <xref:System.DateTimeOffset> struktury w celu jego jednoznacznej reprezentują pojedynczy punkt w czasie. Ponieważ <xref:System.DateTimeOffset> obiektów przechowywanie wartości daty i godziny wraz z jego przesunięcie od czasu UTC, zawsze reprezentują określonego punktu w czasie w relacji do czasu UTC.

Najprostszym sposobem skonwertować godzinę na czas UTC jest wywołać `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> metody. Dokładne konwersji wykonywane przez metodę zależy od wartości `dateTime` parametru <xref:System.DateTime.Kind%2A> właściwości, jak to pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Konwertuje lokalnego czasu na czas UTC.                                                    |
| `DateTimeKind.Unspecified` | Założono `dateTime` parametr jest czasem lokalnym i konwertuje czasu lokalnego na czas UTC. |
| `DateTimeKind.Utc`         | Zwraca `dateTime` parametru bez zmian.                                    |

Poniższy kod konwertuje bieżący czas lokalny na czas UTC i wyświetla wyniki w konsoli.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> — Metoda nie zwraca wyników, które są takie same jak <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType> i <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> metody. Jeśli system hosta lokalnego strefy czasowej zawiera wiele reguł korygowania, <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> stosuje odpowiednią regułę do określonej daty i godziny. Te dwie metody zawsze Stosuj najnowsze reguła korekty.

Jeśli wartość daty i godziny nie reprezentuje czas lokalny albo UTC, <xref:System.DateTime.ToUniversalTime%2A> metody prawdopodobnie będzie zwracać błędne wyniki. Można jednak użyć <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metodę, aby przekonwertować datę i godzinę z określonej strefy czasowej. (Aby uzyskać szczegółowe informacje na pobieranie <xref:System.TimeZoneInfo> obiekt, który reprezentuje strefę czasową docelowym, zobacz [znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Poniższy kod używa <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metodę, aby przekonwertować wschodni czas standardowy na czas UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Należy pamiętać, że ta metoda zgłasza <xref:System.ArgumentException> Jeśli <xref:System.DateTime> obiektu <xref:System.DateTime.Kind%2A> właściwości i strefy czasowej są niezgodne. Występuje niezgodność, jeśli <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind?displayProperty=nameWithType> , ale <xref:System.TimeZoneInfo> obiekt nie reprezentuje w lokalnej strefie czasowej, lub jeśli <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind?displayProperty=nameWithType> , ale <xref:System.TimeZoneInfo> obiektu nie jest równa <xref:System.DateTimeKind?displayProperty=nameWithType>.

Wszystkie te metody zająć <xref:System.DateTime> wartości jako parametry i zwracane <xref:System.DateTime> wartość. Dla <xref:System.DateTimeOffset> wartości, <xref:System.DateTimeOffset> ma struktury <xref:System.DateTimeOffset.ToUniversalTime%2A> wystąpienia metody, który konwertuje datę i godzinę bieżącego wystąpienia na czas UTC. Następujące przykładowe wywołania <xref:System.DateTimeOffset.ToUniversalTime%2A> metodę, aby przekonwertować czasem lokalnym i kilka innych razy uniwersalny czas koordynowany (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Konwertowanie wyznaczonych strefę czasową UTC

Aby przekonwertować UTC na czas lokalny, w sekcji "Konwertowanie UTC na czas lokalny" poniżej. Aby przekonwertować w dowolnej strefie czasowej wyznaczony czas UTC, należy wywołać <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> metody. Metoda przyjmuje dwa parametry:

* Czas UTC do konwersji. Musi to być <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na `Unspecified` lub `Utc`.

* Strefę czasową UTC, aby przekonwertować.

Poniższy kod konwertuje UTC Środkowa (czas standardowy).

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Konwertowanie UTC na czas lokalny

Aby przekonwertować UTC na czas lokalny, należy wywołać <xref:System.DateTime.ToLocalTime%2A> metody <xref:System.DateTime> obiektu których czas, który chcesz przekonwertować. Dokładne zachowanie metody zależy od wartości obiektu <xref:System.DateTime.Kind%2A> właściwości, jak to pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Zwraca <xref:System.DateTime> wartości bez zmian.                                      |
| `DateTimeKind.Unspecified` | Zakłada się, że <xref:System.DateTime> wartość jest UTC i konwertuje UTC na czas lokalny. |
| `DateTimeKind.Utc`         | Konwertuje <xref:System.DateTime> wartość na czas lokalny.                                 |

> [!NOTE]
> <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Metody zachowuje się tak samo `DateTime.ToLocalTime` metody. Trwa jeden parametr, który jest wartość daty i godziny do przekonwertowania.

Czas w strefie czasowej, wszelkie wyznaczonych można przekonwertować na czas lokalny, przy użyciu `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> metody. Ta technika jest omówiona w następnej sekcji.

## <a name="converting-between-any-two-time-zones"></a>Konwertowanie pomiędzy żadnych dwie strefy czasowe

Można konwertować między żadnych dwóch stref czasowych przy użyciu jednej z następujących dwóch `static` (`Shared` w języku Visual Basic) metody <xref:System.TimeZoneInfo> klasy:

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  Parametry tej metody jest wartość daty i godziny, aby dokonać konwersji, `TimeZoneInfo` obiekt, który reprezentuje strefę czasową wartości daty i godziny, a `TimeZoneInfo` obiekt, który reprezentuje można przekonwertować wartości daty i godziny na strefę czasową.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Ta metoda parametry są daty i czasu wartości do konwersji, identyfikator daty i strefy czasowej wartość czasu i identyfikator strefy czasowej, można przekonwertować wartości daty i godziny na.

Obie metody wymagają, aby <xref:System.DateTime.Kind%2A> właściwości wartości daty i godziny do konwersji i <xref:System.TimeZoneInfo> identyfikator obiektu lub strefy czasowej, który reprezentuje jego strefa czasowa odpowiadają sobie nawzajem. W przeciwnym razie <xref:System.ArgumentException> jest generowany. Na przykład jeśli `Kind` właściwość wartość daty i godziny jest `DateTimeKind.Local`, jest zwracany wyjątek, jeśli `TimeZoneInfo` obiekt przekazany jako parametr do metody nie jest równa `TimeZoneInfo.Local`. Również jest zgłaszany wyjątek, jeśli identyfikator przekazany jako parametr do metody nie jest równa `TimeZoneInfo.Local.Id`.

W poniższym przykładzie użyto <xref:System.TimeZoneInfo.ConvertTime%2A> do przekonwertowania na czas lokalny z Hawaje (czas standardowy).

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Konwertowanie wartości DateTimeOffset

Wartości daty i godziny reprezentowany przez <xref:System.DateTimeOffset> obiekty nie są w pełni strefy czasowej wiedzieć, ponieważ obiekt jest oddzielone od strefy czasowej w czasie zostanie on uruchomiony. Jednak w wielu przypadkach aplikacji wystarczy przekonwertować daty i czasu oparte na dwie różne przesunięcia od czasu UTC, a nie na czas w szczególności stref czasowych. Aby wykonać tę konwersję, należy wywołać bieżącego wystąpienia <xref:System.DateTimeOffset.ToOffset%2A> metody. Pojedynczy parametr metody jest przesunięcie Nowa data i metoda ma zwrócić wartość czasu.

Na przykład, jeśli data i godzina użytkownika żądania dla strony sieci Web jest znany i jest szeregowana jako ciąg w formacie MM/dd/rrrr gg zzzz, następujące `ReturnTimeOnServer` metoda konwertuje ta wartość daty i godziny, Data i godzina na serwerze sieci Web.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Jeśli metoda jest przekazywana ciąg "1-9/2007 5:32:07-05: 00", który reprezentuje datę i godzinę w strefie czasowej pięć godziny wcześniejszy niż czas UTC, zwraca 1-9/2007 3:32:07 AM-07: 00 serwera znajduje się w Stanach Zjednoczonych Pacyficzny standardowa strefy czasowej.

<xref:System.TimeZoneInfo> Klasa zawiera także przeciążenia <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metodę, która wykonuje konwersji strefy czasowej z <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> wartości. Parametry metody są <xref:System.DateTimeOffset> wartość i odwołanie do strefy czasowej czasu jest ma zostać przekonwertowany. Wywołanie metody zwraca <xref:System.DateTimeOffset> wartość. Na przykład `ReturnTimeOnServer` metody w poprzednim przykładzie można w następujący sposób ulegną wywołać <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> metody.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Zobacz także

<xref:System.TimeZoneInfo>[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
