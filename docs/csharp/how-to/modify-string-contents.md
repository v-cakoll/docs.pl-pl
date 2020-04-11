---
title: Jak zmodyfikować zawartość ciągu — Przewodnik języka C#
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 260e4022c514db0cee3c1459b9d746a1c8e2addd
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121127"
---
# <a name="how-to-modify-string-contents-in-c"></a>Jak zmodyfikować zawartość ciągu w języku C\#

W tym artykule przedstawiono `string` kilka technik do `string`produkcji przez modyfikację istniejącego . Wszystkie zademonstrowane techniki zwracają wynik modyfikacji jako `string` nowy obiekt. Aby wyraźnie to zademonstrować, wszystkie przykłady przechowują wynik w nowej zmiennej. Następnie można sprawdzić zarówno `string` oryginał `string` i wynikające z modyfikacji po uruchomieniu każdego przykładu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Istnieje kilka technik zademonstrowanych w tym artykule. Istniejący tekst można zastąpić. Można wyszukiwać wzory i zamieniać pasujący tekst na inny tekst. Ciąg można traktować jako sekwencję znaków. Można również użyć metod wygody, które usuwają odstęp. Należy wybrać techniki, które najbardziej pasują do scenariusza.

## <a name="replace-text"></a>Zamienianie tekstu

Poniższy kod tworzy nowy ciąg, zastępując istniejący tekst substytutem.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Poprzedni kod demonstruje tę *niezmienną* właściwość ciągów. W poprzednim przykładzie widać, `source`że oryginalny ciąg, nie jest modyfikowany. Metoda <xref:System.String.Replace%2A?displayProperty=nameWithType> tworzy nowy `string` zawierający modyfikacje.

Metoda <xref:System.String.Replace%2A> może zastąpić ciągi znaków lub pojedyncze znaki. W obu przypadkach każde wystąpienie poszukiwanego tekstu jest zastępowane.  Poniższy przykład zastępuje wszystkie znaki\_' ' z ':

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Ciąg źródłowy pozostaje niezmieniony, a nowy ciąg jest zwracany z zastąpieniem.

## <a name="trim-white-space"></a>Przycinanie odstępu

Można użyć <xref:System.String.Trim%2A?displayProperty=nameWithType>programu <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> i metod, aby usunąć wszelkie odstępy wiodące lub końcowe.  Poniższy kod przedstawia przykład każdego. Ciąg źródłowy nie zmienia się; te metody zwracają nowy ciąg ze zmodyfikowaną zawartością.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Usuwanie tekstu

Tekst z ciągu można usunąć <xref:System.String.Remove%2A?displayProperty=nameWithType> przy użyciu metody. Ta metoda usuwa liczbę znaków, począwszy od określonego indeksu. W poniższym przykładzie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> pokazano, jak <xref:System.String.Remove%2A> użyć, po którym należy usunąć tekst z ciągu:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Zamienianie pasujących wzorów

[Wyrażeń regularnych](../../standard/base-types/regular-expressions.md) można używać do zastępowania szyków dopasowywania tekstu nowym tekstem, ewentualnie zdefiniowanym przez wzorzec. W poniższym <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> przykładzie użyto klasy, aby znaleźć wzorzec w ciągu źródłowym i zastąpić go odpowiednią kapitalizacją. Metoda <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> przyjmuje funkcję, która zapewnia logikę zastąpienia jako jeden z jego argumentów. W tym przykładzie `LocalReplaceMatchCase` tej funkcji jest **funkcją lokalną** zadeklarowaną wewnątrz metody próbkowania. `LocalReplaceMatchCase`używa <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy do tworzenia ciągu zastępczego z odpowiednią kapitalizacją.

Wyrażenia regularne są najbardziej przydatne do wyszukiwania i zastępowania tekstu zgodnego ze wzorcem, a nie znanym tekstem. Zobacz [Jak wyszukiwać ciągi, aby](search-strings.md) uzyskać więcej szczegółów. Wzorzec wyszukiwania "the\s" wyszukuje słowo "the", po którym następuje znak odstępu. Ta część wzorca zapewnia, że nie pasuje "tam" w ciągu źródłowym. Aby uzyskać więcej informacji na temat elementów języka wyrażenia regularnego, zobacz [Język wyrażenia regularnego — podręczna dokumentacja](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

Metoda <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> zwraca niezmienny ciąg z zawartością <xref:System.Text.StringBuilder> w obiekcie.

## <a name="modifying-individual-characters"></a>Modyfikowanie pojedynczych znaków

Można utworzyć tablicę znaków z ciągu, zmodyfikować zawartość tablicy, a następnie utworzyć nowy ciąg ze zmodyfikowanej zawartości tablicy.

W poniższym przykładzie pokazano, jak zastąpić zestaw znaków w ciągu. Po pierwsze używa <xref:System.String.ToCharArray?displayProperty=nameWithName> metody do tworzenia tablicy znaków. Używa tej <xref:System.String.IndexOf%2A> metody, aby znaleźć indeks początkowy słowa "lis". Następne trzy znaki zostaną zastąpione innym słowem. Na koniec nowy ciąg jest konstruowany z tablicy zaktualizowanych znaków.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programowo skompiluj zawartość ciągu

Ponieważ ciągi są niezmienne, poprzednie przykłady wszystkie utworzyć tymczasowe ciągi lub tablice znaków. W scenariuszach wysokiej wydajności może być pożądane, aby uniknąć tych alokacji sterty. .NET Core <xref:System.String.Create%2A?displayProperty=nameWithType> zapewnia metodę, która umożliwia programowe wypełnianie zawartości znaku ciągu za pomocą wywołania zwrotnego, unikając pośrednich alokacji ciągów tymczasowych.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Można zmodyfikować ciąg w stałym bloku z niebezpiecznym kodem, ale jest **zdecydowanie** odradzane, aby zmodyfikować zawartość ciągu po utworzeniu ciągu. W ten sposób złamie rzeczy w nieprzewidywalny sposób. Na przykład jeśli ktoś stażysta ciąg, który ma taką samą zawartość jak Twoja, otrzymają kopię i nie będzie oczekiwać, że modyfikujesz ich ciąg w ogóle.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [.NET Framework — Wyrażenia regularne](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
