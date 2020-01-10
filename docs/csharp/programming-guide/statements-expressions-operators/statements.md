---
title: Instrukcje — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: d50b50bb291d0d087015ea5bd075ae90ced66ff5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711938"
---
# <a name="statements-c-programming-guide"></a>Instrukcje (Przewodnik programowania w języku C#)

Akcje podejmowane przez program są wyrażone w instrukcjach. Typowe akcje obejmują deklarowanie zmiennych, przypisywanie wartości, wywoływanie metod, zapętlenie za pomocą kolekcji i rozgałęzianie do jednego lub innego bloku kodu, w zależności od danego warunku. Kolejność, w której instrukcje są wykonywane w programie, nazywa się przepływem sterowania lub przepływu wykonania. Przepływ sterowania może się różnić przy każdym uruchomieniu programu, w zależności od tego, jak program reaguje na dane wejściowe w czasie wykonywania.

Instrukcja może składać się z jednego wiersza kodu, który jest kończący się średnikiem lub serii instrukcji jednowierszowych w bloku. Blok instrukcji jest ujęty w nawiasy {} i może zawierać zagnieżdżonych bloków. Poniższy kod przedstawia dwa przykłady instrukcji jednowierszowych i blok instrukcji wielowierszowej:

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>Typy instrukcji

W poniższej tabeli wymieniono różne typy instrukcji w C# i skojarzonych z nimi słowa kluczowe, z linkami do tematów zawierających więcej informacji:

|Kategoria|C#Słowa kluczowe/uwagi|
|--------------|---------------------------|
|[Deklaracje deklaracji](#declaration-statements)|Instrukcja deklaracji wprowadza nową zmienną lub stałą. Deklaracja zmiennej może opcjonalnie przypisać wartość do zmiennej. W deklaracji stałej jest wymagane przypisanie.|
|[Instrukcje wyrażeń](expressions.md)|Instrukcje wyrażenia, które obliczają wartość, muszą przechowywać wartość w zmiennej. Aby uzyskać więcej informacji, zobacz [instrukcje wyrażeń](#expression-statements).|
|Instrukcje wyboru|Instrukcje wyboru umożliwiają rozgałęzienie z różnymi sekcjami kodu, w zależności od jednego lub większej liczby określonych warunków. Więcej informacji znajduje się w następujących tematach: <ul><li>[if](../../language-reference/keywords/if-else.md)</li><li>[Przejmi](../../language-reference/keywords/if-else.md)</li><li>[switch](../../language-reference/keywords/switch.md)</li><li>[case](../../language-reference/keywords/switch.md)</li></ul>|
|Instrukcje iteracji|Instrukcje iteracji umożliwiają pętlę za pomocą kolekcji, takich jak tablice, lub wielokrotne wykonywanie tego samego zestawu instrukcji do czasu spełnienia określonego warunku. Więcej informacji znajduje się w następujących tematach: <ul><li>[do](../../language-reference/keywords/do.md)</li><li>[for](../../language-reference/keywords/for.md)</li><li>[spowodował](../../language-reference/keywords/foreach-in.md)</li><li>[in](../../language-reference/keywords/foreach-in.md)</li><li>[while](../../language-reference/keywords/while.md)</li></ul>|
|Instrukcje skoku|Przeskocz kontrolę transferu do innej sekcji kodu. Więcej informacji znajduje się w następujących tematach: <ul><li>[break](../../language-reference/keywords/break.md)</li><li>[continue](../../language-reference/keywords/continue.md)</li><li>[default](../../language-reference/keywords/switch.md)</li><li>[goto](../../language-reference/keywords/goto.md)</li><li>[return](../../language-reference/keywords/return.md)</li><li>[yield](../../language-reference/keywords/yield.md)</li></ul>|
|Instrukcje obsługi wyjątków|Instrukcje obsługi wyjątków umożliwiają bezpieczne odzyskiwanie z wyjątkowych warunków występujących w czasie wykonywania. Więcej informacji znajduje się w następujących tematach: <ul><li>[throw](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Zaznaczone i niezaznaczone](../../language-reference/keywords/checked-and-unchecked.md)|Instrukcje sprawdzone i niesprawdzone umożliwiają określenie, czy operacje numeryczne mogą spowodować przepełnienie, gdy wynik jest przechowywany w zmiennej, która jest zbyt mała, aby pomieścić wynikową wartość. Aby uzyskać więcej informacji, zobacz [zaznaczone](../../language-reference/keywords/checked.md) i [niezaznaczone](../../language-reference/keywords/unchecked.md).|
|Instrukcja `await`|Jeśli oznaczesz metodę za pomocą modyfikatora [asynchronicznego](../../language-reference/keywords/async.md) , możesz użyć operatora [await](../../language-reference/operators/await.md) w metodzie. Gdy kontrolka osiągnie wyrażenie `await` w metodzie asynchronicznej, sterowanie powraca do obiektu wywołującego, a postęp w metodzie jest zawieszony do momentu zakończenia zadania oczekiwania. Po zakończeniu zadania wykonywanie może zostać wznowione w metodzie.<br /><br /> Aby zapoznać się z prostym przykładem, zobacz sekcję "metody asynchroniczne" w temacie [metody](../classes-and-structs/methods.md). Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i await](../concepts/async/index.md).|
|Instrukcja `yield return`|Iterator wykonuje niestandardową iterację w kolekcji, na przykład listę lub tablicę. Iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz. Po osiągnięciu instrukcji `yield return` bieżąca lokalizacja w kodzie jest zapamiętywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji, kiedy iterator jest wywoływana następnym razem.<br /><br /> Aby uzyskać więcej informacji, zobacz [Iteratory](../concepts/iterators.md).|
|Instrukcja `fixed`|Stała instrukcja uniemożliwia ponowne lokalizowanie ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [FIXED](../../language-reference/keywords/fixed-statement.md).|
|Instrukcja `lock`|Instrukcja lock umożliwia ograniczenie dostępu do bloków kodu tylko do jednego wątku naraz. Aby uzyskać więcej informacji, zobacz [Blokada](../../language-reference/keywords/lock-statement.md).|
|Instrukcje oznaczone|Możesz nadać instrukcji etykietę, a następnie użyć słowa kluczowego [goto](../../language-reference/keywords/goto.md) , aby przejść do instrukcji oznaczonej etykietą. (Zobacz przykład w następującym wierszu).|
|[Pusta instrukcja](#the-empty-statement)|Pusta instrukcja składa się z pojedynczego średnika. Nic nie robi i może być używane w miejscach, w których instrukcja jest wymagana, ale nie trzeba wykonywać żadnych czynności.|

## <a name="declaration-statements"></a>Deklaracje deklaracji

Poniższy kod przedstawia przykłady deklaracji zmiennych z przypisaniem wstępnym i bez niego oraz stałą deklarację z wymaganą inicjalizacją.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>Instrukcje wyrażeń

Poniższy kod przedstawia przykłady instrukcji wyrażeń, w tym przypisanie, tworzenie obiektów z przypisaniem i wywoływanie metody.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Pusta instrukcja

W poniższych przykładach przedstawiono dwa zastosowania dla pustej instrukcji:

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Osadzone instrukcje

Niektóre instrukcje, w [tym do,](../../language-reference/keywords/do.md) [while](../../language-reference/keywords/while.md), [for](../../language-reference/keywords/for.md)i [foreach](../../language-reference/keywords/foreach-in.md), zawsze mają osadzoną instrukcję, która następuje po nich. Ta osadzona instrukcja może być pojedynczą instrukcją lub wieloma instrukcjami zawartymi w nawiasach {} w bloku instrukcji. Nawet osadzone instrukcje jednowierszowe mogą być ujęte w nawiasy {}, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Osadzona instrukcja, która nie jest ujęta w nawiasy {} nie może być instrukcją deklaracji ani instrukcją etykiety. Jest to pokazane w poniższym przykładzie:

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Umieść osadzoną instrukcję w bloku, aby naprawić błąd:

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>Zagnieżdżone bloki instrukcji

Bloki instrukcji mogą być zagnieżdżane, jak pokazano w poniższym kodzie:

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Nieosiągalne instrukcje

Jeśli kompilator określi, że przepływ sterowania nigdy nie dociera do konkretnej instrukcji w jakichkolwiek okolicznościach, spowoduje to wygenerowanie ostrzeżenia CS0162, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcje](~/_csharplang/spec/statements.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Słowa kluczowe instrukcji](../../language-reference/keywords/statement-keywords.md)  
- [Wyrażenia](expressions.md)  
