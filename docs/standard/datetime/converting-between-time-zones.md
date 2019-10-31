---
title: Konwertowanie czasów między strefami czasowymi
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
ms.openlocfilehash: d0b38523f054598ba6fb1f05a0183bc4ccff2120
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132567"
---
# <a name="converting-times-between-time-zones"></a>Konwertowanie czasów między strefami czasowymi

Staje się coraz bardziej ważna dla wszystkich aplikacji, które współdziałają z datami i godzinami w celu obsługi różnic między strefami czasowymi. Aplikacja nie może już przyjąć, że wszystkie godziny mogą być wyrażone w lokalnym czasie, który jest czasem dostępnym w strukturze <xref:System.DateTime>. Na przykład strona sieci Web, która wyświetla bieżący czas w środkowej części Stany Zjednoczone nie będzie mieć wiarygodności dla klienta w Azji Wschodniej. W tym temacie wyjaśniono, jak konwertować czasy z jednej strefy czasowej na inną, a także jak konwertować wartości <xref:System.DateTimeOffset>, które mają ograniczoną świadomość strefy czasowej.

## <a name="converting-to-coordinated-universal-time"></a>Konwertowanie na uniwersalny czas koordynowany

Uniwersalny czas koordynowany (UTC) to standard czasu o dużej precyzji. Strefy czasowe na świecie są wyrażane jako dodatnie lub ujemne przesunięcia z czasu UTC. W ten sposób czas UTC zapewnia niezależny od strefy czasowej lub neutralną strefę czasową. Korzystanie z czasu UTC jest zalecane, gdy ważna jest data i godzina przenośna między komputerami. (Aby uzyskać szczegółowe informacje i inne najlepsze rozwiązania przy użyciu daty i godziny, zobacz [najlepsze rozwiązania dotyczące kodowania przy użyciu daty i godziny w .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10))). Przekonwertowanie poszczególnych stref czasowych na czas UTC ułatwia porównanie czasu.

> [!NOTE]
> Można również serializować strukturę <xref:System.DateTimeOffset>, aby jednoznacznie reprezentował pojedynczy punkt w czasie. Ponieważ obiekty <xref:System.DateTimeOffset> przechowują wartości daty i godziny wraz z przesunięciami od czasu UTC, zawsze reprezentują określony punkt w czasie w zależności od czasu UTC.

Najprostszym sposobem przekonwertowania czasu na czas UTC jest wywołanie `static` (`Shared` w Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> metodzie. Dokładna konwersja wykonywana przez metodę zależy od wartości właściwości <xref:System.DateTime.Kind%2A> parametru `dateTime`, jak pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Konwertuje czas lokalny na UTC.                                                    |
| `DateTimeKind.Unspecified` | Przyjęto, że parametr `dateTime` jest czasem lokalnym i konwertuje czas lokalny na UTC. |
| `DateTimeKind.Utc`         | Zwraca parametr `dateTime` bez zmian.                                    |

Poniższy kod konwertuje bieżący czas lokalny na UTC i wyświetla wynik w konsoli programu.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Jeśli wartość daty i godziny nie reprezentuje czasu lokalnego lub UTC, Metoda <xref:System.DateTime.ToUniversalTime%2A> prawdopodobnie zwróci błędny wynik. Można jednak użyć metody <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>, aby przekonwertować datę i godzinę z określonej strefy czasowej. (Aby uzyskać szczegółowe informacje na temat pobierania obiektu <xref:System.TimeZoneInfo>, który reprezentuje docelową strefę czasową, zobacz [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)). Poniższy kod używa metody <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>, aby skonwertować Wschodni czas standardowy na UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Należy zauważyć, że ta metoda zgłasza <xref:System.ArgumentException>, jeśli właściwość <xref:System.DateTime.Kind%2A> obiektu <xref:System.DateTime> i strefa czasowa są niezgodne. Występuje niezgodność, jeśli właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, ale obiekt <xref:System.TimeZoneInfo> nie reprezentuje lokalnej strefy czasowej lub jeśli właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, ale obiekt <xref:System.TimeZoneInfo> nie jest równy <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.

Wszystkie te metody przyjmują <xref:System.DateTime> wartości jako parametry i zwracają <xref:System.DateTime> wartość. W przypadku wartości <xref:System.DateTimeOffset> struktura <xref:System.DateTimeOffset> ma metodę wystąpienia <xref:System.DateTimeOffset.ToUniversalTime%2A>, która konwertuje datę i godzinę bieżącego wystąpienia na czas UTC. Poniższy przykład wywołuje metodę <xref:System.DateTimeOffset.ToUniversalTime%2A>, aby skonwertować czas lokalny i kilka innych czasów na uniwersalny czas koordynowany (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Konwertowanie czasu UTC na wydaną strefę czasową

Aby skonwertować czasu UTC na czas lokalny, zapoznaj się z sekcją "Konwertowanie czasu UTC na czas lokalny" poniżej. Aby przekonwertować czas UTC na godzinę w dowolnej wyznaczonej strefie czasowej, wywołaj metodę <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>. Metoda przyjmuje dwa parametry:

- Czas UTC do przekonwertowania. Musi to być <xref:System.DateTime> wartość, której Właściwość <xref:System.DateTime.Kind%2A> ma wartość `Unspecified` lub `Utc`.

- Strefa czasowa do przekonwertowania czasu UTC na.

Poniższy kod konwertuje czas UTC do centralnego czasu standardowego.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Konwertowanie czasu UTC na czas lokalny

Aby skonwertować czasu UTC na czas lokalny, wywołaj metodę <xref:System.DateTime.ToLocalTime%2A> obiektu <xref:System.DateTime>, którego czas chcesz skonwertować. Dokładne zachowanie metody zależy od wartości właściwości <xref:System.DateTime.Kind%2A> obiektu, jak pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Zwraca wartość <xref:System.DateTime> bez zmian.                                      |
| `DateTimeKind.Unspecified` | Przyjęto założenie, że wartość <xref:System.DateTime> jest UTC i konwertuje godzinę UTC na czas lokalny. |
| `DateTimeKind.Utc`         | Konwertuje wartość <xref:System.DateTime> na czas lokalny.                                 |

> [!NOTE]
> Metoda <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> zachowuje się identycznie z metodą `DateTime.ToLocalTime`. Przyjmuje jeden parametr, który jest wartością daty i godziny do przekonwertowania.

Możesz również skonwertować czas w każdej określonej strefie czasowej na czas lokalny przy użyciu metody <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> `static` (`Shared` w Visual Basic). Ta technika została omówiona w następnej sekcji.

## <a name="converting-between-any-two-time-zones"></a>Konwertowanie między dowolnymi dwiema strefami czasowymi

Można dokonać konwersji między dowolnymi dwiema strefami czasowymi przy użyciu jednej z następujących dwóch metod `static` (`Shared` w Visual Basic) klasy <xref:System.TimeZoneInfo>:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Parametry tej metody to wartość daty i godziny do przekonwertowania, obiekt `TimeZoneInfo`, który reprezentuje strefę czasową wartości daty i godziny oraz obiekt `TimeZoneInfo`, który reprezentuje strefę czasową do przekonwertowania wartości daty i godziny na.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Parametry tej metody są wartościami daty i godziny do przekonwertowania, identyfikatorem strefy czasowej wartości daty i godziny oraz identyfikatorem strefy czasowej do przekonwertowania wartości daty i godziny na.

Obie metody wymagają, aby Właściwość <xref:System.DateTime.Kind%2A> wartości daty i godziny była konwertowana, a obiekt <xref:System.TimeZoneInfo> lub Identyfikator strefy czasowej, który reprezentuje strefę czasową, odpowiada siebie. W przeciwnym razie zostanie zgłoszony <xref:System.ArgumentException>. Na przykład jeśli właściwość `Kind` wartości daty i godziny jest `DateTimeKind.Local`, zostanie zgłoszony wyjątek, jeśli obiekt `TimeZoneInfo` przeszedł jako parametr do metody nie jest równy `TimeZoneInfo.Local`. Wyjątek jest zgłaszany również wtedy, gdy identyfikator przesłany jako parametr do metody nie jest równy `TimeZoneInfo.Local.Id`.

W poniższym przykładzie użyto metody <xref:System.TimeZoneInfo.ConvertTime%2A>, aby konwertować z "hawajski czas standardowy na czas lokalny.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Konwertowanie wartości DateTimeOffset

Wartości daty i godziny reprezentowane przez <xref:System.DateTimeOffset> obiekty nie są w pełni obsługiwane w strefie czasowej, ponieważ obiekt jest nieskojarzony ze strefą czasową podczas tworzenia wystąpienia. Jednak w wielu przypadkach aplikacja po prostu musi przekonwertować datę i godzinę na podstawie dwóch różnych przesunięć od czasu UTC, a nie w określonych strefach czasowych. Aby wykonać tę konwersję, można wywołać metodę <xref:System.DateTimeOffset.ToOffset%2A> bieżącego wystąpienia. Pojedynczy parametr metody jest przesunięciem nowej wartości daty i godziny, która ma zostać zwrócona przez metodę.

Jeśli na przykład data i godzina żądania użytkownika dla strony sieci Web jest znana i jest serializowana jako ciąg w formacie MM/dd/rrrr hh: mm: SS zzzz, Poniższa metoda `ReturnTimeOnServer` konwertuje tę datę i godzinę na serwer sieci Web.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Jeśli metoda jest przenoszona jako ciąg "9/1/2007 5:32:07 -05:00", który reprezentuje datę i godzinę w strefie czasowej 5 godzin wcześniejszą niż UTC, zwraca 9/1/2007 3:32:07 AM-07:00 dla serwera znajdującego się w strefie czasowej w Stanach Zjednoczonych w warstwie Standardowa.

Klasa <xref:System.TimeZoneInfo> obejmuje również Przeciążenie metody <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>, która wykonuje konwersje stref czasowych z wartościami <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>. Parametry metody są wartością <xref:System.DateTimeOffset> i odwołaniem do strefy czasowej, do której ma zostać przekonwertowany czas. Wywołanie metody zwraca wartość <xref:System.DateTimeOffset>. Na przykład metodę `ReturnTimeOnServer` w poprzednim przykładzie można napisać ponownie w następujący sposób, aby wywołać metodę <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.TimeZoneInfo>
- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
