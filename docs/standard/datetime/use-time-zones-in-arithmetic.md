---
title: "Porady: użycie stref czasowych w arytmetyczne daty i czasu"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bcffc98d763c125ac44c1048a7c89c8f6a1e89f1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a>Porady: użycie stref czasowych w arytmetyczne daty i czasu

Zwykle podczas wykonywania daty i przy czasu arytmetyczne przy użyciu <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości, wynik nie odzwierciedla żadnych reguł korygowania strefy czasowej. Dotyczy to nawet wtedy, gdy jest wyraźnie strefę czasową wartości daty i godziny (na przykład, gdy <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na <xref:System.DateTimeKind.Local>). W tym temacie przedstawiono sposób wykonywania operacji arytmetycznych na wartości daty i godziny, które należą do określonej strefy czasowej. Wyniki operacji arytmetycznych zostaną one zastosowane reguł korygowania strefy czasowej.

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a>Aby zastosować zasady dopasowania do arytmetyczne daty i czasu

1. Implementuje niektóre metody ściśle uzupełnienie wartość daty i godziny o strefie czasowej, do którego on należy. Na przykład można zadeklarować struktury, która obejmuje daty i wartości godziny i strefy czasowej. W poniższym przykładzie użyto tej metody, aby połączyć <xref:System.DateTime> wartości strefy czasowej.

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. Konwertuj czas uniwersalny czas koordynowany (UTC), wywołując jedną <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody lub <xref:System.TimeZoneInfo.ConvertTime%2A> metody.

3. Do operacji arytmetycznych na czas UTC.

4. Konwertowanie czas UTC na czas oryginalnego skojarzone strefy czasowej przez wywołanie metody <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.

## <a name="example"></a>Przykład

W poniższym przykładzie dodano dwóch godzin i 30 minut do 9 marca 2008 godzinie 01:30:00 Środkowy czas stand. Strefę czasową przejście do czasu letniego występuje 30 minut później, o 2:00 9 marca 2008. Ponieważ przykładzie następuje czterech kroków opisanych w poprzedniej sekcji, poprawnie raporty wynikowego czas jako 05:00. 9 marca 2008.

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są oddzielone od dowolnej strefie czasowej, do których może należeć. Do wykonania w taki sposób, aby automatycznie stosuje reguł korygowania strefę czasową arytmetyczne daty i czasu, musi być natychmiastowe określenie strefy czasowej, do których wszystkie daty i godziny należy wartość. Oznacza to, że datę i godzinę i jego skojarzony strefę czasową musi być ściśle powiązane. Istnieje kilka sposobów, w tym celu, które obejmują:

* Załóżmy, że zawsze są używane w aplikacji należących do danej strefy czasowej. Mimo że jest to odpowiednie w niektórych przypadkach, takie podejście udostępnia ograniczoną elastyczność i przenośność prawdopodobnie ograniczone.

* Zdefiniuj typ, który ściśle couples datę i godzinę z jego skojarzony strefy czasowej, umieszczając w niej zarówno jako pola typu. Takie podejście jest używany w przykładzie kodu, który definiuje strukturę do przechowywania datę i godzinę i strefę czasową w dwóch polach elementu członkowskiego.

Jak wykonać operacje arytmetyczne na pokazano w przykładzie <xref:System.DateTime> wartości, tak aby reguł korygowania strefy czasowej są stosowane do wyniku. Jednak <xref:System.DateTimeOffset> równie łatwo można używać wartości. Poniższy przykład przedstawia, jak kod w oryginalnym przykład może być dostosowane do użycia <xref:System.DateTimeOffset> zamiast <xref:System.DateTime> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

Należy pamiętać, że jeśli to dodawanie po prostu jest wykonywana na <xref:System.DateTimeOffset> wartość bez najpierw konwertowana na czas UTC, wynik odzwierciedla poprawne punktu w czasie, ale jego przesunięcie nie odzwierciedla który wyznaczonych strefę czasową dla wybranego okresu.

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy <xref:System> przestrzeni nazw można zaimportować z `using` instrukcji (wymagane w kodzie języka C#).

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[wykonywanie operacji arytmetycznych na daty i godziny](../../../docs/standard/datetime/performing-arithmetic-operations.md)
