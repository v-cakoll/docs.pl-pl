---
title: 'Porady: wyszukiwanie ciągów (Przewodnik C#)'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: b9c27e419d37b6c0730f214d3b2b9bbdf7e30d11
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202876"
---
# <a name="how-to-search-strings"></a>Porady: wyszukiwanie ciągów

Aby wyszukać tekst w ciągach, można użyć dwóch strategii głównego. Metody <xref:System.String> Wyszukiwanie klas dla określonego tekstu. Wyrażenia regularne wyszukiwanie wzorców tekstu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

[Ciąg](../language-reference/keywords/string.md) typ, który jest aliasem dla <xref:System.String?displayProperty=nameWithType> klasy, udostępnia wiele użytecznych metod wyszukiwać zawartość ciągu. Między nimi są <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa oferuje rozbudowane słownictwa wyszukiwanie wzorców tekstu. W tym artykule dowiesz się, te techniki oraz sposobu wybierania najlepszą metodę do własnych potrzeb.

## <a name="does-a-string-contain-text"></a>Ciąg zawiera tekst?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> i <xref:System.String.EndsWith%2A?displayProperty=nameWithType> metody wyszukują ciągu dla określonego tekstu. Poniższy przykład przedstawia każdego z tych metod oraz zmianę, która korzysta z search nie rozróżnia wielkości liter:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Pokazano w powyższym przykładzie to ważny punkt dotyczące korzystania z tych metod. Podczas wyszukiwania jest **liter** domyślnie. Możesz użyć <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> wartość wyliczenia, aby określić wyszukiwania bez uwzględniania wielkości liter.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Gdzie występuje tekstu używanych w ciągu

<xref:System.String.IndexOf%2A> i <xref:System.String.LastIndexOf%2A> metody również wyszukać tekst w ciągach. Te metody zwracają lokalizacja tekstu niestabilna. Jeśli tekst nie zostanie znaleziona, zwracają one `-1`. Poniższy przykład pokazuje, wyszukaj pierwsze i ostatnie wystąpienie wyrazu "metody" i wyświetla tekst między.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Określony tekst wyszukiwania za pomocą wyrażeń regularnych

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa może być używana do wyszukiwania ciągów. Wyszukiwanie można dostosować w zakresie złożonością, od prostych do wzorców tekstu skomplikowane.

Poniższy przykładowy kod wyszukuje słowo "" lub "ich" w zdaniu, bez uwzględnienia wielkości liter. Metoda statyczna <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> wykonuje wyszukiwanie. Możesz nadać mu ciąg do wyszukiwania i wzorzec wyszukiwania. W tym przypadku trzeci argument określa wyszukiwanie bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Wzorzec wyszukiwania w tym artykule opisano tekst, który możesz wyszukać. W poniższej tabeli opisano każdy element wzorzec wyszukiwania. (W poniższej tabeli używa pojedynczego `\` muszą być wyjściowym jako `\\` w ciągu języka C#).

| wzorzec  | Znaczenie     |
| -------- |-------------|
| W      | tekst "" |
| (eir)?   | dopasowania 0 lub 1 wystąpienie "eir" |
| \s       | Dopasowuje znak odstępu    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Metody są zazwyczaj lepiej opcje podczas wyszukiwania dokładnie taki ciąg znaków. Wyrażenia regularne, są lepiej podczas wyszukiwania dla niektórych wzorzec jest ciągiem źródła.

## <a name="does-a-string-follow-a-pattern"></a>Ciąg jest zgodna z wzorcem?

W poniższym kodzie użyto wyrażenia regularne, aby sprawdzić poprawność format każdego ciągu w tablicy. Weryfikacja wymaga każdego ciągu formularza numer telefonu, w którym trzy grupy cyfry są oddzielone kreskami, pierwsze dwie grupy zawierać trzy cyfry, a trzecia grupa zawiera cztery cyfry. Wzorzec wyszukiwania używa wyrażenia regularnego `^\\d{3}-\\d{3}-\\d{4}$`. Aby uzyskać więcej informacji, zobacz [język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md).

| wzorzec  | Znaczenie                             |
| -------- |-------------------------------------|
| ^        | pasuje do początku ciągu |
| \d{3}    | Dopasowuje dokładnie 3 znaki cyfr  |
| -        | pasuje do "-" znaków           |
| \d{3}    | Dopasowuje dokładnie 3 znaki cyfr  |
| -        | pasuje do "-" znaków           |
| \d{4}    | Dopasowuje dokładnie 4 znaki cyfr  |
| $        | Dopasowuje koniec ciągu       |

[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Ten wzorzec wyszukiwania pojedynczego pasuje wiele prawidłowe ciągi. Wyrażenia regularne są lepiej wyszukiwania lub przeprowadzić walidacji względem wzorca, a nie jeden ciąg tekstowy.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../programming-guide/index.md)
- [Ciągi](../programming-guide/strings/index.md)
- [LINQ i ciągi](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Wyrażeń regularnych programu .NET framework](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Najlepsze rozwiązania dotyczące używania ciągów w programie .NET](../../standard/base-types/best-practices-strings.md)
