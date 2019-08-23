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
ms.openlocfilehash: 7b68d079413168b042412a67e8732e8afed66ffa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915881"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Wykonywanie niezależnych od kultury porównań ciągów
Domyślnie <xref:System.String.Compare%2A?displayProperty=nameWithType> Metoda wykonuje porównania uwzględniające kulturę i wielkość liter. Ta metoda zawiera również kilka przeciążeń, `culture` które udostępniają parametr, który pozwala określić kulturę, która `comparisonType` ma być używana, oraz parametr, który umożliwia określenie reguł porównania do użycia. Wywoływanie tych metod zamiast przeciążenia domyślnego usuwa wszelkie niejednoznaczności dotyczące reguł używanych w wywołaniu określonej metody i jednoznacznie wskazuje, czy w danym porównaniu jest uwzględniana kultura, czy nie.  
  
> [!NOTE]
> Oba przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wykonują porównania zależne od kultury i wielkości liter; nie można użyć tej metody do wykonywania porównań bez uwzględniania kultury. W przypadku przejrzystości kodu zalecamy użycie <xref:System.String.Compare%2A?displayProperty=nameWithType> metody zamiast.  
  
 W przypadku operacji zależnych od kultury należy <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> określić <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> wartość wyliczenia lub jako `comparisonType` parametr. Jeśli chcesz wykonać porównanie z uwzględnieniem kultury przy użyciu wyoznaczonej kultury innej niż bieżąca kultura, określ <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje tę kulturę `culture` jako parametr.  
  
 Porównania ciągów niewrażliwych na kulturę obsługiwane przez <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę są językiem (na podstawie Konwencji sortowania niezmiennej kultury) lub w języku innym niż język (na podstawie wartości porządkowej znaków w ciągu). Porównania nielingwistyczne stanowią większość pośród porównań ciągów, w których nie jest uwzględniana kultura. Dla tych porównań należy określić <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> wartość <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> wyliczenia lub jako `comparisonType` parametr. Na przykład jeśli decyzja dotycząca zabezpieczeń (taka jak porównywanie nazwy użytkownika lub hasła) jest podejmowana na podstawie porównania ciągów, w operacji nie powinna być uwzględniana kultura, a operacja powinna być nielingwistyczna, dzięki czemu konwencje dotyczące określonej kultury lub języka nie będą miały wpływu na wynik.  
  
 Lingwistycznych porównań ciągów, w których nie jest uwzględniana kultura, należy używać w sytuacji, gdy trzeba w spójny sposób obsługiwać lingwistycznie podobne ciągi z różnych kultur. Na przykład jeśli w aplikacji w polu listy są wyświetlane wyrazy, w których jest używanych wiele zestawów znaków, warto wyświetlać te wyrazy w takiej samej kolejności, niezależnie od bieżącej kultury. Dla porównań lingwistycznych, w których nie jest uwzględniana kultura, program .NET Framework definiuje niezmienną kulturę, która jest oparta na konwencjach lingwistycznych języka angielskiego. Aby przeprowadzić porównanie lingwistyczne bez uwzględniania kultur, określ <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako `comparisonType` parametr.  
  
 W poniższym przykładzie są wykonywane dwa nielingwistyczne porównania ciągów, w których nie jest uwzględniana kultura. W pierwszym z nich jest uwzględniana wielkość liter, a w drugim nie.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Można pobrać [tabele wagi sortowania](https://www.microsoft.com/download/details.aspx?id=10921), zestaw plików tekstowych, które zawierają informacje o wagach znaków używanych w operacjach sortowania i porównywania dla systemów operacyjnych Windows, a także [domyślną tabelę elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), sortowanie tabela wag dla systemów Linux i macOS.

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
