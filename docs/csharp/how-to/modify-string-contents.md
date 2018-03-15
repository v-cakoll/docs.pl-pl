---
title: "Porady: modyfikowanie zawartości ciągu - przewodnik C#"
ms.date: 02/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- strings [C#], modifying
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 830ca207c4cd5bd24dbb667328465cafb2509409
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-modify-string-contents-in-c"></a>Porady: modyfikowanie zawartości ciągu w języku C# #

W tym artykule przedstawiono kilka technik w celu utworzenia `string` przez zmodyfikowanie istniejącej `string`. Wszystkie techniki przedstawiona zwracają wynik jako nowe zmiany `string` obiektu. Aby zademonstrować to wyraźnie, wszystkie przykłady przechowywać wynik w nowej zmiennej. Następnie można sprawdzić zarówno oryginalny `string` i `string` wynikające z modyfikacji podczas uruchamiania każdy przykład.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Istnieje kilka technik przedstawiona w tym artykule. Można zastąpić istniejącego tekstu. Można wyszukać wzorców i zamienić szukanego tekstu inny tekst. Ciąg można traktować jako sekwencja znaków. Umożliwia także podręczne metody, które Usuń biały znak. Należy wybrać techniki, które najlepiej pasują danego scenariusza.

## <a name="replace-text"></a>Zastępowanie tekstu

Poniższy kod tworzy nowe parametry, zastępując istniejący tekst zastępczy.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Poprzedni kod pokazuje to *niezmienne* właściwości ciągów. Można zobaczyć w poprzednim przykładzie który oryginalnego ciągu `source`, nie jest modyfikowany. <xref:System.String.Replace%2A?displayProperty=nameWithType> Metoda tworzy nowy `string` zawierające te zmiany.

<xref:System.String.Replace%2A> Metody można zastąpić, ciągi lub pojedynczy znaki. W obu przypadkach każde wystąpienie poszukiwaną tekst został zastąpiony.  Poniższy przykład zastępuje wszystkie ' "znaków i zawierają"\_":

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Ciąg źródłowy jest bez zmian, a nowy ciąg z zastąpienia.

## <a name="trim-white-space"></a>TRIM biały znak

Można użyć <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>, i <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> metod, aby usunąć wszystkie białe wiodących lub końcowych.  Poniższy kod przedstawia przykład każdego z nich. Ciąg źródłowy nie ulega zmianie; te metody zwracają nowe parametry z zawartością, zmodyfikowany.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Usuń tekst

Możesz usunąć tekst z ciągu za pomocą <xref:System.String.Remove%2A?displayProperty=nameWithType> metody. Ta metoda usuwa liczba znaków, zaczynając od określonego indeksu. Poniższy przykład przedstawia użycie <xref:System.String.IndexOf%2A?displayProperty=nameWithType> następuje <xref:System.String.Remove%2A> do usunięcia z ciągu tekstowego:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Zastąp wzorce dopasowania

Można użyć [wyrażeń regularnych](../../standard/base-types/regular-expressions.md) tekst wzorce nowym tekstem, prawdopodobnie wynika z wzorca dopasowania. W poniższym przykładzie użyto <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> klasy można znaleźć wzorzec ciągu źródła i Zamień odpowiednie wielkości liter. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> Metoda przyjmuje funkcja, która udostępnia logikę zastąpienia jako jeden z jego argumentów. W tym przykładzie, że funkcja `LocalReplaceMatchCase` jest **funkcja lokalna** deklarowane w przykładowej metody. `LocalReplaceMatchCase` używa <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasa do tworzenia ciąg zastępczy z właściwego wielkość liter.

Wyrażenia regularne są najbardziej przydatny w przypadku wyszukiwania i zastępowanie tekstu, która jest zgodna ze wzorcem zamiast tekstu znane. Zobacz [porady: wyszukiwanie ciągów](search-strings.md) więcej szczegółów. Wzorzec wyszukiwania "the\s" Wyszukiwanie słowa "" następuje biały znak. Części wzorca gwarantuje, że nie jest zgodna "Brak" w ciągu źródła. Aby uzyskać więcej informacji na elementy języka wyrażeń regularnych, zobacz [język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> Metoda zwraca niezmienny ciąg z zawartością w <xref:System.Text.StringBuilder> obiektu.

## <a name="modifying-individual-characters"></a>Modyfikowanie znaki

Można utworzyć tablicy znaków z ciągu, modyfikowania zawartości tablicy, a następnie utwórz nowe parametry z zmodyfikowanej zawartości tablicy.

Poniższy przykład pokazuje, jak zastąpić zestaw znaków w ciągu. Po pierwsze, używa <xref:System.String.ToCharArray?displayProperty=nameWithName> metodę w celu utworzenia tablicy znaków. Używa <xref:System.String.IndexOf%2A> metody do znalezienia indeks początkowy wyrazu "fox." Trzech kolejnych znaków są zastępowane innego programu word. Ponadto nowy ciąg jest tworzony z tablicy znaków zaktualizowane.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="unsafe-modifications-to-string"></a>Niebezpieczne modyfikacje na ciąg

Przy użyciu **niebezpieczne** kodu, ciąg "w miejscu" można modyfikować po został utworzony. Niebezpieczny kod pomijany wiele funkcji .NET zaprojektowany w celu zminimalizowania niektórych typów błędów w kodzie. Należy użyć można zmodyfikować ciąg w miejscu, ponieważ klasa ciąg został zaprojektowany jako niebezpieczny kod **niezmienialnych** typu. Po utworzeniu, jego wartość nie ulega zmianie. Niebezpieczny kod obejścia tej właściwości, uzyskiwanie dostępu i modyfikując pamięci używanej przez `string` bez użycia normalne `string` metody.
Poniższy przykład jest dostępna dla tych rzadkich sytuacji, w której chcesz zmodyfikować ciąg w miejscu przy użyciu niebezpieczny kod. W przykładzie pokazano sposób użycia `fixed` — słowo kluczowe. `fixed` — Słowo kluczowe uniemożliwia przenoszenie z obiektem ciągu w pamięci, gdy kod uzyskuje dostęp do pamięci przy użyciu wskaźnika niebezpieczny moduł garbage collector (GC). Ilustruje też jedną możliwe ubocznym niebezpieczne operacje na ciągach będącą wynikiem sposób kompilatora C# wewnętrznie przechowuje ciągi (stażystów). Ogólnie rzecz biorąc nie należy użyć tej metody, chyba że jest bezwzględnie konieczne. Możesz dowiedzieć się więcej informacji, zobacz artykuły na [niebezpieczne](../language-reference/keywords/unsafe.md) i [stałej](../language-reference/keywords/fixed-statement.md). Dokumentacja interfejsu API dla <xref:System.String.Intern%2A> obejmuje inforamtion na interning ciągu.

[!code-csharp-interactive[unsafe ways to create a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Możesz spróbować te przykłady, sprawdzając kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Można również pobrać próbki [jako plik zip](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Zobacz także

[.NET framework — nieprawidłowe wyrażenia](../../standard/base-types/regular-expressions.md)  
 [Język wyrażeń regularnych — podręczny wykaz](../../standard/base-types/regular-expression-language-quick-reference.md)  
