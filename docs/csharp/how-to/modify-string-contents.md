---
title: Jak zmodyfikować zawartość ciągu - C# Przewodnik
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: ecedd9a9027aa925c753f8e187d611b19d3db991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543264"
---
# <a name="how-to-modify-string-contents-in-c"></a>Jak zmodyfikować zawartość ciągu w C\#

W tym artykule przedstawiono kilka `string` technik tworzenia `string`przez modyfikowanie istniejącego . Wszystkie zademonstrowane techniki zwracają wynik modyfikacji jako nowy `string` obiekt. Aby wyraźnie to zademonstrować, przykłady wszystkie przechowywać wynik w nowej zmiennej. Następnie można sprawdzić zarówno `string` oryginał, jak `string` i wynikające z modyfikacji po uruchomieniu każdego przykładu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Istnieje kilka technik wykazano w tym artykule. Można zastąpić istniejący tekst. Można wyszukiwać wzorce i zastępować pasujący tekst innym tekstem. Ciąg znaków można traktować jako sekwencję znaków. Można również użyć metod wygody, które usuwają biały znak. Należy wybrać techniki, które najbardziej odpowiadają scenariuszowi.

## <a name="replace-text"></a>Zastępowanie tekstu

Poniższy kod tworzy nowy ciąg, zastępując istniejący tekst substytutem.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Poprzedni kod demonstruje tę *niezmienną* właściwość ciągów. W poprzednim przykładzie widać, `source`że oryginalny ciąg , nie jest modyfikowany. Metoda <xref:System.String.Replace%2A?displayProperty=nameWithType> tworzy nowy `string` zawierający modyfikacje.

Metoda <xref:System.String.Replace%2A> może zastąpić ciągi lub pojedyncze znaki. W obu przypadkach każde wystąpienie poszukiwanego tekstu jest zastępowane.  Poniższy przykład zastępuje wszystkie ' '\_znaków z ' ":

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Ciąg źródłowy pozostaje bez zmian, a nowy ciąg jest zwracany z zastąpieniem.

## <a name="trim-white-space"></a>Przycinanie odstępu

Można użyć <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>i <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> metody, aby usunąć wszelkie interweniujące lub końcowe biały znak.  Poniższy kod przedstawia przykład każdego z nich. Ciąg źródłowy nie zmienia się; metody te zwracają nowy ciąg ze zmodyfikowaną zawartością.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Usuwanie tekstu

Tekst można usunąć z ciągu <xref:System.String.Remove%2A?displayProperty=nameWithType> za pomocą tej metody. Ta metoda usuwa liczbę znaków rozpoczynających się od określonego indeksu. W poniższym przykładzie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> pokazano, jak użyć, a <xref:System.String.Remove%2A> następnie usunąć tekst z ciągu:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Zastępowanie pasujących desek

Wyrażenia regularne można używać do [zastępowania wzorców](../../standard/base-types/regular-expressions.md) dopasowywania tekstu nowym tekstem, prawdopodobnie zdefiniowanym przez wzorzec. W poniższym <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> przykładzie użyto klasy, aby znaleźć wzorzec w ciągu źródłowym i zastąpić go poproper capitalization. Metoda <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> przyjmuje funkcję, która zapewnia logikę zastąpienia jako jeden z jego argumentów. W tym przykładzie tej `LocalReplaceMatchCase` funkcji jest **funkcja lokalna** zadeklarowana wewnątrz metody próbki. `LocalReplaceMatchCase`używa <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy do tworzenia ciągu zastępczego z poprawidłową kapitalizacją.

Wyrażenia regularne są najbardziej przydatne do wyszukiwania i zastępowania tekstu następującego po wzorcu, a nie znanego tekstu. Zobacz [Jak wyszukiwać ciągi, aby](search-strings.md) uzyskać więcej informacji. Wzorzec wyszukiwania "the\s" wyszukuje słowo "the", po którym następuje znak odstępu. Ta część wzorca zapewnia, że nie pasuje "tam" w ciągu źródłowym. Aby uzyskać więcej informacji na temat elementów języka wyrażenia regularnego, zobacz [Język wyrażenia regularnego — szybkie odwołanie](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

Metoda <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> zwraca niezmienny ciąg z zawartością <xref:System.Text.StringBuilder> w obiekcie.

## <a name="modifying-individual-characters"></a>Modyfikowanie pojedynczych znaków

Tablicę znaków można utworzyć z ciągu, zmodyfikować zawartość tablicy, a następnie utworzyć nowy ciąg ze zmodyfikowanej zawartości tablicy.

W poniższym przykładzie pokazano, jak zastąpić zestaw znaków w ciągu. Po pierwsze używa <xref:System.String.ToCharArray?displayProperty=nameWithName> metody do tworzenia tablicy znaków. Używa metody, <xref:System.String.IndexOf%2A> aby znaleźć początkowy indeks słowa "lis". Następne trzy znaki są zastępowane innym słowem. Na koniec nowy ciąg jest konstruowany z zaktualizowanej tablicy znaków.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programowo tworzenie zawartości ciągu

Ponieważ ciągi są niezmienne, poprzednie przykłady tworzą tymczasowe ciągi lub tablice znaków. W scenariuszach o wysokiej wydajności może być pożądane, aby uniknąć tych alokacji sterty. .NET Core <xref:System.String.Create%2A?displayProperty=nameWithType> udostępnia metodę, która umożliwia programowo wypełnić zawartość znaku ciągu za pośrednictwem wywołania odwróconego przy jednoczesnym uniknięciu pośrednich tymczasowych alokacji ciągów.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Można zmodyfikować ciąg w stałym bloku z niebezpiecznym kodem, ale **zdecydowanie** odradza się modyfikowanie zawartości ciągu po utworzeniu ciągu. W ten sposób wszystko spowoduje, że wszystko będzie w nieprzewidywalne sposób. Na przykład jeśli ktoś internuje ciąg, który ma taką samą zawartość jak Twoja, otrzyma twoją kopię i nie będzie oczekiwać, że w ogóle modyfikujesz ich ciąg.

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać próbki [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [.NET Framework — Wyrażenia regularne](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
