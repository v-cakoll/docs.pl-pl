---
title: Jak wyszukiwać ciągi (Przewodnik w języku C#)
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

Aby wyszukać tekst w ciągach, można użyć dwóch głównych strategii. Metody <xref:System.String> klasy szukają określonego tekstu. Wyrażenia regularne wyszukują wzorce w tekście.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Typ [ciągu](../language-reference/builtin-types/reference-types.md#the-string-type) , który jest aliasem dla <xref:System.String?displayProperty=nameWithType> klasy, zapewnia wiele przydatnych metod wyszukiwania zawartości ciągu. Między nimi są <xref:System.String.Contains%2A> , <xref:System.String.StartsWith%2A> ,,, <xref:System.String.EndsWith%2A> <xref:System.String.IndexOf%2A> <xref:System.String.LastIndexOf%2A> . <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>Klasa zawiera bogate słownictwo do wyszukiwania wzorców w tekście. Ten artykuł zawiera informacje o tych technikach i sposobach wybierania najlepszej metody dla Twoich potrzeb.

## <a name="does-a-string-contain-text"></a>Czy ciąg zawiera tekst?

<xref:System.String.Contains%2A?displayProperty=nameWithType> <xref:System.String.StartsWith%2A?displayProperty=nameWithType> <xref:System.String.EndsWith%2A?displayProperty=nameWithType> Metody i przeszukują ciąg w poszukiwaniu określonego tekstu. Poniższy przykład pokazuje każdą z tych metod i odmianę, która używa wyszukiwania bez uwzględniania wielkości liter:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

W powyższym przykładzie przedstawiono ważny punkt korzystania z tych metod. W wyszukiwaniu jest domyślnie **rozróżniana wielkość** liter. <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>Wartość wyliczenia jest używana do określenia wyszukiwania bez uwzględniania wielkości liter.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Gdzie poszukiwany tekst występuje w ciągu?

<xref:System.String.IndexOf%2A>Metody i <xref:System.String.LastIndexOf%2A> wyszukują również tekst w ciągach. Metody te zwracają lokalizację tekstu, który jest szukiwany. Jeśli tekst nie zostanie znaleziony, zwracają `-1` . Poniższy przykład pokazuje wyszukiwanie pierwszego i ostatniego wystąpienia wyrazu "Methods" i wyświetla tekst między.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Znajdowanie określonego tekstu przy użyciu wyrażeń regularnych

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>Klasa może służyć do wyszukania ciągów. Te wyszukiwania mogą przedziałować złożoność od prostych do skomplikowanych wzorców tekstu.

Poniższy przykład kodu wyszukuje wyraz "" "lub" swój "w zdaniu, ignorując wielkość liter. Metoda statyczna <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> wykonuje wyszukiwanie. Należy podać ciąg do wyszukania i wzorzec wyszukiwania. W tym przypadku trzeci argument określa wyszukiwanie bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Wzorzec wyszukiwania opisuje szukany tekst. W poniższej tabeli opisano każdy element wzorca wyszukiwania. (W poniższej tabeli jest używany pojedynczy, `\` który musi zostać zmieniony jako `\\` ciąg w języku C#).

| znaczne  | Znaczenie     |
| -------- |-------------|
| względem zasobu      | dopasowuje tekst "" |
| (EIR)?   | dopasowuje 0 lub 1 wystąpienie "EIR" |
| \s       | Dopasowuje znak odstępu    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string`Metody są zwykle lepszymi opcjami podczas wyszukiwania dokładnego ciągu. Wyrażenia regularne są lepsze podczas wyszukiwania pewnego wzorca w ciągu źródłowym.

## <a name="does-a-string-follow-a-pattern"></a>Czy ciąg jest zgodny ze wzorcem?

Poniższy kod używa wyrażeń regularnych do sprawdzania poprawności formatu każdego ciągu w tablicy. Walidacja wymaga, aby każdy ciąg miał postać numeru telefonu, w którym trzy grupy cyfr są oddzielone kreskami, pierwsze dwie grupy zawierają trzy cyfry, a trzecia grupa zawiera cztery cyfry. Wzorzec wyszukiwania używa wyrażenia regularnego `^\\d{3}-\\d{3}-\\d{4}$` . Aby uzyskać więcej informacji, zobacz [Język wyrażeń regularnych — szybkie informacje](../../standard/base-types/regular-expression-language-quick-reference.md).

| znaczne  | Znaczenie                             |
| -------- |-------------------------------------|
| ^        | dopasowuje początek ciągu |
| \d{3}    | dopasowuje dokładnie 3 znaki cyfr  |
| -        | Dopasowuje znak "-"           |
| \d{3}    | dopasowuje dokładnie 3 znaki cyfr  |
| -        | Dopasowuje znak "-"           |
| \d{4}    | dopasowuje dokładnie 4 znaki cyfry  |
| $        | dopasowuje koniec ciągu       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Ten pojedynczy wzorzec wyszukiwania jest zgodny z wieloma prawidłowymi ciągami. Wyrażenia regularne służą lepiej do wyszukiwania lub weryfikowania wzorca, a nie pojedynczego ciągu tekstowego.

Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Możesz też pobrać przykłady [jako plik zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [LINQ i ciągi](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework — Wyrażenia regularne](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Najlepsze rozwiązania dotyczące używania ciągów w programie .NET](../../standard/base-types/best-practices-strings.md)
