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
ms.openlocfilehash: aae3e5145d2fa85cd55fc5b1288ef4aaa0fef48f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569298"
---
# <a name="how-to-resolve-ambiguous-times"></a>Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalnego czasu koordynowanego (UTC). Występuje ona, gdy czas zegara jest uwzględniany w czasie, takie jak podczas przechodzenia na strefę czasową czasu jego (czas standardowy). Podczas obsługi niejednoznaczny czas, możesz wykonać jedną z następujących czynności:

* Należy z założenia na temat sposobu mapowania czasu UTC. Na przykład można założyć, że że niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).

* Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika, aby rozstrzygnąć niejednoznaczność.

W tym temacie przedstawiono sposób niejednoznaczny czas, przez rozwiązania, przy założeniu, że reprezentuje strefy czasowej (czas standardowy).

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Aby zamapować niejednoznaczny czas na strefy czasowej (czas standardowy)

1. Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę pozwala ustalić, czy czas jest niejednoznaczna.

2. Jeśli czas jest niejednoznaczny, Odejmij czasu od <xref:System.TimeSpan> obiektu zwróconego przez strefę czasową <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości.

3. Wywołaj `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konwertowania niejednoznaczny czas UTC, przy założeniu, że reprezentuje czas standardowy strefy czasu lokalnego.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Przykład zawiera metodę o nazwie `ResolveAmbiguousTime` określający, czy <xref:System.DateTime> wartością przekazywaną do niego jest niejednoznaczna. Jeśli wartość jest niejednoznaczny, metoda zwraca <xref:System.DateTime> wartość, która reprezentuje odpowiedni czas UTC. Ta konwersja jest obsługiwała przez odjęcie wartości lokalnej strefy czasowej <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości od czasu lokalnego.

Zazwyczaj niejednoznaczny czas odbywa się przez wywołanie metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodę, która pobierze tablicę <xref:System.TimeSpan> obiektów, które zawierają niejednoznaczny czas UTC możliwe przesunięcia. Jednak w tym przykładzie sprawia, że dowolne założenie, że niejednoznaczny czas zawsze powinien być mapowany do strefy czasowej (czas standardowy). <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Właściwość zwraca przesunięcie między czasem UTC i strefy czasowej (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czas lokalny strefy nigdy nie jest przypisany do zmiennej obiektu. Jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda unieważnia żadnych obiektów przypisanych do lokalnej strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
