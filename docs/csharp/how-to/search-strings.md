---
title: Jak wyszukiwać ciągi (Przewodnik języka C#)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: f3e6d95eb4a01d48fac5b5e2c951b9c346206004
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121495"
---
# <a name="how-to-search-strings"></a>Jak wyszukiwać ciągi

Można użyć dwóch głównych strategii wyszukiwania tekstu w ciągach. Metody <xref:System.String> klasy wyszukiwania określonego tekstu. Wyrażenia regularne wyszukują wzorce w tekście.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Typ [ciągu,](../language-reference/builtin-types/reference-types.md#the-string-type) który jest aliasem <xref:System.String?displayProperty=nameWithType> dla klasy, zawiera szereg przydatnych metod wyszukiwania zawartości ciągu. Wśród nich <xref:System.String.Contains%2A> <xref:System.String.StartsWith%2A>są <xref:System.String.EndsWith%2A> <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>, , . Klasa <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> zapewnia bogate słownictwo do wyszukiwania wzorców w tekście. W tym artykule nauczysz się tych technik i jak wybrać najlepszą metodę dla Swoich potrzeb.

## <a name="does-a-string-contain-text"></a>Czy ciąg zawiera tekst?

Metody <xref:System.String.Contains%2A?displayProperty=nameWithType> <xref:System.String.StartsWith%2A?displayProperty=nameWithType> i <xref:System.String.EndsWith%2A?displayProperty=nameWithType> metody wyszukiwania ciągu dla określonego tekstu. Poniższy przykład przedstawia każdą z tych metod i odmianę, która używa wyszukiwania bez uwzględniania wielkości liter:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

W poprzednim przykładzie pokazano ważny punkt dla korzystania z tych metod. W wyszukiwaniach domyślnie **rozróżniana jest wielkość liter.** Wartość wyliczenia <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> służy do określania wyszukiwania bez uwzględniania wielkości liter.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Gdzie występuje poszukiwany tekst w ciągu?

Metody <xref:System.String.IndexOf%2A> <xref:System.String.LastIndexOf%2A> i metody również wyszukiwać tekst w ciągach. Metody te zwracają lokalizację poszukiwanego tekstu. Jeśli tekst nie zostanie znaleziony, `-1`zwróci . Poniższy przykład pokazuje wyszukiwanie pierwszego i ostatniego wystąpienia słowa "metody" i wyświetla tekst pomiędzy.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Znajdowanie określonego tekstu przy użyciu wyrażeń regularnych

Klasa <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> może służyć do wyszukiwania ciągów. Te wyszukiwania mogą wahać się w złożoności od prostych do skomplikowanych wzorców tekstu.

Poniższy przykład kodu wyszukuje słowo "the" lub "ich" w zdaniu, ignorując przypadek. Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> statyczna wykonuje wyszukiwanie. Dajesz mu ciąg do wyszukiwania i wzorzec wyszukiwania. W takim przypadku trzeci argument określa wyszukiwanie bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Wzorzec wyszukiwania opisuje wyszukiwany tekst. W poniższej tabeli opisano każdy element wzorca wyszukiwania. (Poniższa tabela używa `\` singla, `\\` który musi zostać zmieniony, jak w ciągu języka C#).

| Wzór  | Znaczenie     |
| -------- |-------------|
| względem zasobu      | dopasować tekst "the" |
| (eir)?   | mecz 0 lub 1 wystąpienie "eir" |
| \s       | dopasowywuj znak odstępu    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> Metody `string` są zwykle lepsze wybory podczas wyszukiwania dokładnego ciągu. Wyrażenia regularne są lepsze, gdy szukasz jakiegoś wzorca w ciągu źródłowym.

## <a name="does-a-string-follow-a-pattern"></a>Czy ciąg jest zgodny ze wzorcem?

Poniższy kod używa wyrażeń regularnych do sprawdzania poprawności formatu każdego ciągu w tablicy. Sprawdzanie poprawności wymaga, aby każdy ciąg miał postać numeru telefonu, w którym trzy grupy cyfr są oddzielone myślnikami, pierwsze dwie grupy zawierają trzy cyfry, a trzecia grupa zawiera cztery cyfry. Wzorzec wyszukiwania używa `^\\d{3}-\\d{3}-\\d{4}$`wyrażenia regularnego . Aby uzyskać więcej informacji, zobacz [Język wyrażenia regularnego — podręczna dokumentacja](../../standard/base-types/regular-expression-language-quick-reference.md).

| Wzór  | Znaczenie                             |
| -------- |-------------------------------------|
| ^        | dopasowuje początek ciągu |
| \d{3}    | pasuje dokładnie 3-cyfrowymi znakami  |
| -        | pasuje do znaku '-'           |
| \d{3}    | pasuje dokładnie 3-cyfrowymi znakami  |
| -        | pasuje do znaku '-'           |
| \d{4}    | pasuje dokładnie 4-cyfrowymi znakami  |
| $        | dopasowuje koniec ciągu       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Ten pojedynczy wzorzec wyszukiwania pasuje do wielu prawidłowych ciągów. Wyrażenia regularne są lepiej wyszukać lub sprawdzić poprawność względem wzorca, a nie pojedynczego ciągu tekstowego.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [LINQ i ciągi](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework — Wyrażenia regularne](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Najważniejsze wskazówki dotyczące używania ciągów w sieci .NET](../../standard/base-types/best-practices-strings.md)
