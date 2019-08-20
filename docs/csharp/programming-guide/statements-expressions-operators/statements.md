---
title: Instrukcje — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 4c3421f7165a0b1a3d1c3678fe28334fd8632472
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588629"
---
# <a name="statements-c-programming-guide"></a>Instrukcje (Przewodnik programowania w języku C#)
Akcje podejmowane przez program są wyrażone w instrukcjach. Typowe akcje obejmują deklarowanie zmiennych, przypisywanie wartości, wywoływanie metod, zapętlenie za pomocą kolekcji i rozgałęzianie do jednego lub innego bloku kodu, w zależności od danego warunku. Kolejność, w której instrukcje są wykonywane w programie, nazywa się przepływem sterowania lub przepływu wykonania. Przepływ sterowania może się różnić przy każdym uruchomieniu programu, w zależności od tego, jak program reaguje na dane wejściowe w czasie wykonywania.  
  
 Instrukcja może składać się z jednego wiersza kodu, który jest kończący się średnikiem lub serii instrukcji jednowierszowych w bloku. Blok instrukcji jest ujęty w {} nawiasy klamrowe i może zawierać zagnieżdżone bloki. Poniższy kod przedstawia dwa przykłady instrukcji jednowierszowych i blok instrukcji wielowierszowej:  
  
 [!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]  
  
## <a name="types-of-statements"></a>Typy instrukcji  
 W poniższej tabeli wymieniono różne typy instrukcji w C# i skojarzonych z nimi słowa kluczowe, z linkami do tematów zawierających więcej informacji:  
  
|Kategoria|C#Słowa kluczowe/uwagi|  
|--------------|---------------------------|  
|[Deklaracje deklaracji](#declaration-statements)|Instrukcja deklaracji wprowadza nową zmienną lub stałą. Deklaracja zmiennej może opcjonalnie przypisać wartość do zmiennej. W deklaracji stałej jest wymagane przypisanie.|  
|[Instrukcje wyrażeń](expressions.md)|Instrukcje wyrażenia, które obliczają wartość, muszą przechowywać wartość w zmiennej. Aby uzyskać więcej informacji, zobacz [instrukcje wyrażeń](#expression-statements).|  
|Instrukcje wyboru|Instrukcje wyboru umożliwiają rozgałęzienie z różnymi sekcjami kodu, w zależności od jednego lub większej liczby określonych warunków. Więcej informacji znajduje się w następujących tematach:<br /><br /> [if](../../language-reference/keywords/if-else.md), [else](../../language-reference/keywords/if-else.md), [Switch](../../language-reference/keywords/switch.md), [Case](../../language-reference/keywords/switch.md)|  
|Instrukcje iteracji|Instrukcje iteracji umożliwiają pętlę za pomocą kolekcji, takich jak tablice, lub wielokrotne wykonywanie tego samego zestawu instrukcji do czasu spełnienia określonego warunku. Więcej informacji znajduje się w następujących tematach:<br /><br /> [](../../language-reference/keywords/do.md)do, [dla](../../language-reference/keywords/for.md), [foreach](../../language-reference/keywords/foreach-in.md), [w](../../language-reference/keywords/foreach-in.md), [while](../../language-reference/keywords/while.md)|  
|Instrukcje skoku|Przeskocz kontrolę transferu do innej sekcji kodu. Więcej informacji znajduje się w następujących tematach:<br /><br /> [Break](../../language-reference/keywords/break.md), [Continue](../../language-reference/keywords/continue.md), [default](../../language-reference/keywords/switch.md), [goto](../../language-reference/keywords/goto.md), [Return](../../language-reference/keywords/return.md), [Yield](../../language-reference/keywords/yield.md)|  
|Instrukcje obsługi wyjątków|Instrukcje obsługi wyjątków umożliwiają bezpieczne odzyskiwanie z wyjątkowych warunków występujących w czasie wykonywania. Więcej informacji znajduje się w następujących tematach:<br /><br /> [throw](../../language-reference/keywords/throw.md), [try-catch](../../language-reference/keywords/try-catch.md), [try-finally](../../language-reference/keywords/try-finally.md), [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)|  
|[Zaznaczone i niezaznaczone](../../language-reference/keywords/checked-and-unchecked.md)|Instrukcje sprawdzone i niesprawdzone umożliwiają określenie, czy operacje numeryczne mogą spowodować przepełnienie, gdy wynik jest przechowywany w zmiennej, która jest zbyt mała, aby pomieścić wynikową wartość. Aby uzyskać więcej informacji, zobacz [zaznaczone](../../language-reference/keywords/checked.md) i [niezaznaczone](../../language-reference/keywords/unchecked.md).|  
|`await` Instrukcja|Jeśli oznaczesz metodę za pomocą modyfikatora [asynchronicznego](../../language-reference/keywords/async.md) , możesz użyć operatora [await](../../language-reference/keywords/await.md) w metodzie. Gdy kontrolka osiągnie `await` wyrażenie w metodzie asynchronicznej, sterowanie powraca do obiektu wywołującego, a postęp w metodzie jest zawieszony do momentu zakończenia zadania oczekiwania. Po zakończeniu zadania wykonywanie może zostać wznowione w metodzie.<br /><br /> Aby zapoznać się z prostym przykładem, zobacz sekcję "metody asynchroniczne" w temacie [metody](../classes-and-structs/methods.md). Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i await](../concepts/async/index.md).|  
|`yield return` Instrukcja|Iterator wykonuje niestandardową iterację w kolekcji, na przykład listę lub tablicę. Iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz. Po osiągnięciu `yield return` instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji, kiedy iterator jest wywoływana następnym razem.<br /><br /> Aby uzyskać więcej informacji, [](../concepts/iterators.md)zobacz Iteratory.|  
|`fixed` Instrukcja|Stała instrukcja uniemożliwia ponowne lokalizowanie ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [FIXED](../../language-reference/keywords/fixed-statement.md).|  
|`lock` Instrukcja|Instrukcja lock umożliwia ograniczenie dostępu do bloków kodu tylko do jednego wątku naraz. Aby uzyskać więcej informacji, zobacz [Blokada](../../language-reference/keywords/lock-statement.md).|  
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

 Niektóre instrukcje, w [](../../language-reference/keywords/do.md)tym do, [while](../../language-reference/keywords/while.md), [for](../../language-reference/keywords/for.md)i [foreach](../../language-reference/keywords/foreach-in.md), zawsze mają osadzoną instrukcję, która następuje po nich. Ta osadzona instrukcja może być pojedynczą instrukcją lub wieloma instrukcją {} ujętą w nawiasy kwadratowe bloku instrukcji. Nawet osadzone instrukcje jednowierszowe mogą być ujęte {} w nawiasy, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]  
  
 Osadzona instrukcja, która nie jest ujęta w {} nawiasy kwadratowe nie może być instrukcją deklaracji ani instrukcją etykiety. Jest to pokazane w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]  
  
 Umieść osadzoną instrukcję w bloku, aby naprawić błąd:  
  
 [!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]  
  
## <a name="nested-statement-blocks"></a>Zagnieżdżone bloki instrukcji  
 Bloki instrukcji mogą być zagnieżdżane, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]  
  
## <a name="unreachable-statements"></a>Nieosiągalne instrukcje  
 Jeśli kompilator określi, że przepływ sterowania nigdy nie dociera do konkretnej instrukcji w jakichkolwiek okolicznościach, spowoduje to wygenerowanie ostrzeżenia CS0162, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Słowa kluczowe instrukcji](../../language-reference/keywords/statement-keywords.md)  
  
- [Wyrażenia](./expressions.md)  
  
- [Operatory](./operators.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
