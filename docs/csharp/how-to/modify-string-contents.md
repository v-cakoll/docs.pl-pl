---
title: 'Porady: modyfikowanie zawartości ciągu — Przewodnik po języku C#'
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: 23d52a52291b3d5c36fc2ed0f299ab82aa5ffabd
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260181"
---
# <a name="how-to-modify-string-contents-in-c"></a>Porady: modyfikowanie zawartości ciągu w języku C\#

W tym artykule przedstawiono kilka technik w celu wygenerowania `string` , modyfikując istniejące `string`. Wszystkie techniki przedstawione w artykule zwracają wynik modyfikacji jako nową `string` obiektu. Aby zademonstrować to wyraźnie, wszystkie przykłady przechowuje wynik w nowej zmiennej. Następnie można sprawdzić zarówno oryginał `string` i `string` wynikające z modyfikacji, po uruchomieniu każdy przykład.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Istnieje kilka technik, które przedstawiono w tym artykule. Możesz zastąpić istniejący tekst. Możesz wyszukiwać wzorce i Zastąp pasujący tekst i inne teksty. Ciąg można traktować jako sekwencja znaków. Można również użyć metod jako udogodnienie, które Usuń biały znak. Należy wybrać technik, które najlepiej pasują do scenariusza.

## <a name="replace-text"></a>Zastąp tekst

Poniższy kod tworzy nowy ciąg, zastępując istniejący tekst zastępczy.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Poprzedni kod pokazuje to *niezmienne* właściwości ciągów. Widać w powyższym przykładzie, oryginalny ciąg `source`, nie jest modyfikowany. <xref:System.String.Replace%2A?displayProperty=nameWithType> Metoda tworzy nowy `string` zawierający modyfikacje.

<xref:System.String.Replace%2A> Metoda może zastąpić ciągi lub pojedyncze znaki. W obu przypadkach każde wystąpienie tekstu używanych jest zastępowany.  Poniższy przykład zastępuje wszystkie ' "znaków za pomocą"\_":

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Ciąg źródłowy pozostaje niezmieniony, a nowy ciąg jest zwracany za pomocą zastąpienia.

## <a name="trim-white-space"></a>Przytnij odstęp

Możesz użyć <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, i <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> metody, aby usunąć wszystkie wiodące i końcowe białe.  Poniższy kod przedstawia przykład każdego z nich. Ciąg źródłowy nie zmienia się; tych metod zwraca nowy ciąg z zawartością zmodyfikowane.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Usuń tekst

Tekst można usunąć z na ciąg za pośrednictwem <xref:System.String.Remove%2A?displayProperty=nameWithType> metody. Ta metoda usuwa określonej liczby znaków, zaczynając od określonego indeksu. Poniższy przykład pokazuje, jak używać <xref:System.String.IndexOf%2A?displayProperty=nameWithType> następuje <xref:System.String.Remove%2A> Aby usunąć tekst z ciągu:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Zastąp wzorce dopasowania

Możesz użyć [wyrażeń regularnych](../../standard/base-types/regular-expressions.md) tekst wzorce nowym tekstem, prawdopodobnie zdefiniowane przez wzorzec dopasowywania. W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> klasy w celu znalezienia wzorca w ciągu źródłowym i zastąp go właściwego użycia wielkich liter. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> Metoda przyjmuje funkcję, która udostępnia logikę zastąpienia jako jeden z jej argumentów. W tym przykładzie tej funkcji, `LocalReplaceMatchCase` jest **funkcja lokalna** zadeklarowana wewnątrz przykładowa metoda. `LocalReplaceMatchCase` używa <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasa do tworzenia ciąg zastępujący przy użyciu prawidłowego użycia wielkich liter.

Wyrażenia regularne są najbardziej przydatne do wyszukiwania i zastępując tekst, który jest zgodna ze wzorcem, a nie znane tekstu. Zobacz [porady: wyszukiwanie ciągów](search-strings.md) Aby uzyskać więcej informacji. Wzorzec wyszukiwania "the\s" wyszukiwane słowa "" następuje znak odstępu. Tę część wzorca gwarantuje, że nie jest zgodna "Brak" w ciągu źródłowego. Aby uzyskać więcej informacji na temat elementy języka wyrażeń regularnych, zobacz [język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> Metoda zwraca ciąg niezmienne z zawartością w <xref:System.Text.StringBuilder> obiektu.

## <a name="modifying-individual-characters"></a>Modyfikowanie pojedynczych znaków

Można utworzyć tablicy znaków z ciągu, modyfikowania zawartości tablicy, a następnie utwórz nowy ciąg z zmodyfikowanej zawartości tablicy.

Poniższy przykład pokazuje, jak zastąpić zestaw znaków w ciągu. Po pierwsze, używa <xref:System.String.ToCharArray?displayProperty=nameWithName> metodę, aby utworzyć tablicę znaków. Używa ona <xref:System.String.IndexOf%2A> metody do znalezienia indeks początkowy słowo "fox." Kolejne trzy znaki są zastępowane innego programu word. Na koniec nowy ciąg jest tworzony z tablicy znaków zaktualizowane.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Niebezpieczne modyfikacji ciągu

Przy użyciu **niebezpieczne** kodu, ciąg "w miejscu" można zmodyfikować po utworzeniu. Niebezpieczny kod pomija wielu funkcji programu .NET, aby zminimalizować niektórych rodzajów błędów w kodzie. Należy użyć niebezpieczny kod można zmodyfikować parametry w miejscu, ponieważ klasa string został zaprojektowany jako **niezmienne** typu. Po jego utworzeniu, jego wartość nie ulega zmianie. Niebezpieczny kod zmierzone tej właściwości przez dostęp i modyfikowania pamięci używanej przez `string` bez korzystania z normalnym `string` metody.
Poniższy przykład znajduje się w tych rzadkich sytuacjach, gdzie chcesz zmodyfikować parametry w miejscu przy użyciu niebezpieczny kod. W przykładzie pokazano sposób użycia `fixed` — słowo kluczowe. `fixed` — Słowo kluczowe zapobiega przenoszenie z obiektem ciągu w pamięci, gdy kod uzyskuje dostęp do pamięci, przy użyciu wskaźnika niebezpieczny moduł odśmiecania pamięci (GC). Ilustruje też możliwe po stronie efektem użycia niebezpieczne operacje na ciągi powstałego w sposób, że kompilator języka C# wewnętrznie przechowuje ciągi (stażystów). Ogólnie rzecz biorąc nie należy używać tej techniki, chyba że jest to absolutnie konieczne. Możesz dowiedzieć się więcej, czytając artykuły na [niebezpieczne](../language-reference/keywords/unsafe.md) i [stałej](../language-reference/keywords/fixed-statement.md). Dokumentacja interfejsu API <xref:System.String.Intern%2A> obejmuje informacji na temat wewnętrzne przygotowanie ciągu.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET framework](../../standard/base-types/regular-expressions.md)  
- [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)  
