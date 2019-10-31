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
ms.openlocfilehash: 85ba91b63ab0edbccc768e2d1ad4aaef31fd2f21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120835"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Wykonywanie niezależnych od kultury porównań ciągów
Domyślnie metoda <xref:System.String.Compare%2A?displayProperty=nameWithType> wykonuje porównania uwzględniające tylko kulturę i wielkość liter. Ta metoda zawiera również kilka przeciążeń, które udostępniają parametr `culture`, który pozwala określić kulturę, która ma być używana, oraz parametr `comparisonType`, który umożliwia określenie reguł porównywania, które mają być używane. Wywoływanie tych metod zamiast przeciążenia domyślnego usuwa wszelkie niejednoznaczności dotyczące reguł używanych w wywołaniu określonej metody i jednoznacznie wskazuje, czy w danym porównaniu jest uwzględniana kultura, czy nie.  
  
> [!NOTE]
> Oba przeciążenia metody <xref:System.String.CompareTo%2A?displayProperty=nameWithType> wykonują porównania uwzględniające kulturę i uwzględniające wielkość liter; nie można użyć tej metody do wykonywania porównania niewrażliwych na kulturę. W przypadku przejrzystości kodu zalecamy użycie metody <xref:System.String.Compare%2A?displayProperty=nameWithType>.  
  
 W przypadku operacji zależnych od kultury należy określić wartość <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> Wyliczenie jako parametr `comparisonType`. Jeśli chcesz wykonać porównanie z uwzględnieniem kultury przy użyciu wyoznaczonej kultury innej niż bieżąca kultura, Określ obiekt <xref:System.Globalization.CultureInfo>, który reprezentuje tę kulturę jako parametr `culture`.  
  
 Porównania ciągów niewrażliwych na kulturę obsługiwane przez metodę <xref:System.String.Compare%2A?displayProperty=nameWithType> są językiem (na podstawie Konwencji sortowania niezmiennej kultury) lub nielingwistycznych (na podstawie wartości porządkowej znaków w ciągu). Porównania nielingwistyczne stanowią większość pośród porównań ciągów, w których nie jest uwzględniana kultura. Dla tych porównań Określ wartość <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> Wyliczenie jako parametr `comparisonType`. Na przykład jeśli decyzja dotycząca zabezpieczeń (taka jak porównywanie nazwy użytkownika lub hasła) jest podejmowana na podstawie porównania ciągów, w operacji nie powinna być uwzględniana kultura, a operacja powinna być nielingwistyczna, dzięki czemu konwencje dotyczące określonej kultury lub języka nie będą miały wpływu na wynik.  
  
 Lingwistycznych porównań ciągów, w których nie jest uwzględniana kultura, należy używać w sytuacji, gdy trzeba w spójny sposób obsługiwać lingwistycznie podobne ciągi z różnych kultur. Na przykład jeśli w aplikacji w polu listy są wyświetlane wyrazy, w których jest używanych wiele zestawów znaków, warto wyświetlać te wyrazy w takiej samej kolejności, niezależnie od bieżącej kultury. Dla porównań lingwistycznych, w których nie jest uwzględniana kultura, program .NET Framework definiuje niezmienną kulturę, która jest oparta na konwencjach lingwistycznych języka angielskiego. Aby przeprowadzić porównanie lingwistyczne bez uwzględniania kultur, określ <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> lub <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> jako parametr `comparisonType`.  
  
 W poniższym przykładzie są wykonywane dwa nielingwistyczne porównania ciągów, w których nie jest uwzględniana kultura. W pierwszym z nich jest uwzględniana wielkość liter, a w drugim nie.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Można pobrać [tabele wagi sortowania](https://www.microsoft.com/download/details.aspx?id=10921), zestaw plików tekstowych, które zawierają informacje o wagach znaków używanych w operacjach sortowania i porównywania dla systemów operacyjnych Windows, a także [domyślną tabelę elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), sortowanie tabela wag dla systemów Linux i macOS.

## <a name="see-also"></a>Zobacz także

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
