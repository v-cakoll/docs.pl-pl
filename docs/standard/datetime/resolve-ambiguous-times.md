---
title: 'Instrukcje: Rozwiązywanie niejednoznacznych czasów'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122248"
---
# <a name="how-to-resolve-ambiguous-times"></a>Instrukcje: Rozwiązywanie niejednoznacznych czasów

Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC). Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego. Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:

- Założenie założeń dotyczących sposobu mapowania czasu na czas UTC. Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.

- Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.

W tym temacie pokazano, jak rozpoznać niejednoznaczny czas przez założenie, że reprezentuje czas standardowy strefy czasowej.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Aby zamapować niejednoznaczny czas na czas standardowy strefy czasowej

1. Wywołaj metodę <xref:System.TimeZoneInfo.IsAmbiguousTime%2A>, aby określić, czy czas jest niejednoznaczny.

2. Jeśli czas jest niejednoznaczny, Odejmij czas od obiektu <xref:System.TimeSpan> zwróconego przez właściwość <xref:System.TimeZoneInfo.BaseUtcOffset%2A> strefy czasowej.

3. Wywołaj metodę <xref:System.DateTime.SpecifyKind%2A> `static` (`Shared` w Visual Basic .NET), aby ustawić właściwość <xref:System.DateTime.Kind%2A> wartości daty i godziny UTC na <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konwertowania niejednoznacznego czasu na czas UTC przez założenie, że reprezentuje on lokalną strefę czasową.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Przykład składa się z metody o nazwie `ResolveAmbiguousTime`, która określa, czy <xref:System.DateTime> wartość jest niejednoznaczna. Jeśli wartość jest niejednoznaczna, metoda zwraca wartość <xref:System.DateTime>, która reprezentuje odpowiadający czas UTC. Metoda obsługuje tę konwersję poprzez odjęcie wartości właściwości <xref:System.TimeZoneInfo.BaseUtcOffset%2A> lokalnej strefy czasowej od czasu lokalnego.

Zwykle niejednoznaczny czas jest obsługiwany przez wywołanie metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>, aby pobrać tablicę obiektów <xref:System.TimeSpan>, które zawierają niejednoznaczne możliwe przesunięcia czasu UTC. Jednak w tym przykładzie to arbitralne założenie, że niejednoznaczny czas powinien być zawsze mapowany do czasu standardowego strefy czasowej. Właściwość <xref:System.TimeZoneInfo.BaseUtcOffset%2A> zwraca przesunięcie między czasem UTC a czasem standardowym.

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone za pomocą właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu. Jest to zalecane rozwiązanie, ponieważ wywołanie metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Przestrzeń nazw <xref:System> zostać zaimportowana przy użyciu instrukcji `using` (wymagane C# w kodzie).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
