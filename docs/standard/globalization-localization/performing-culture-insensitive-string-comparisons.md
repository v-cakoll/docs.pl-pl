---
title: Wykonywanie niezależnych od kultury porównań ciągów
ms.date: 08/22/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84b1c10b655fefcd420a0c3cf038dba00e688d3e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876158"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Wykonywanie niezależnych od kultury porównań ciągów
Domyślnie <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda wykonuje porównania jest rozróżniana kultura oraz wielkość liter. Ta metoda obejmuje także kilka przeciążeń dostarczających `culture` parametr, który umożliwia określenie kultury, aby użyć, a `comparisonType` parametr, który umożliwia określenie reguł porównania do użycia. Wywoływanie tych metod zamiast przeciążenia domyślnego usuwa wszelkie niejednoznaczności dotyczące reguł używanych w wywołaniu określonej metody i jednoznacznie wskazuje, czy w danym porównaniu jest uwzględniana kultura, czy nie.  
  
> [!NOTE]
>  Oba przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wykonywania uwzględniana kultura i wielkość liter; tej metody nie można używać do wykonywania niezależnych od kultury porównań. Czystości kodu zaleca się, że używasz <xref:System.String.Compare%2A?displayProperty=nameWithType> metody zamiast tego.  
  
 Dla operacji wrażliwych na kulturę, określ <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> wartość wyliczenia jako `comparisonType` parametru. Jeśli chcesz wykonać porównanie zależne od kultury, przy użyciu wyznaczonej kultury innej niż bieżąca kultura, określ <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę kulturę jako `culture` parametru.  
  
 Porównania ciągów niewrażliwość na ustawienia kulturowe, obsługiwane przez <xref:System.String.Compare%2A?displayProperty=nameWithType> metody są lingwistyczne (oparte na konwencjach sortowania niezmiennej kultury) lub nielingwistyczne (oparte na wartości porządkowej znaków w ciągu). Porównania nielingwistyczne stanowią większość pośród porównań ciągów, w których nie jest uwzględniana kultura. W przypadku tych porównań określić <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartość wyliczenia jako `comparisonType` parametru. Na przykład jeśli decyzja dotycząca zabezpieczeń (taka jak porównywanie nazwy użytkownika lub hasła) jest podejmowana na podstawie porównania ciągów, w operacji nie powinna być uwzględniana kultura, a operacja powinna być nielingwistyczna, dzięki czemu konwencje dotyczące określonej kultury lub języka nie będą miały wpływu na wynik.  
  
 Lingwistycznych porównań ciągów, w których nie jest uwzględniana kultura, należy używać w sytuacji, gdy trzeba w spójny sposób obsługiwać lingwistycznie podobne ciągi z różnych kultur. Na przykład jeśli w aplikacji w polu listy są wyświetlane wyrazy, w których jest używanych wiele zestawów znaków, warto wyświetlać te wyrazy w takiej samej kolejności, niezależnie od bieżącej kultury. Dla porównań lingwistycznych, w których nie jest uwzględniana kultura, program .NET Framework definiuje niezmienną kulturę, która jest oparta na konwencjach lingwistycznych języka angielskiego. Aby wykonać lingwistyczne porównanie niewrażliwość na ustawienia kulturowe, określ <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako `comparisonType` parametru.  
  
 W poniższym przykładzie są wykonywane dwa nielingwistyczne porównania ciągów, w których nie jest uwzględniana kultura. W pierwszym z nich jest uwzględniana wielkość liter, a w drugim nie.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Możesz pobrać [tabele wagi sortowania](https://www.microsoft.com/en-us/download/details.aspx?id=10921), zbiór plików tekstowych, które zawierają informacje o wagi znaku w operacjach sortowania i porównywania systemów operacyjnych Windows.

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Compare%2A?displayProperty=nameWithType>  
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>  
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
