---
title: 'Porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083871dd97a36529351aacbdcd39980bdde74a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalny czas koordynowany (UTC). Nastąpi to po czas zegara jest uwzględniany w czasie, takie jak podczas przejścia z czasu letniego strefę czasową na jego czas standardowy. Podczas obsługi niejednoznaczny czas, możesz wybrać jedną z następujących czynności:

* Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika w celu rozwiązania niejednoznaczności.

* Należy założeń dotyczących sposób mapowania czas UTC. Na przykład można założyć, że który niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).

W tym temacie przedstawiono sposób umożliwia użytkownikowi niejednoznaczny czas rozpoznania.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby umożliwić użytkownikowi rozwiązać niejednoznaczny czas

1. Pobierz datę i godzinę wejściowych przez użytkownika.

2. Wywołanie <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczna.

3. Jeśli czas jest niejednoznaczny, wywołanie <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda pobierania tablicę <xref:System.TimeSpan> obiektów. Każdy element w tablicy zawiera przesunięcie czasu UTC, który można mapować niejednoznaczny czas.

4. Poinformuj użytkowników wybierz żądane przesunięcie.

5. Pobierz Data i Godzina UTC przez odjęcie przesunięcie wybrane przez użytkownika z czasem lokalnym.

6. Wywołanie `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić czas UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

W poniższym przykładzie monituje użytkownika o wprowadź datę i godzinę i, jeśli jest niejednoznaczny, umożliwia użytkownikowi wybieranie niejednoznaczny czas mapowana na czas UTC.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Podstawowy przykład kodu wykorzystuje tablicę <xref:System.TimeSpan> obiektów, aby wskazać możliwe przesunięcia niejednoznaczny czas od czasu UTC. Jednak przesunięcia prawdopodobnie nie jest zrozumiały dla użytkownika. Wyjaśnienie przesunięcia, kod uwagi również, czy przesunięcie reprezentuje strefy czasu lokalnego (czas standardowy) lub jego czasu letniego. Kod określa czas, który jest standardem, a które czas letni porównując przesunięcie z wartością <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości. Ta właściwość wskazuje różnicę między czasem UTC i strefy czasowej (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czasu lokalnego strefy nigdy nie jest przypisany do zmiennej obiektu. To jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia żadnych obiektów przypisanych do strefy czasu lokalnego.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> przestrzeni nazw można zaimportować z `using` instrukcji (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md)
