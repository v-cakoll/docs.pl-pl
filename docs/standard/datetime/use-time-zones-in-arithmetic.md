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
ms.openlocfilehash: 053ca2d10deadf58d5bb8b4628fb5dee815d82c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026500"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny

Zazwyczaj podczas możesz wykonać daty i godziny arytmetycznych przy użyciu <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości, wynik nie odzwierciedla żadnych reguł dopasowania stref czasowych. Ta zasada obowiązuje nawet wtedy, gdy jest wyraźnie strefy czasowej w wartości daty i godziny (na przykład, gdy <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na <xref:System.DateTimeKind.Local>). W tym temacie pokazano, jak wykonywać operacje arytmetyczne na wartości daty i godziny, które należą do określonej strefy czasowej. Wyniki operacji arytmetycznych odzwierciedlają reguł korygowania strefy czasowej.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Aby zastosować reguły dopasowania do arytmetyka daty i godziny

1. Zaimplementowanie niektóre metody ściśle sprzężenia wartości daty i godziny ze strefą czasową, do której należy. Na przykład można zadeklarować strukturę, która zawiera datę i wartości godziny i strefy czasowej. W poniższym przykładzie użyto tego podejścia połączyć <xref:System.DateTime> wartość z ich strefą czasu.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Konwertuj czas uniwersalny czas koordynowany (UTC), wywołując jedną <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody lub <xref:System.TimeZoneInfo.ConvertTime%2A> metody.

3. Wykonywanie operacji arytmetycznej na czas UTC.

4. Przekonwertować wartość czasu względem czasu UTC na pierwotny czas skojarzone strefę czasową, wywołując <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.

## <a name="example"></a>Przykład

Poniższy przykład dodaje dwie godziny i 30 minut do 9 marca 2008 roku o godzinie 1:30 Środkowy czas standardowy. Strefa czasowa przejścia do czasu letniego występuje trzydzieści minut później, o 2:00 9 marca 2008. Ponieważ w przykładzie poniżej czterech kroków opisanych w poprzedniej sekcji, poprawnie raporty wynikowego czas jako 05:00. 9 marca 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są oddzielone od dowolnej strefie czasowej, do których może należeć. Aby wykonać arytmetyka w taki sposób, aby automatycznie stosuje reguły dopasowania jest strefa czasowa daty i godziny, strefę czasową, do której wszystkie daty i godziny wartość należy musi być natychmiastowe określenie. Oznacza to, że datę i godzinę i jego skojarzone strefę czasową musi być ściśle powiązane. Istnieje kilka sposobów, w tym celu, m.in:

* Załóżmy, że cały czas używane w aplikacji należących do określonej strefy czasowej. Mimo że jest to stosowne, w niektórych przypadkach, to podejście zapewnia ograniczoną elastyczność i przenośność prawdopodobnie ograniczone.

* Zdefiniuj typ, który jest ściśle couples daty i godziny za pomocą jego skojarzonego strefy czasowej, umieszczając zarówno jako pola tego typu. Ta metoda jest używana w przykładzie kodu, który definiuje strukturę do przechowywania datę i godzinę i strefę czasową w dwóch pól członka.

W przykładzie pokazano, jak wykonywać operacje arytmetyczne na <xref:System.DateTime> wartości, tak aby reguł dopasowania stref czasowych są stosowane do wyniku. Jednak <xref:System.DateTimeOffset> równie łatwo można używać wartości. W poniższym przykładzie pokazano, jak kod w przykładzie, oryginalnym musi być dostosowane do użytku <xref:System.DateTimeOffset> zamiast <xref:System.DateTime> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Należy pamiętać, że jeśli to dodawanie po prostu jest wykonywana na <xref:System.DateTimeOffset> wartości bez najpierw podczas konwertowania go na czas UTC, wynik odzwierciedla prawidłowe punktu w czasie, ale przesunięcie nie odzwierciedla z wyznaczonym strefę czasową dla wybranego okresu.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Wykonywanie operacji arytmetycznych na wartościach dat i godzin](../../../docs/standard/datetime/performing-arithmetic-operations.md)
