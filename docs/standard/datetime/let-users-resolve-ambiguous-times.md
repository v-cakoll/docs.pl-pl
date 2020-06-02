---
title: 'Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: ac723738d80a2f686a5fcaf279cec791b3c58619
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281586"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC). Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego. Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:

- Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.

- Założenie założeń dotyczących sposobu mapowania czasu na czas UTC. Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.

W tym temacie pokazano, jak zezwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby pozwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu

1. Pobierz datę i godzinę wprowadzania danych przez użytkownika.

2. Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczny.

3. Jeśli czas jest niejednoznaczny, wywołaj <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodę, aby pobrać tablicę <xref:System.TimeSpan> obiektów. Każdy element w tablicy zawiera przesunięcie czasu UTC, do którego można mapować niejednoznaczny czas.

4. Zezwalaj użytkownikowi na wybranie żądanego przesunięcia.

5. Pobierz datę i godzinę UTC, odejmując przesunięcie wybrane przez użytkownika od czasu lokalnego.

6. Wywołaj `static` `Shared` metodę (w Visual Basic .NET), <xref:System.DateTime.SpecifyKind%2A> Aby ustawić właściwość Data i godzina UTC <xref:System.DateTime.Kind%2A> na wartość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="example"></a>Przykład

Poniższy przykład powoduje, że użytkownik wprowadza datę i godzinę oraz, jeśli jest niejednoznaczny, umożliwia użytkownikowi wybranie czasu UTC, który jest mapowany na.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Rdzeń przykładowego kodu używa tablicy <xref:System.TimeSpan> obiektów, aby wskazać możliwe przesunięcie niejednoznaczny czas od czasu UTC. Jednak te przesunięcia są mało znaczące dla użytkownika. Aby wyjaśnić znaczenie przesunięć, kod również zawiera informacje o tym, czy przesunięcie reprezentuje czas standardowy czasu standardowego lub czasu letniego. Kod określa, który czas jest standardowy i czas jest okresowy, porównując przesunięcie z wartością <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości. Ta właściwość wskazuje różnicę między czasem UTC i strefą czasową (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone przez <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwość; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu. Jest to zalecane rozwiązanie, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że <xref:System> przestrzeń nazw ma zostać zaimportowana przy użyciu `using` instrukcji (wymaganej w kodzie C#).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu](resolve-ambiguous-times.md)
