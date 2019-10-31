---
title: 'Instrukcje: pozwalanie użytkownikom na rozwiązywanie niejednoznacznych godzin'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: f988616a4b2a5d8202c87e3be3cb23c7f9f1f130
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122274"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Instrukcje: pozwalanie użytkownikom na rozwiązywanie niejednoznacznych godzin

Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC). Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego. Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:

- Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.

- Założenie założeń dotyczących sposobu mapowania czasu na czas UTC. Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.

W tym temacie pokazano, jak zezwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby pozwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu

1. Pobierz datę i godzinę wprowadzania danych przez użytkownika.

2. Wywołaj metodę <xref:System.TimeZoneInfo.IsAmbiguousTime%2A>, aby określić, czy czas jest niejednoznaczny.

3. Jeśli czas jest niejednoznaczny, wywołaj metodę <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>, aby pobrać tablicę obiektów <xref:System.TimeSpan>. Każdy element w tablicy zawiera przesunięcie czasu UTC, do którego można mapować niejednoznaczny czas.

4. Zezwalaj użytkownikowi na wybranie żądanego przesunięcia.

5. Pobierz datę i godzinę UTC, odejmując przesunięcie wybrane przez użytkownika od czasu lokalnego.

6. Wywołaj metodę <xref:System.DateTime.SpecifyKind%2A> `static` (`Shared` w Visual Basic .NET), aby ustawić właściwość <xref:System.DateTime.Kind%2A> wartości daty i godziny UTC na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład powoduje, że użytkownik wprowadza datę i godzinę oraz, jeśli jest niejednoznaczny, umożliwia użytkownikowi wybranie czasu UTC, który jest mapowany na.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Rdzeń przykładowego kodu używa tablicy obiektów <xref:System.TimeSpan>, aby wskazać możliwe przesunięcie niejednoznaczny czas od czasu UTC. Jednak te przesunięcia są mało znaczące dla użytkownika. Aby wyjaśnić znaczenie przesunięć, kod również zawiera informacje o tym, czy przesunięcie reprezentuje czas standardowy czasu standardowego lub czasu letniego. Kod określa, który czas jest standardowy i czas jest okresowy, porównując przesunięcie z wartością właściwości <xref:System.TimeZoneInfo.BaseUtcOffset%2A>. Ta właściwość wskazuje różnicę między czasem UTC i strefą czasową (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone za pomocą właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu. Jest to zalecane rozwiązanie, ponieważ wywołanie metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Przestrzeń nazw <xref:System> zostać zaimportowana przy użyciu instrukcji `using` (wymagane C# w kodzie).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md)
