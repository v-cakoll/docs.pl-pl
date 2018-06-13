---
title: 'Porady: Rozwiązywanie niejednoznacznych wartości czasu'
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
ms.openlocfilehash: a92081a164d15e5150c582b37c6c688cd15e619e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571202"
---
# <a name="how-to-resolve-ambiguous-times"></a>Porady: Rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalny czas koordynowany (UTC). Nastąpi to po czas zegara jest uwzględniany w czasie, takie jak podczas przejścia z czasu letniego strefę czasową na jego czas standardowy. Podczas obsługi niejednoznaczny czas, możesz wybrać jedną z następujących czynności:

* Należy założeń dotyczących sposób mapowania czas UTC. Na przykład można założyć, że który niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).

* Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika w celu rozwiązania niejednoznaczności.

W tym temacie pokazano, jak rozwiązać niejednoznaczny czas przez przy założeniu, że reprezentuje strefy czasowej (czas standardowy).

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Aby zamapować niejednoznaczny czas na strefę czasową (czas standardowy)

1. Wywołanie <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczna.

2. Jeśli czas jest niejednoznaczny, odejmuje wartość czasu od <xref:System.TimeSpan> obiektu zwróconego przez strefę czasową <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości.

3. Wywołanie `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić czas UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób konwertowania niejednoznaczny czas UTC przez przy założeniu, że reprezentuje czas standardowy strefy czasu lokalnego.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Przykład zawiera metodę o nazwie `ResolveAmbiguousTime` Określa, czy <xref:System.DateTime> wartości przekazywane do niego jest niejednoznaczna. Jeśli wartość jest niejednoznaczny, metoda zwraca <xref:System.DateTime> wartość, która reprezentuje odpowiedni czas UTC. Metoda obsługi konwersji przez odjęcie wartości lokalnej strefy czasowej <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwość z czasem lokalnym.

Zwykle niejednoznaczny czas jest obsługiwany przez wywołanie metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda pobierania tablicę <xref:System.TimeSpan> obiektów zawierających niejednoznaczny czas UTC możliwe przesunięcia. Jednak w tym przykładzie powoduje, że dowolnego założenie, że niejednoznaczny czas powinien zawsze być zamapowany na strefie czasowej (czas standardowy). <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Właściwość zwraca przesunięcie UTC i strefy czasowej (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czasu lokalnego strefy nigdy nie jest przypisany do zmiennej obiektu. To jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia żadnych obiektów przypisanych do strefy czasu lokalnego.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> przestrzeni nazw można zaimportować z `using` instrukcji (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
