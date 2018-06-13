---
title: Wykonywanie niezależnych od kultury porównań ciągów
ms.date: 03/30/2017
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
ms.openlocfilehash: 35805d1760b0e06d33498efeeb3104979da26bc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573610"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Wykonywanie niezależnych od kultury porównań ciągów
Domyślnie <xref:System.String.Compare%2A?displayProperty=nameWithType> — metoda wykonuje porównania z uwzględnieniem kultury i z uwzględnieniem wielkości liter. Ta metoda obejmuje również kilka przeciążeń udostępniających `culture` parametr, który umożliwia określenie kultury do użycia, a `comparisonType` parametr, który umożliwia określenie reguł porównania. Wywoływanie tych metod zamiast przeciążenia domyślnego usuwa wszelkie niejednoznaczności dotyczące reguł używanych w wywołaniu określonej metody i jednoznacznie wskazuje, czy w danym porównaniu jest uwzględniana kultura, czy nie.  
  
> [!NOTE]
>  Zarówno przeciążeń <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wykonywać porównania z uwzględnieniem kultury i z uwzględnieniem wielkości liter, tej metody nie można użyć do wykonania porównania niezależnych od kultury. Dla jasności kodu, firma Microsoft zaleca się używanie <xref:System.String.Compare%2A?displayProperty=nameWithType> metody zamiast tego.  
  
 Dla operacji zależne od kultury, określ <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> wartość wyliczenia jako `comparisonType` parametru. Jeśli chcesz wykonać porównanie zależne od kultury, przy użyciu wyznaczonej kultury niż bieżącej kultury, określ <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tej kultury jako `culture` parametru.  
  
 Porównywanie ciągów niezależnych od kultury, obsługiwane przez <xref:System.String.Compare%2A?displayProperty=nameWithType> metody są albo językowe (na podstawie Konwencji sortowania z kulturą niezmienną) lub z systemem innym niż językowe (na podstawie wartości porządkowej znaków w ciągu). Porównania nielingwistyczne stanowią większość pośród porównań ciągów, w których nie jest uwzględniana kultura. Dla porównania, określ <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wartość wyliczenia jako `comparisonType` parametru. Na przykład jeśli decyzja dotycząca zabezpieczeń (taka jak porównywanie nazwy użytkownika lub hasła) jest podejmowana na podstawie porównania ciągów, w operacji nie powinna być uwzględniana kultura, a operacja powinna być nielingwistyczna, dzięki czemu konwencje dotyczące określonej kultury lub języka nie będą miały wpływu na wynik.  
  
 Lingwistycznych porównań ciągów, w których nie jest uwzględniana kultura, należy używać w sytuacji, gdy trzeba w spójny sposób obsługiwać lingwistycznie podobne ciągi z różnych kultur. Na przykład jeśli w aplikacji w polu listy są wyświetlane wyrazy, w których jest używanych wiele zestawów znaków, warto wyświetlać te wyrazy w takiej samej kolejności, niezależnie od bieżącej kultury. Dla porównań lingwistycznych, w których nie jest uwzględniana kultura, program .NET Framework definiuje niezmienną kulturę, która jest oparta na konwencjach lingwistycznych języka angielskiego. Aby wykonać niezależnych od kultury językowej porównania, określ <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako `comparisonType` parametru.  
  
 W poniższym przykładzie są wykonywane dwa nielingwistyczne porównania ciągów, w których nie jest uwzględniana kultura. W pierwszym z nich jest uwzględniana wielkość liter, a w drugim nie.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String.Compare%2A?displayProperty=nameWithType>  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType>  
 [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
