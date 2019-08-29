---
title: 'Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf97f1a08c6df13ce639466fc07472926c63987f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106623"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC). Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego. Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:

- Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.

- Założenie założeń dotyczących sposobu mapowania czasu na czas UTC. Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.

W tym temacie pokazano, jak zezwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby pozwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu

1. Pobierz datę i godzinę wprowadzania danych przez użytkownika.

2. Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczny.

3. Jeśli czas jest niejednoznaczny, wywołaj <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodę, aby pobrać <xref:System.TimeSpan> tablicę obiektów. Każdy element w tablicy zawiera przesunięcie czasu UTC, do którego można mapować niejednoznaczny czas.

4. Zezwalaj użytkownikowi na wybranie żądanego przesunięcia.

5. Pobierz datę i godzinę UTC, odejmując przesunięcie wybrane przez użytkownika od czasu lokalnego.

6. `Shared` <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTime.Kind%2A> Wywołaj metodę <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>(w Visual Basic .NET), aby ustawić właściwość Data i godzina UTC na wartość. `static`

## <a name="example"></a>Przykład

Poniższy przykład powoduje, że użytkownik wprowadza datę i godzinę oraz, jeśli jest niejednoznaczny, umożliwia użytkownikowi wybranie czasu UTC, który jest mapowany na.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Rdzeń przykładowego kodu używa tablicy <xref:System.TimeSpan> obiektów, aby wskazać możliwe przesunięcie niejednoznaczny czas od czasu UTC. Jednak te przesunięcia są mało znaczące dla użytkownika. Aby wyjaśnić znaczenie przesunięć, kod również zawiera informacje o tym, czy przesunięcie reprezentuje czas standardowy czasu standardowego lub czasu letniego. Kod określa, który czas jest standardowy i czas jest okresowy, porównując przesunięcie z wartością <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości. Ta właściwość wskazuje różnicę między czasem UTC i strefą czasową (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone przez <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwość; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu. Jest to zalecane rozwiązanie, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System>

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Rozwiązywanie niejednoznacznych czasów](../../../docs/standard/datetime/resolve-ambiguous-times.md)
