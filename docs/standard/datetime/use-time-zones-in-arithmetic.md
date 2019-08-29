---
title: 'Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 417d8f00c9323f096a2d6228e853a55b1573f48c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106713"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny

Zwykle podczas wykonywania obliczeń daty i godziny przy użyciu <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości, wynik nie uwzględnia żadnych reguł korekty strefy czasowej. Jest to prawdziwe, nawet gdy strefa czasowa wartości daty i godziny jest jasno zidentyfikowana (na przykład gdy <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na <xref:System.DateTimeKind.Local>). W tym temacie przedstawiono sposób wykonywania operacji arytmetycznych na wartościach daty i godziny, które należą do określonej strefy czasowej. Wyniki operacji arytmetycznych odzwierciedlają reguły dostosowania strefy czasowej.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Aby zastosować reguły dostosowania do operacji arytmetycznych daty i godziny

1. Zaimplementuj pewną metodę ścisłego sprzęgania wartości daty i godziny ze strefą czasową, do której należy. Na przykład Zadeklaruj strukturę, która zawiera zarówno wartość daty, jak i jej strefę czasową. Poniższy przykład używa tego podejścia do łączenia <xref:System.DateTime> wartości ze strefą czasową.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Przekształć czas na uniwersalny czas koordynowany (UTC), wywołując <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metodę <xref:System.TimeZoneInfo.ConvertTime%2A> lub metodę.

3. Wykonaj operację arytmetyczną na czas UTC.

4. Przekonwertuj godzinę z czasu UTC na oryginalną strefę czasową skojarzoną z <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> czasem, wywołując metodę.

## <a name="example"></a>Przykład

Poniższy przykład dodaje dwie godziny i 30 minut do 9 marca 2008, o godz. 1:30 rano Środkowy czas standardowy. Przejście strefy czasowej do czasu letniego występuje 30 minut później, o godzinie 2:00 9 marca 2008. Ponieważ przykład jest zgodny z czterema krokami wymienionymi w poprzedniej sekcji, prawidłowo raportuje otrzymany czas jako 5:00 rano 9 marca 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Oba <xref:System.DateTime> i<xref:System.DateTimeOffset> wartości są nieskojarzone ze strefą czasową, do której mogą się one znajdować. Aby wykonać operacje arytmetyczne daty i godziny w sposób, który automatycznie stosuje reguły dostosowania strefy czasowej, strefa czasowa, do której należy każda wartość daty i godziny musi być od razu możliwa do zidentyfikowania. Oznacza to, że data i godzina oraz skojarzona ze strefą czasową muszą być ściśle sprzężone. Można to zrobić na kilka sposobów:

- Załóżmy, że wszystkie godziny używane w aplikacji należą do określonej strefy czasowej. Chociaż jest to odpowiednie w niektórych przypadkach, ta metoda oferuje ograniczoną elastyczność i prawdopodobnie ograniczoną przenośność.

- Zdefiniuj typ, który ściśle Couples datę i godzinę ze skojarzoną strefą czasową przez uwzględnienie obu pól jako pola typu. To podejście jest używane w przykładowym kodzie, który definiuje strukturę do przechowywania daty i godziny i strefy czasowej w dwóch polach elementów członkowskich.

Przykład ilustruje sposób wykonywania operacji arytmetycznych na <xref:System.DateTime> wartościach, dzięki czemu do wyniku są stosowane reguły dopasowywania strefy czasowej. <xref:System.DateTimeOffset> Jednak wartości mogą być używane równie łatwo. Poniższy przykład ilustruje, jak kod w oryginalnym przykładzie może zostać dostosowany do użycia <xref:System.DateTimeOffset> <xref:System.DateTime> zamiast wartości.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Należy pamiętać, że jeśli ten dodatkowy element jest po <xref:System.DateTimeOffset> prostu wykonywany na wartości bez wcześniejszego przekonwertowania na czas UTC, wynik odzwierciedla prawidłowy punkt w czasie, ale jego przesunięcie nie odzwierciedla tego, czy określona strefa czasowa jest w tym czasie.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System>

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Wykonywanie operacji arytmetycznych na wartościach dat i godzin](../../../docs/standard/datetime/performing-arithmetic-operations.md)
