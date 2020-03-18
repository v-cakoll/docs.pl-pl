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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120835"
---
# <a name="performing-culture-insensitive-string-comparisons"></a>Wykonywanie niezależnych od kultury porównań ciągów
Domyślnie <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda wykonuje porównania zależne od kultury i wielkości liter. Ta metoda zawiera również kilka `culture` przeciążeń, które zapewniają parametr, `comparisonType` który umożliwia określenie kultury do użycia i parametr, który pozwala określić reguły porównania do użycia. Wywoływanie tych metod zamiast przeciążenia domyślnego usuwa wszelkie niejednoznaczności dotyczące reguł używanych w wywołaniu określonej metody i jednoznacznie wskazuje, czy w danym porównaniu jest uwzględniana kultura, czy nie.  
  
> [!NOTE]
> Oba przeciążenia <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody wykonać porównania zależne od kultury i wielkości liter; nie można użyć tej metody do wykonywania porównań niewrażliwych na kulturę. Dla jasności kodu zaleca się <xref:System.String.Compare%2A?displayProperty=nameWithType> użycie metody zamiast tego.  
  
 W przypadku operacji uwzględniających <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> kulturę określ `comparisonType` wartość lub wyliczenie jako parametr. Jeśli chcesz wykonać porównanie zależne od kultury przy użyciu wyznaczonej kultury <xref:System.Globalization.CultureInfo> innej niż bieżąca kultura, określ obiekt, który reprezentuje tę kulturę `culture` jako parametr.  
  
 Porównania ciągów nieczułych na kulturę obsługiwane przez <xref:System.String.Compare%2A?displayProperty=nameWithType> metodę są lingwistyczne (oparte na konwencjach sortowania kultury niezmiennej) lub niejęzykowe (na podstawie wartości ordinal znaków w ciągu). Porównania nielingwistyczne stanowią większość pośród porównań ciągów, w których nie jest uwzględniana kultura. Dla tych porównań <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> określ wartość lub <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> `comparisonType` wyliczenie jako parametr. Na przykład jeśli decyzja dotycząca zabezpieczeń (taka jak porównywanie nazwy użytkownika lub hasła) jest podejmowana na podstawie porównania ciągów, w operacji nie powinna być uwzględniana kultura, a operacja powinna być nielingwistyczna, dzięki czemu konwencje dotyczące określonej kultury lub języka nie będą miały wpływu na wynik.  
  
 Lingwistycznych porównań ciągów, w których nie jest uwzględniana kultura, należy używać w sytuacji, gdy trzeba w spójny sposób obsługiwać lingwistycznie podobne ciągi z różnych kultur. Na przykład jeśli w aplikacji w polu listy są wyświetlane wyrazy, w których jest używanych wiele zestawów znaków, warto wyświetlać te wyrazy w takiej samej kolejności, niezależnie od bieżącej kultury. Dla porównań lingwistycznych, w których nie jest uwzględniana kultura, program .NET Framework definiuje niezmienną kulturę, która jest oparta na konwencjach lingwistycznych języka angielskiego. Aby wykonać porównanie językowe niewrażliwe <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> na `comparisonType` kulturę, określ <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> lub jako parametr.  
  
 W poniższym przykładzie są wykonywane dwa nielingwistyczne porównania ciągów, w których nie jest uwzględniana kultura. W pierwszym z nich jest uwzględniana wielkość liter, a w drugim nie.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

Można pobrać [tabele wagi sortowania,](https://www.microsoft.com/download/details.aspx?id=10921)zestaw plików tekstowych, które zawierają informacje na temat wagi znaków używanych w operacjach sortowania i porównywania dla systemów operacyjnych Windows, a [domyślna tabela elementów sortowania Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), tabela wagi sortowania dla systemów Linux i macOS.

## <a name="see-also"></a>Zobacz też

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Najlepsze rozwiązania dotyczące używania ciągów](../../../docs/standard/base-types/best-practices-strings.md)
