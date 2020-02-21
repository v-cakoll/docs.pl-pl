---
title: Jak zmodyfikować zawartość ciągu — C# Przewodnik
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: ecedd9a9027aa925c753f8e187d611b19d3db991
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543264"
---
# <a name="how-to-modify-string-contents-in-c"></a>Jak zmodyfikować zawartość ciągu w języku C\#

W tym artykule przedstawiono kilka technik tworzenia `string`, modyfikując istniejące `string`. Wszystkie przedstawione techniki zwracają wynik modyfikacji jako nowy obiekt `string`. Aby jasno zademonstrować ten element, wszystkie przykłady zapisują wynik w nowej zmiennej. Następnie można przeanalizować zarówno oryginalny `string`, jak i `string` wynikający z modyfikacji podczas uruchamiania każdego przykładu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W tym artykule przedstawiono kilka technik. Możesz zamienić istniejący tekst. Możesz wyszukać wzorce i zamienić pasujący tekst na inny tekst. Ciąg może być traktowany jako sekwencja znaków. Możesz również używać wygodnych metod, które usuwają biały znak. Należy wybrać techniki, które najlepiej pasują do Twojego scenariusza.

## <a name="replace-text"></a>Zastąp tekst

Poniższy kod tworzy nowy ciąg poprzez zastępowanie istniejącego tekstu substytutem.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Poprzedni kod demonstruje tę *niemodyfikowalną* właściwość ciągów. W poprzednim przykładzie można zobaczyć, że oryginalny ciąg, `source`, nie jest modyfikowany. Metoda <xref:System.String.Replace%2A?displayProperty=nameWithType> tworzy nowy `string` zawierający modyfikacje.

Metoda <xref:System.String.Replace%2A> może zastąpić ciągi lub pojedyncze znaki. W obu przypadkach każde wystąpienie szukanego tekstu zostało zastąpione.  Poniższy przykład zastępuje wszystkie znaki "" "\_":

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Ciąg źródłowy jest niezmieniony i zwracany jest nowy ciąg.

## <a name="trim-white-space"></a>Przytnij biały znak

Możesz użyć metod <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>i <xref:System.String.TrimEnd%2A?displayProperty=nameWithType>, aby usunąć wszystkie wiodące i końcowe białe znaki.  Poniższy kod przedstawia przykład każdego z nich. Ciąg źródłowy nie zmienia się; te metody zwracają nowy ciąg z zmodyfikowaną zawartością.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Usuń tekst

Można usunąć tekst z ciągu przy użyciu metody <xref:System.String.Remove%2A?displayProperty=nameWithType>. Ta metoda usuwa liczbę znaków, zaczynając od określonego indeksu. Poniższy przykład pokazuje, jak używać <xref:System.String.IndexOf%2A?displayProperty=nameWithType> i <xref:System.String.Remove%2A> do usuwania tekstu z ciągu:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Zamień pasujące wzorce

Można użyć [wyrażeń regularnych](../../standard/base-types/regular-expressions.md) , aby zastąpić wzorce tekstu nowym tekstem, prawdopodobnie zdefiniowanym przez wzorzec. Poniższy przykład używa klasy <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>, aby znaleźć wzorzec w ciągu źródłowym i zastąpić go odpowiednią wielką literą. Metoda <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> przyjmuje funkcję, która udostępnia logikę wymiany jako jeden z jej argumentów. W tym przykładzie ta funkcja `LocalReplaceMatchCase` jest **funkcją lokalną** zadeklarowaną wewnątrz metody przykładowej. `LocalReplaceMatchCase` używa klasy <xref:System.Text.StringBuilder?displayProperty=nameWithType> do kompilowania ciągu zamiennego przy użyciu odpowiedniej wielkości liter.

Wyrażenia regularne są najbardziej przydatne do wyszukiwania i zamieniania tekstu, który następuje po wzorcu, a nie na znanym tekście. Zobacz [jak wyszukiwać ciągi,](search-strings.md) Aby uzyskać więcej szczegółów. Wzorzec wyszukiwania "the\s" wyszukuje wyraz "" ", po którym następuje znak odstępu. Ta część wzorca gwarantuje, że w ciągu źródłowym nie pasuje do "tam". Aby uzyskać więcej informacji na temat elementów języka wyrażenia regularnego, zobacz temat [wyrażenie regularne — szybkie odwołanie](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

Metoda <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> zwraca niezmienny ciąg z zawartością w obiekcie <xref:System.Text.StringBuilder>.

## <a name="modifying-individual-characters"></a>Modyfikowanie pojedynczych znaków

Można utworzyć tablicę znaków z ciągu, zmodyfikować zawartość tablicy, a następnie stworzyć nowy ciąg na podstawie zmodyfikowanej zawartości tablicy.

Poniższy przykład pokazuje, jak zastąpić zestaw znaków w ciągu. Najpierw używa metody <xref:System.String.ToCharArray?displayProperty=nameWithName>, aby utworzyć tablicę znaków. Używa metody <xref:System.String.IndexOf%2A>, aby znaleźć początkowy indeks słowa "Fox". Następne trzy znaki są zastępowane innym słowem. Na koniec nowy ciąg jest tworzony na podstawie zaktualizowanej tablicy znaków.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programowo Kompiluj zawartość ciągu

Ponieważ ciągi są niezmienne, poprzednie przykłady tworzą tymczasowe ciągi lub tablice znakowe. W scenariuszach o wysokiej wydajności może być wskazane uniknięcie tego przydziału sterty. Platforma .NET Core udostępnia metodę <xref:System.String.Create%2A?displayProperty=nameWithType>, która pozwala programistycznie wprowadzać zawartość znaku ciągu za pośrednictwem wywołania zwrotnego, unikając pośrednich tymczasowych alokacji ciągu.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Można zmodyfikować ciąg w stałym bloku z niebezpiecznym kodem, ale **zdecydowanie** odradza się modyfikowanie zawartości ciągu po utworzeniu ciągu. Wykonanie tej czynności spowoduje uszkodzenie elementów na nieprzewidywalny sposób. Na przykład, jeśli ktoś internił ciąg o tej samej zawartości, otrzyma kopię i nie będzie oczekiwać, że w ogóle modyfikujesz ciąg.

Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz też

- [.NET Framework wyrażeń regularnych](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)
