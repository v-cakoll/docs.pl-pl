---
title: "Porady: wyszukiwanie ciągów (Przewodnik C#)"
ms.date: 02/21/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.author: wiwagn
ms.openlocfilehash: cb672ef74d9eb83df7d1c8985e518136dad54c34
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings"></a>Porady: wyszukiwanie ciągów

Dwie główne strategii służy do wyszukiwania tekstu w ciągach. Metody <xref:System.String> klasy, wyszukaj określony tekst. Wyrażenia regularne wyszukiwania wzorców w tekście.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

[Ciąg](../language-reference/keywords/string.md) typu, który jest aliasem dla <xref:System.String?displayProperty=nameWithType> klasy, udostępnia kilka metod przydatne wyszukiwania zawartości ciągu. Między nimi są <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa udostępnia bogate słownictwa wyszukiwania wzorców w tekście. W tym artykule dowiesz się, te techniki i Wybieranie najlepszej metody do własnych potrzeb.

## <a name="does-a-string-contain-text"></a>Ciąg zawiera tekst?

<xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> i <xref:System.String.EndsWith%2A?displayProperty=nameWithType> metody wyszukiwanie ciągu dla określonego tekstu. W poniższym przykładzie przedstawiono każdej z tych metod i zmiany, która używa wyszukiwania bez uwzględniania wielkości liter:

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

Pokazano w powyższym przykładzie ważnym dotyczące korzystania z tych metod. Podczas wyszukiwania jest **z uwzględnieniem wielkości liter** domyślnie. Możesz użyć <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> wartości wyliczenia, aby określić wyszukiwania bez uwzględniania wielkości liter.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Gdzie występuje poszukiwaną tekst w ciągu

<xref:System.String.IndexOf%2A> i <xref:System.String.LastIndexOf%2A> metody również wyszukać tekst w ciągach. Te metody zwracają lokalizacji poszukiwanego tekstu. Jeśli tekst nie zostanie odnaleziony, zwracają `-1`. Poniższy przykład przedstawia wyszukiwanie imię i nazwisko wystąpienia wyrazu "metody" i wyświetla tekst między nimi.
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a>Wyszukiwanie tekstu określonego za pomocą wyrażeń regularnych

<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Klasa może być używana do wyszukiwania ciągów. Te wyszukiwania można dostosować w zakresie w złożoności z proste wzorce tekstu skomplikowane.

Poniższy przykład kodu wyszukuje słowo "" lub "ich" w zdaniu, bez uwzględnienia wielkości liter. Statyczna metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> wykonuje wyszukiwanie. Możesz nadać jej ciągu wyszukiwania i wzorzec wyszukiwania. W takim przypadku trzeci argument określa wyszukiwania bez uwzględniania wielkości liter. Aby uzyskać więcej informacji, zobacz <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  

Wzorzec wyszukiwania opisuje tekst wyszukiwania. W poniższej tabeli opisano każdy element wzorzec wyszukiwania. (W poniższej tabeli używa jednego `\` którego należy zastosować ucieczkę jako `\\` w ciągu języka C#).

| wzorzec  | Znaczenie     |
| -------- |-------------|
| programu      | zgodny z tekstem "" |
| (eir)?   | dopasowania 0 lub 1 wystąpieniem "eir" |
| \s       | Dopasowuje biały znak    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> `string` Metody są zazwyczaj lepiej opcje podczas wyszukiwania dokładnie taki ciąg znaków. Wyrażenia regularne są lepiej podczas wyszukiwania dla niektórych wzorzec jest ciąg źródła.

## <a name="does-a-string-follow-a-pattern"></a>Ciąg jest zgodna z wzorcem?

Poniższy kod używa wyrażeń regularnych do walidacji format każdego ciągu w tablicy. Sprawdzanie poprawności musi mieć każdy ciąg formę numer telefonu, w którym trzech grup cyfr są oddzielone kreskami, pierwsze dwie grupy zawierają trzech cyfr i trzecia grupa zawiera cztery cyfry. Wzorzec wyszukiwania używa wyrażenia regularnego `^\\d{3}-\\d{3}-\\d{4}$`. Aby uzyskać więcej informacji, zobacz [język wyrażeń regularnych — podręczny wykaz](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).

| wzorzec  | Znaczenie                             |
| -------- |-------------------------------------|
| ^        | Dopasowuje początek ciągu |
| \d{3}    | Dopasowuje dokładnie 3 znaki cyfrę  |
| -        | Dopasowuje '-' znaków           |
| \d{3}    | Dopasowuje dokładnie 3 znaki cyfrę  |
| -        | Dopasowuje '-' znaków           |
| \d{4}    | Dopasowuje dokładnie 4 cyfry znaków  |
| $        | Dopasowuje koniec ciągu       |


[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

Ten wzorzec wyszukiwania pojedynczego odpowiada wielu prawidłowe ciągi. Wyrażenia regularne są lepiej wyszukiwania lub sprawdzania poprawności wzorca zamiast jeden ciąg tekstowy.

Możesz spróbować te przykłady, sprawdzając kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Można również pobrać próbki [jako plik zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też  

 [Przewodnik programowania w języku C#](../programming-guide/index.md)  
 [Ciągi](../programming-guide/strings/index.md)  
 [LINQ i ciągi](../programming-guide/concepts/linq/linq-and-strings.md)   
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>     
 [.NET framework — nieprawidłowe wyrażenia](../../standard/base-types/regular-expressions.md)   
 [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)   
 [Najlepsze rozwiązania dotyczące używania ciągów w .NET](../../standard/base-types/best-practices-strings.md)  
