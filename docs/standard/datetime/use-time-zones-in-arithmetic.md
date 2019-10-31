---
title: 'Instrukcje: używanie stref czasowych w operacji arytmetycznych daty i czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
ms.openlocfilehash: 1acd53fad6b0ab173f855850353339190ebdd893
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132541"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Instrukcje: używanie stref czasowych w operacji arytmetycznych daty i czasu

Zwykle podczas przeprowadzania operacji arytmetycznej daty i godziny przy użyciu wartości <xref:System.DateTime> lub <xref:System.DateTimeOffset> wynik nie odzwierciedla żadnych reguł korekty strefy czasowej. Jest to prawdziwe, nawet gdy strefa czasowa wartości daty i godziny jest jasno zidentyfikowana (na przykład gdy właściwość <xref:System.DateTime.Kind%2A> jest ustawiona na <xref:System.DateTimeKind.Local>). W tym temacie przedstawiono sposób wykonywania operacji arytmetycznych na wartościach daty i godziny, które należą do określonej strefy czasowej. Wyniki operacji arytmetycznych odzwierciedlają reguły dostosowania strefy czasowej.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Aby zastosować reguły dostosowania do operacji arytmetycznych daty i godziny

1. Zaimplementuj pewną metodę ścisłego sprzęgania wartości daty i godziny ze strefą czasową, do której należy. Na przykład Zadeklaruj strukturę, która zawiera zarówno wartość daty, jak i jej strefę czasową. Poniższy przykład używa tego podejścia do łączenia wartości <xref:System.DateTime> ze strefą czasową.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Przekształć czas na uniwersalny czas koordynowany (UTC), wywołując metodę <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> lub metodę <xref:System.TimeZoneInfo.ConvertTime%2A>.

3. Wykonaj operację arytmetyczną na czas UTC.

4. Przekonwertuj godzinę z czasu UTC na oryginalną strefę czasową skojarzoną z czasem, wywołując metodę <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład dodaje dwie godziny i 30 minut do 9 marca 2008, o godz. 1:30 rano Środkowy czas standardowy. Przejście strefy czasowej do czasu letniego występuje 30 minut później, o godzinie 2:00 9 marca 2008. Ponieważ przykład jest zgodny z czterema krokami wymienionymi w poprzedniej sekcji, prawidłowo raportuje otrzymany czas jako 5:00 rano 9 marca 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Wartości <xref:System.DateTime> i <xref:System.DateTimeOffset> są rozkojarzone ze strefą czasową, do której mogą się one znajdować. Aby wykonać operacje arytmetyczne daty i godziny w sposób, który automatycznie stosuje reguły dostosowania strefy czasowej, strefa czasowa, do której należy każda wartość daty i godziny musi być od razu możliwa do zidentyfikowania. Oznacza to, że data i godzina oraz skojarzona ze strefą czasową muszą być ściśle sprzężone. Można to zrobić na kilka sposobów:

- Załóżmy, że wszystkie godziny używane w aplikacji należą do określonej strefy czasowej. Chociaż jest to odpowiednie w niektórych przypadkach, ta metoda oferuje ograniczoną elastyczność i prawdopodobnie ograniczoną przenośność.

- Zdefiniuj typ, który ściśle Couples datę i godzinę ze skojarzoną strefą czasową przez uwzględnienie obu pól jako pola typu. To podejście jest używane w przykładowym kodzie, który definiuje strukturę do przechowywania daty i godziny i strefy czasowej w dwóch polach elementów członkowskich.

Przykład ilustruje sposób wykonywania operacji arytmetycznych na wartościach <xref:System.DateTime>, tak aby reguły dopasowywania strefy czasowej były stosowane do wyniku. Jednak wartości <xref:System.DateTimeOffset> mogą być używane równie łatwo. Poniższy przykład ilustruje, jak kod w pierwotnym przykładzie może zostać dostosowany do użycia <xref:System.DateTimeOffset> zamiast wartości <xref:System.DateTime>.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Należy pamiętać, że jeśli to dodanie jest wykonywane po prostu na wartości <xref:System.DateTimeOffset> bez wcześniejszego przeprowadzenia konwersji na czas UTC, wynik będzie odzwierciedlać prawidłowy punkt w czasie, ale jego przesunięcie nie odzwierciedla tego, czy określona strefa czasowa jest w tym czasie.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Przestrzeń nazw <xref:System> zostać zaimportowana przy użyciu instrukcji `using` (wymagane C# w kodzie).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Wykonywanie operacji arytmetycznych na wartościach dat i godzin](../../../docs/standard/datetime/performing-arithmetic-operations.md)
