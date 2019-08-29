---
title: 'Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e98d5d8240492ca30da2825b72277d7a35f97f6
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106785"
---
# <a name="how-to-resolve-ambiguous-times"></a>Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC). Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego. Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:

- Założenie założeń dotyczących sposobu mapowania czasu na czas UTC. Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.

- Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.

W tym temacie pokazano, jak rozpoznać niejednoznaczny czas przez założenie, że reprezentuje czas standardowy strefy czasowej.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Aby zamapować niejednoznaczny czas na czas standardowy strefy czasowej

1. Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczny.

2. Jeśli czas jest niejednoznaczny, Odejmij czas od <xref:System.TimeSpan> obiektu zwróconego przez <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Właściwość strefy czasowej.

3. `Shared` <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTime.Kind%2A> Wywołaj metodę <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>(w Visual Basic .NET), aby ustawić właściwość Data i godzina UTC na wartość. `static`

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konwertowania niejednoznacznego czasu na czas UTC przez założenie, że reprezentuje on lokalną strefę czasową.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Przykład składa się z metody o `ResolveAmbiguousTime` nazwie, która określa <xref:System.DateTime> , czy wartość przeniesiona do niej jest niejednoznaczna. Jeśli wartość jest niejednoznaczna, metoda zwraca <xref:System.DateTime> wartość, która reprezentuje odpowiadający czas UTC. Metoda obsługuje tę konwersję poprzez odjęcie wartości <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości lokalnej strefy czasowej od czasu lokalnego.

Zwykle niejednoznaczny czas jest obsługiwany przez wywołanie <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody w celu pobrania <xref:System.TimeSpan> tablicy obiektów, które zawierają niejednoznaczne możliwe przesunięcie czasu UTC. Jednak w tym przykładzie to arbitralne założenie, że niejednoznaczny czas powinien być zawsze mapowany do czasu standardowego strefy czasowej. <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Właściwość zwraca przesunięcie między czasem UTC i strefą czasową (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone przez <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwość; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu. Jest to zalecane rozwiązanie, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System>

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych czasów](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
