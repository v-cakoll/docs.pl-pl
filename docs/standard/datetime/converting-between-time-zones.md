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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b78e3985169954d71b479aa2e8a034f61afc01
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106967"
---
# <a name="converting-times-between-time-zones"></a>Konwertowanie czasów między strefami czasowymi

Staje się coraz bardziej ważna dla wszystkich aplikacji, które współdziałają z datami i godzinami w celu obsługi różnic między strefami czasowymi. Aplikacja nie może już zakładać, że wszystkie godziny mogą być wyrażone w lokalnym czasie, który jest czasem dostępnym ze <xref:System.DateTime> struktury. Na przykład strona sieci Web, która wyświetla bieżący czas w środkowej części Stany Zjednoczone nie będzie mieć wiarygodności dla klienta w Azji Wschodniej. W tym temacie wyjaśniono, jak konwertować czasy z jednej strefy czasowej na inną, a także jak <xref:System.DateTimeOffset> konwertować wartości, które mają ograniczoną świadomość strefy czasowej.

## <a name="converting-to-coordinated-universal-time"></a>Konwertowanie na uniwersalny czas koordynowany

Uniwersalny czas koordynowany (UTC) to standard czasu o dużej precyzji. Strefy czasowe na świecie są wyrażane jako dodatnie lub ujemne przesunięcia z czasu UTC. W ten sposób czas UTC zapewnia niezależny od strefy czasowej lub neutralną strefę czasową. Korzystanie z czasu UTC jest zalecane, gdy ważna jest data i godzina przenośna między komputerami. (Aby uzyskać szczegółowe informacje i inne najlepsze rozwiązania przy użyciu daty i godziny, zobacz [najlepsze rozwiązania dotyczące kodowania przy użyciu daty i godziny w .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10))). Przekonwertowanie poszczególnych stref czasowych na czas UTC ułatwia porównanie czasu.

> [!NOTE]
> Można również serializować <xref:System.DateTimeOffset> strukturę w sposób niejednoznaczny reprezentujący pojedynczy punkt w czasie. Ponieważ <xref:System.DateTimeOffset> obiekty przechowują wartość daty i godziny wraz z przesunięciem od czasu UTC, zawsze reprezentują określony punkt w czasie w zależności od czasu UTC.

Najprostszym sposobem przekonwertowania czasu na czas UTC jest wywołanie `static` metody (`Shared` w Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> . Dokładna konwersja wykonywana przez metodę zależy od wartości `dateTime` <xref:System.DateTime.Kind%2A> właściwości parametru, jak pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Konwertuje czas lokalny na UTC.                                                    |
| `DateTimeKind.Unspecified` | Przyjęto `dateTime` , że parametr jest czasem lokalnym i konwertuje czas lokalny na UTC. |
| `DateTimeKind.Utc`         | `dateTime` Zwraca parametr bez zmian.                                    |

Poniższy kod konwertuje bieżący czas lokalny na UTC i wyświetla wynik w konsoli programu.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Jeśli wartość daty i godziny nie reprezentuje czasu lokalnego lub czasu UTC, <xref:System.DateTime.ToUniversalTime%2A> Metoda prawdopodobnie zwróci błędny wynik. Można jednak użyć <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metody, aby przekonwertować datę i godzinę z określonej strefy czasowej. (Aby uzyskać szczegółowe informacje na <xref:System.TimeZoneInfo> temat pobierania obiektu, który reprezentuje docelową strefę czasową, zobacz [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)). Poniższy kod używa <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> metody do konwersji wschodniego czasu standardowego na UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Należy zauważyć, że ta metoda <xref:System.ArgumentException> zgłasza, <xref:System.DateTime> Jeśli <xref:System.DateTime.Kind%2A> właściwość obiektu i strefa czasowa są niezgodne. Niezgodność <xref:System.DateTime.Kind%2A> występuje <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType> <xref:System.DateTime.Kind%2A> ,jeśli<xref:System.DateTimeKind.Local?displayProperty=nameWithType> właściwość jest, ale obiekt nie reprezentuje lokalnej strefy czasowej lub jeśli właściwość jest, ale obiektniejestrówny.<xref:System.TimeZoneInfo>

Wszystkie te metody przyjmują <xref:System.DateTime> wartości jako parametry i <xref:System.DateTime> zwracają wartość. W <xref:System.DateTimeOffset> przypadku wartości <xref:System.DateTimeOffset> struktura ma <xref:System.DateTimeOffset.ToUniversalTime%2A> metodę wystąpienia, która konwertuje datę i godzinę bieżącego wystąpienia na czas UTC. Poniższy przykład wywołuje <xref:System.DateTimeOffset.ToUniversalTime%2A> metodę w celu przekonwertowania czasu lokalnego i kilku innych czasów na uniwersalny czas koordynowany (UTC).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Konwertowanie czasu UTC na wydaną strefę czasową

Aby skonwertować czasu UTC na czas lokalny, zapoznaj się z sekcją "Konwertowanie czasu UTC na czas lokalny" poniżej. Aby skonwertować czas UTC na godzinę w dowolnej wyznaczonej strefie czasowej, wywołaj <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> metodę. Metoda przyjmuje dwa parametry:

- Czas UTC do przekonwertowania. Musi to być <xref:System.DateTime> wartość, której <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na `Unspecified` lub `Utc`.

- Strefa czasowa do przekonwertowania czasu UTC na.

Poniższy kod konwertuje czas UTC do centralnego czasu standardowego.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Konwertowanie czasu UTC na czas lokalny

Aby skonwertować czasu UTC na czas lokalny, wywołaj <xref:System.DateTime.ToLocalTime%2A> metodę <xref:System.DateTime> obiektu, którego czas chcesz skonwertować. Dokładne zachowanie metody zależy od wartości <xref:System.DateTime.Kind%2A> właściwości obiektu, jak pokazano w poniższej tabeli.

| `DateTime.Kind`            | Konwersja                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | <xref:System.DateTime> Zwraca wartość bez zmian.                                      |
| `DateTimeKind.Unspecified` | Przyjęto założenie, że <xref:System.DateTime> wartość jest UTC i konwertowany czasu UTC na czas lokalny. |
| `DateTimeKind.Utc`         | <xref:System.DateTime> Konwertuje wartość na czas lokalny.                                 |

> [!NOTE]
> Metoda zachowuje się identycznie z `DateTime.ToLocalTime`metodą. <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> Przyjmuje jeden parametr, który jest wartością daty i godziny do przekonwertowania.

Możesz również skonwertować czas w każdej określonej strefie czasowej na czas lokalny przy użyciu `static` metody (`Shared` w Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> . Ta technika została omówiona w następnej sekcji.

## <a name="converting-between-any-two-time-zones"></a>Konwertowanie między dowolnymi dwiema strefami czasowymi

Można dokonać konwersji między dowolnymi dwoma strefami czasowymi przy użyciu jednej `static` z`Shared` następujących dwóch metod (w <xref:System.TimeZoneInfo> Visual Basic) klasy:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Parametry tej metody to wartość daty i godziny do przekonwertowania, `TimeZoneInfo` obiekt, który reprezentuje strefę czasową wartości daty i godziny `TimeZoneInfo` oraz obiekt, który reprezentuje strefę czasową do przekonwertowania wartości daty i godziny na.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Parametry tej metody są wartościami daty i godziny do przekonwertowania, identyfikatorem strefy czasowej wartości daty i godziny oraz identyfikatorem strefy czasowej do przekonwertowania wartości daty i godziny na.

Obie metody wymagają, <xref:System.DateTime.Kind%2A> aby Właściwość daty i godziny była konwertowana <xref:System.TimeZoneInfo> oraz identyfikator obiektu lub strefy czasowej, który reprezentuje strefę czasową, odpowiada siebie. W przeciwnym razie jest zgłaszany. <xref:System.ArgumentException> Na przykład jeśli `Kind` Właściwość daty i godziny ma `DateTimeKind.Local`wartość, `TimeZoneInfo` wyjątek jest zgłaszany, jeśli obiekt przeszedł jako `TimeZoneInfo.Local`parametr do metody nie jest równy. Wyjątek jest zgłaszany również wtedy, gdy identyfikator przesłany jako parametr do metody nie jest równy `TimeZoneInfo.Local.Id`.

W poniższym przykładzie użyto <xref:System.TimeZoneInfo.ConvertTime%2A> metody do konwersji z "hawajski" czasu standardowego na czas lokalny.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Konwertowanie wartości DateTimeOffset

Wartości daty i godziny reprezentowane przez <xref:System.DateTimeOffset> obiekty nie są w pełni obsługiwane przez strefę, ponieważ obiekt jest nieskojarzony ze strefą czasową podczas tworzenia wystąpienia. Jednak w wielu przypadkach aplikacja po prostu musi przekonwertować datę i godzinę na podstawie dwóch różnych przesunięć od czasu UTC, a nie w określonych strefach czasowych. Aby wykonać tę konwersję, można wywołać <xref:System.DateTimeOffset.ToOffset%2A> metodę bieżącego wystąpienia. Pojedynczy parametr metody jest przesunięciem nowej wartości daty i godziny, która ma zostać zwrócona przez metodę.

Jeśli na przykład data i godzina żądania użytkownika dla strony sieci Web jest znana i jest serializowana jako ciąg w formacie mm/dd/rrrr hh: mm: SS zzzz, następująca `ReturnTimeOnServer` Metoda konwertuje wartość daty i godziny na serwer sieci Web.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Jeśli metoda jest przenoszona jako ciąg "9/1/2007 5:32:07 -05:00", który reprezentuje datę i godzinę w strefie czasowej 5 godzin wcześniejszą niż UTC, zwraca 9/1/2007 3:32:07 AM-07:00 dla serwera znajdującego się w Stanach Zjednoczonych Standardowa strefa czasowa (pacyficzny).

Klasa zawiera również Przeciążenie <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody, która wykonuje konwersje strefy czasowej z <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> wartościami. <xref:System.TimeZoneInfo> Parametry metody są <xref:System.DateTimeOffset> wartością i odwołaniem do strefy czasowej, do której ma zostać przekonwertowany czas. Wywołanie metody zwraca <xref:System.DateTimeOffset> wartość. Na przykład `ReturnTimeOnServer` metodę w poprzednim przykładzie można napisać ponownie w następujący sposób, aby <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> wywołać metodę.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.TimeZoneInfo>
- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
