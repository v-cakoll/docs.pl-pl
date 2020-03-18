---
title: Instrukcje — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: d50b50bb291d0d087015ea5bd075ae90ced66ff5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711938"
---
# <a name="statements-c-programming-guide"></a>Instrukcje (Przewodnik programowania w języku C#)

Akcje podejmowane przez program są wyrażane w instrukcjach. Typowe akcje obejmują deklarowanie zmiennych, przypisywanie wartości, wywoływanie metod, zapętlanie kolekcji i rozgałęzianie do jednego lub innego bloku kodu, w zależności od danego warunku. Kolejność, w której instrukcje są wykonywane w programie jest nazywany przepływ kontroli lub przepływu wykonywania. Przepływ sterowania może się różnić za każdym razem, gdy program jest uruchamiany, w zależności od tego, jak program reaguje na dane wejściowe, które odbiera w czasie wykonywania.

Instrukcja może składać się z jednego wiersza kodu, który kończy się średnikiem lub serii instrukcji jednowierszowych w bloku. Blok instrukcji jest ujęty w {} nawiasy i może zawierać bloki zagnieżdżone. Poniższy kod przedstawia dwa przykłady instrukcji jednowierszowych i wielowierszowy blok instrukcji:

[!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]

## <a name="types-of-statements"></a>Rodzaje zestawienia

W poniższej tabeli wymieniono różne typy instrukcji w języku C# i powiązane z nimi słowa kluczowe z łączami do tematów, które zawierają więcej informacji:

|Kategoria|Słowa kluczowe /notatki języka C#|
|--------------|---------------------------|
|[Deklaracje deklaracji](#declaration-statements)|Deklaracja instrukcji wprowadza nową zmienną lub stałą. Deklaracja zmiennej może opcjonalnie przypisać wartość do zmiennej. W deklaracji stałej wymagane jest przypisanie.|
|[Instrukcje wyrażeń](expressions.md)|Instrukcje wyrażenia, które obliczają wartość, muszą przechowywać wartość w zmiennej. Aby uzyskać więcej informacji, zobacz [Instrukcje wyrażeń](#expression-statements).|
|Instrukcje wyboru|Instrukcje wyboru umożliwiają rozgałęzianie się do różnych sekcji kodu, w zależności od jednego lub więcej określonych warunków. Aby uzyskać więcej informacji, zobacz następujące tematy: <ul><li>[Jeśli](../../language-reference/keywords/if-else.md)</li><li>[Innego](../../language-reference/keywords/if-else.md)</li><li>[Przełącznik](../../language-reference/keywords/switch.md)</li><li>[Przypadku](../../language-reference/keywords/switch.md)</li></ul>|
|Instrukcje iteracji|Instrukcje iteracji umożliwiają przechodzenie za pośrednictwem kolekcji, takich jak tablice, lub wielokrotne wykonywanie tego samego zestawu instrukcji, dopóki nie zostanie spełniony określony warunek. Aby uzyskać więcej informacji, zobacz następujące tematy: <ul><li>[Zrobić](../../language-reference/keywords/do.md)</li><li>[for](../../language-reference/keywords/for.md)</li><li>[Foreach](../../language-reference/keywords/foreach-in.md)</li><li>[Cala](../../language-reference/keywords/foreach-in.md)</li><li>[Podczas](../../language-reference/keywords/while.md)</li></ul>|
|Instrukcje skoku|Instrukcje przeskoku transferu kontroli do innej sekcji kodu. Aby uzyskać więcej informacji, zobacz następujące tematy: <ul><li>[Przerwy](../../language-reference/keywords/break.md)</li><li>[Kontynuować](../../language-reference/keywords/continue.md)</li><li>[Domyślny](../../language-reference/keywords/switch.md)</li><li>[Goto](../../language-reference/keywords/goto.md)</li><li>[return](../../language-reference/keywords/return.md)</li><li>[yield](../../language-reference/keywords/yield.md)</li></ul>|
|Instrukcje obsługi wyjątków|Instrukcje obsługi wyjątków umożliwiają bezpiecznie odzyskać z wyjątkowych warunków, które występują w czasie wykonywania. Aby uzyskać więcej informacji, zobacz następujące tematy: <ul><li>[throw](../../language-reference/keywords/throw.md)</li><li>[try-catch](../../language-reference/keywords/try-catch.md)</li><li>[try-finally](../../language-reference/keywords/try-finally.md)</li><li>[try-catch-finally](../../language-reference/keywords/try-catch-finally.md)</li></ul>|
|[Sprawdzone i niezaznaczone](../../language-reference/keywords/checked-and-unchecked.md)|Instrukcje zaznaczone i niezaznaczone umożliwiają określenie, czy operacje liczbowe mogą powodować przepełnienie, gdy wynik jest przechowywany w zmiennej, która jest zbyt mała, aby pomieścić wynikową wartość. Aby uzyskać więcej informacji, zobacz [sprawdzone](../../language-reference/keywords/checked.md) i [niezaznaczone](../../language-reference/keywords/unchecked.md).|
|Oświadczenie `await`|Jeśli oznaczysz metodę modyfikatorem [asynchroni,](../../language-reference/keywords/async.md) możesz użyć [operatora await](../../language-reference/operators/await.md) w metodzie. Gdy formant osiągnie `await` wyrażenie w metodzie asynchronicznej, formant powraca do obiektu wywołującego, a postęp w metodzie jest zawieszony, dopóki nie zostanie ukończone oczekiwane zadanie. Po zakończeniu zadania wykonanie można wznowić w metodzie.<br /><br /> Aby uzyskać prosty przykład, zobacz sekcję Metody asynchronicznej [metody](../classes-and-structs/methods.md). Aby uzyskać więcej informacji, zobacz [Programowanie asynchroniczne z async i czekam .](../concepts/async/index.md)|
|Oświadczenie `yield return`|Iterator wykonuje iterację niestandardową nad kolekcją, taką jak lista lub tablica. Iterator używa [yield return](../../language-reference/keywords/yield.md) instrukcji do zwrócenia każdego elementu po jednym na raz. Po `yield return` osiągnięciu instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji, gdy sterująca jest wywoływana następnym razem.<br /><br /> Aby uzyskać więcej informacji, zobacz [Iterytory](../concepts/iterators.md).|
|Oświadczenie `fixed`|Stała instrukcja uniemożliwia modułowi odśmiecania pamięci przemieszczanie ruchomej zmiennej. Aby uzyskać więcej informacji, zobacz [stałe](../../language-reference/keywords/fixed-statement.md).|
|Oświadczenie `lock`|Lock Instrukcji umożliwia ograniczenie dostępu do bloków kodu tylko jeden wątek naraz. Aby uzyskać więcej informacji, zobacz [blokada](../../language-reference/keywords/lock-statement.md).|
|Instrukcje oznaczone|Możesz nadać instrukcji etykietę, a następnie użyć słowa kluczowego [goto,](../../language-reference/keywords/goto.md) aby przejść do instrukcji oznaczonej etykietą. (Zobacz przykład w następnym wierszu).|
|[Pusta instrukcja](#the-empty-statement)|Pusta instrukcja składa się z pojedynczego średnika. Nie robi nic i może być używany w miejscach, gdzie instrukcja jest wymagana, ale nie trzeba wykonywać żadnych działań.|

## <a name="declaration-statements"></a>Deklaracje deklaracji

Poniższy kod przedstawia przykłady deklaracji zmiennych z i bez przypisania początkowego i stałej deklaracji z niezbędną inicjalizacją.

[!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>Instrukcje wyrażeń

Poniższy kod przedstawia przykłady instrukcji wyrażeń, w tym przypisania, tworzenia obiektu z przypisaniem i wywołanie metody.

[!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Pusta instrukcja

W poniższych przykładach przedstawiono dwa zastosowania pustej instrukcji:

[!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Instrukcje osadzone

Niektóre oświadczenia, w tym [zrobić](../../language-reference/keywords/do.md), [podczas gdy](../../language-reference/keywords/while.md), [dla](../../language-reference/keywords/for.md), i [foreach](../../language-reference/keywords/foreach-in.md), zawsze mają osadzone oświadczenie, które następuje po nich. Ta osadzona instrukcja może być pojedynczą {} instrukcją lub wieloma instrukcjami ujętymi w nawiasy w bloku instrukcji. Nawet jednowierszowe instrukcje osadzone {} mogą być ujęte w nawiasy, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]

Osadzona instrukcja, która {} nie jest ujęta w nawiasy, nie może być instrukcją deklaracji ani instrukcją z etykietą. Jest to pokazane w poniższym przykładzie:

[!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]

Umieść osadzoną instrukcję w bloku, aby naprawić błąd:

[!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]

## <a name="nested-statement-blocks"></a>Bloki zagnieżdżonych instrukcji

Bloki instrukcji mogą być zagnieżdżone, jak pokazano w następującym kodzie:

[!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]

## <a name="unreachable-statements"></a>Nieosiągalne stwierdzenia

Jeśli kompilator stwierdzi, że przepływ kontroli nigdy nie może osiągnąć określonego instrukcji w żadnych okolicznościach, spowoduje wyświetlenie ostrzeżenia CS0162, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [instrukcje](~/_csharplang/spec/statements.md) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Słowa kluczowe oświadczenie](../../language-reference/keywords/statement-keywords.md)  
- [Wyrażenia](expressions.md)  
