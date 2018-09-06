---
title: 'Porady: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91e80f44934092007f6f842f0694789d49321446
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863554"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Porady: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu

Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalnego czasu koordynowanego (UTC). Występuje ona, gdy czas zegara jest uwzględniany w czasie, takie jak podczas przechodzenia na strefę czasową czasu jego (czas standardowy). Podczas obsługi niejednoznaczny czas, możesz wykonać jedną z następujących czynności:

* Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika, aby rozstrzygnąć niejednoznaczność.

* Należy z założenia na temat sposobu mapowania czasu UTC. Na przykład można założyć, że że niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).

W tym temacie przedstawiono sposób umożliwiają użytkownikowi rozwiązać niejednoznaczny czas.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Aby umożliwić użytkownikowi rozwiązać niejednoznaczny czas

1. Rozpoczynanie daty i godziny, danych wejściowych przez użytkownika.

2. Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę pozwala ustalić, czy czas jest niejednoznaczna.

3. Jeśli czas jest niejednoznaczny, należy wywołać <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodę, która pobierze tablicę <xref:System.TimeSpan> obiektów. Każdy element w tablicy zawiera przesunięcie czasu UTC, który można mapować niejednoznaczny czas.

4. Poinformuj użytkowników wybierz żądaną przesunięcie.

5. Uzyskaj Data i Godzina UTC przez odjęcie przesunięcie wybranego przez użytkownika od czasu lokalnego.

6. Wywołaj `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład monituje użytkownika o wprowadź datę i godzinę, a jeśli jest niejednoznaczny, umożliwia użytkownikowi wybranie czasu UTC, który mapuje niejednoznaczny czas.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Podstawowy przykład kodu wykorzystuje tablicę <xref:System.TimeSpan> obiektów, aby wskazać możliwe przesunięcia niejednoznaczny czas względem czasu UTC. Jednak te przesunięcia prawdopodobnie nie jest zrozumiały dla użytkownika. Wyjaśnienie przesunięcia, kod również uwagi, czy przesunięcie reprezentuje strefy czasu lokalnego (czas standardowy) lub jego czasu letniego. Kod określa, które jest w warstwie standardowa, a które czas letni porównując przesunięcie z wartością <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości. Ta właściwość wskazuje różnicę między czasem UTC i strefy czasowej (czas standardowy).

W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czas lokalny strefy nigdy nie jest przypisany do zmiennej obiektu. Jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda unieważnia żadnych obiektów przypisanych do lokalnej strefy czasowej.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
* [Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md)
