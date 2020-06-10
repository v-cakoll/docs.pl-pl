---
title: Jak zmodyfikować zawartość ciągu — przewodnik w języku C#
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: a32665b67cfa73aa7d4753a1427c6955827e1b86
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663008"
---
# <a name="how-to-modify-string-contents-in-c"></a>Jak zmodyfikować zawartość ciągu w języku C\#

W tym artykule przedstawiono kilka technik, które należy utworzyć `string` , modyfikując istniejące `string` . Wszystkie techniki pokazują wynik modyfikacji jako nowy `string` obiekt. Aby jasno zademonstrować ten element, wszystkie przykłady zapisują wynik w nowej zmiennej. Następnie można przeanalizować zarówno oryginał `string` , jak i `string` wyniki modyfikacji podczas uruchamiania każdego przykładu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

W tym artykule przedstawiono kilka technik. Możesz zamienić istniejący tekst. Możesz wyszukać wzorce i zamienić pasujący tekst na inny tekst. Ciąg może być traktowany jako sekwencja znaków. Możesz również używać wygodnych metod, które usuwają biały znak. Wybierz techniki, które najlepiej pasują do Twojego scenariusza.

## <a name="replace-text"></a>Zastąp tekst

Poniższy kod tworzy nowy ciąg poprzez zastępowanie istniejącego tekstu substytutem.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet1":::

Poprzedni kod demonstruje tę *niemodyfikowalną* właściwość ciągów. W poprzednim przykładzie można zobaczyć, że oryginalny ciąg `source` nie jest modyfikowany. <xref:System.String.Replace%2A?displayProperty=nameWithType>Metoda tworzy nową `string` zawierającą modyfikacje.

<xref:System.String.Replace%2A>Metoda może zastąpić ciągi lub pojedyncze znaki. W obu przypadkach każde wystąpienie szukanego tekstu zostało zastąpione.  Poniższy przykład zastępuje wszystkie znaki "" "" \_ :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet2":::

Ciąg źródłowy jest niezmieniony i zwracany jest nowy ciąg.

## <a name="trim-white-space"></a>Przytnij biały znak

Można użyć <xref:System.String.Trim%2A?displayProperty=nameWithType> <xref:System.String.TrimStart%2A?displayProperty=nameWithType> metod, i, <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> Aby usunąć wszystkie wiodące lub końcowe białe znaki.  Poniższy kod przedstawia przykład każdego z nich. Ciąg źródłowy nie zmienia się; te metody zwracają nowy ciąg z zmodyfikowaną zawartością.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet3":::

## <a name="remove-text"></a>Usuń tekst

Można usunąć tekst z ciągu przy użyciu <xref:System.String.Remove%2A?displayProperty=nameWithType> metody. Ta metoda usuwa liczbę znaków, zaczynając od określonego indeksu. Poniższy przykład pokazuje, jak używać <xref:System.String.IndexOf%2A?displayProperty=nameWithType> , a następnie, <xref:System.String.Remove%2A> Aby usunąć tekst z ciągu:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet4":::

## <a name="replace-matching-patterns"></a>Zamień pasujące wzorce

Można użyć [wyrażeń regularnych](../../standard/base-types/regular-expressions.md) , aby zastąpić wzorce tekstu nowym tekstem, prawdopodobnie zdefiniowanym przez wzorzec. Poniższy przykład używa klasy, <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Aby znaleźć wzorzec w ciągu źródłowym i zamienić go na poprawną wielką literę. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType>Metoda przyjmuje funkcję, która udostępnia logikę wymiany jako jeden z jej argumentów. W tym przykładzie ta funkcja `LocalReplaceMatchCase` jest **funkcją lokalną** zadeklarowaną wewnątrz metody przykładowej. `LocalReplaceMatchCase`używa <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy do kompilowania ciągu zamiennego przy użyciu odpowiedniej wielkości liter.

Wyrażenia regularne są najbardziej przydatne do wyszukiwania i zamieniania tekstu, który następuje po wzorcu, a nie na znanym tekście. Aby uzyskać więcej informacji, zobacz [jak wyszukiwać ciągi](search-strings.md). Wzorzec wyszukiwania "the\s" wyszukuje wyraz "" ", po którym następuje znak odstępu. Ta część wzorca gwarantuje, że w ciągu źródłowym nie pasuje do "tam". Aby uzyskać więcej informacji na temat elementów języka wyrażenia regularnego, zobacz temat [wyrażenie regularne — szybkie odwołanie](../../standard/base-types/regular-expression-language-quick-reference.md).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet5":::

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>Metoda zwraca niezmienny ciąg z zawartością w <xref:System.Text.StringBuilder> obiekcie.

## <a name="modifying-individual-characters"></a>Modyfikowanie pojedynczych znaków

Można utworzyć tablicę znaków z ciągu, zmodyfikować zawartość tablicy, a następnie stworzyć nowy ciąg na podstawie zmodyfikowanej zawartości tablicy.

Poniższy przykład pokazuje, jak zastąpić zestaw znaków w ciągu. Najpierw używa <xref:System.String.ToCharArray?displayProperty=nameWithType> metody, aby utworzyć tablicę znaków. Używa metody, <xref:System.String.IndexOf%2A> Aby znaleźć początkowy indeks słowa "Fox". Następne trzy znaki są zastępowane innym słowem. Na koniec nowy ciąg jest tworzony na podstawie zaktualizowanej tablicy znaków.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet6":::

## <a name="programmatically-build-up-string-content"></a>Programowo Kompiluj zawartość ciągu

Ponieważ ciągi są niezmienne, poprzednie przykłady tworzą tymczasowe ciągi lub tablice znakowe. W scenariuszach o wysokiej wydajności może być wskazane uniknięcie tego przydziału sterty. Platforma .NET Core udostępnia <xref:System.String.Create%2A?displayProperty=nameWithType> metodę, która umożliwia programowe wprowadzanie zawartości znaku ciągu za pośrednictwem wywołania zwrotnego, unikając pośrednich tymczasowych alokacji ciągu.

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet7":::

Można zmodyfikować ciąg w stałym bloku z niebezpiecznym kodem, ale **zdecydowanie** odradza się modyfikowanie zawartości ciągu po utworzeniu ciągu. Wykonanie tej czynności spowoduje uszkodzenie elementów na nieprzewidywalny sposób. Na przykład, jeśli ktoś internił ciąg o tej samej zawartości, otrzyma kopię i nie będzie oczekiwać, że w ogóle modyfikujesz ciąg.

## <a name="see-also"></a>Zobacz także

- [.NET Framework wyrażeń regularnych](../../standard/base-types/regular-expressions.md)
- [Język wyrażeń regularnych — Krótki przewodnik](../../standard/base-types/regular-expression-language-quick-reference.md)
