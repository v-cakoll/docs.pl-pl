---
title: Jak wyszukiwać ciągi znaków (Przewodnik po języku C#)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 15ea77d13a93d88bd996a22b6fe1aaad81df572d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74959705"
---
# <a name="how-to-search-strings"></a>Jak wyszukiwać ciągi

Do wyszukiwania tekstu w ciągach można użyć dwóch głównych strategii. Metody wyszukiwania <xref:System.String> klasy dla określonego tekstu. Wyrażenia regularne wyszukują wzorce w tekście.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Typ [ciągu,](../language-reference/builtin-types/reference-types.md#the-string-type) który jest aliasem dla <xref:System.String?displayProperty=nameWithType> klasy, zawiera szereg przydatnych metod wyszukiwania zawartości ciągu. Wśród nich <xref:System.String.Contains%2A> <xref:System.String.StartsWith%2A>są <xref:System.String.EndsWith%2A> <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>, , . Klasa <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> zapewnia bogate słownictwo do wyszukiwania wzorców w tekście. W tym artykule, można dowiedzieć się tych technik i jak wybrać najlepszą metodę dla twoich potrzeb.

## <a name="does-a-string-contain-text"></a>Czy ciąg zawiera tekst?

<xref:System.String.Contains%2A?displayProperty=nameWithType>Przyciski <xref:System.String.StartsWith%2A?displayProperty=nameWithType> <xref:System.String.EndsWith%2A?displayProperty=nameWithType> i metody wyszukiwania ciągu dla określonego tekstu. W poniższym przykładzie przedstawiono każdą z tych metod i odmianę, która używa wyszukiwania bez uwzględniania wielkości liter:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

W poprzednim przykładzie przedstawiono ważny punkt przy użyciu tych metod. W wyszukiwarce domyślnie **jest z uwzględnieniem wielkości liter.** Wartość wyliczenia <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> służy do określania wyszukiwania bez uwzględniania wielkości liter.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Gdzie występuje poszukiwany tekst w ciągu?

Metody <xref:System.String.IndexOf%2A> <xref:System.String.LastIndexOf%2A> i również wyszukać tekst w ciągach. Metody te zwracają lokalizację poszukiwanego tekstu. Jeśli tekst nie zostanie znaleziony, `-1`powracają . W poniższym przykładzie przedstawiono wyszukiwanie pierwszego i ostatniego wystąpienia słowa "metody" i wyświetla tekst pomiędzy nimi.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Znajdowanie określonego tekstu przy użyciu wyrażeń regularnych

Klasa <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> może służyć do wyszukiwania ciągów. Te wyszukiwania mogą się wahać w złożoności od prostych do skomplikowanych wzorców tekstu.

Poniższy przykład kodu wyszukuje słowo "the" lub "ich" w zdaniu, ignorując sprawę. Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> statyczna wykonuje wyszukiwanie. Nadaj mu ciąg wyszukiwania i wzorzec wyszukiwania. W takim przypadku trzeci argument określa wyszukiwanie bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Wzorzec wyszukiwania opisuje wyszukiwany tekst. W poniższej tabeli opisano każdy element wzorca wyszukiwania. (W poniższej tabeli `\` użyto pojedynczego, który musi być uciekł, jak `\\` w ciągu C#).

| Wzór  | Znaczenie     |
| -------- |-------------|
| względem zasobu      | dopasowywać tekst "the" |
| (eir)?   | mecz 0 lub 1 wystąpienie "eir" |
| \s       | dopasowywanie znaku odstępu    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Metody są zwykle lepszym wyborem podczas wyszukiwania dokładnego ciągu. Wyrażenia regularne są lepsze, gdy szukasz wzorka w ciągu źródłowym.

## <a name="does-a-string-follow-a-pattern"></a>Czy ciąg podąża za wzorcem?

Poniższy kod używa wyrażeń regularnych do sprawdzania poprawności formatu każdego ciągu w tablicy. Sprawdzanie poprawności wymaga, aby każdy ciąg miał postać numeru telefonu, w którym trzy grupy cyfr są oddzielone myślnikami, pierwsze dwie grupy zawierają trzy cyfry, a trzecia grupa zawiera cztery cyfry. Wzorzec wyszukiwania `^\\d{3}-\\d{3}-\\d{4}$`używa wyrażenia regularnego . Aby uzyskać więcej informacji, zobacz [Język wyrażenia regularnego — podręczny numer referencyjny](../../standard/base-types/regular-expression-language-quick-reference.md).

| Wzór  | Znaczenie                             |
| -------- |-------------------------------------|
| ^        | pasuje do początku ciągu |
| \d{3}    | pasuje dokładnie do 3-cyfrowych znaków  |
| -        | pasuje do znaku '-'           |
| \d{3}    | pasuje dokładnie do 3-cyfrowych znaków  |
| -        | pasuje do znaku '-'           |
| \d{4}    | pasuje dokładnie do 4-cyfrowych znaków  |
| $        | pasuje do końca ciągu       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Ten pojedynczy wzorzec wyszukiwania pasuje do wielu prawidłowych ciągów. Wyrażenia regularne są lepiej wyszukiwać lub sprawdzać poprawność względem wzorca, a nie pojedynczy ciąg tekstowy.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [LINQ i ciągi](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [.NET Framework — Wyrażenia regularne](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Najważniejsze wskazówki dotyczące używania ciągów w .NET](../../standard/base-types/best-practices-strings.md)
