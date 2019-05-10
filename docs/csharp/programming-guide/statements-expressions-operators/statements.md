---
title: Instrukcje — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 6dcf5a69be7817351a9e250506ba51471918a772
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608136"
---
# <a name="statements-c-programming-guide"></a>Instrukcje (Przewodnik programowania w języku C#)
Akcje, które przyjmuje programu są wyrażane w instrukcjach. Typowe akcje obejmują zadeklarowania zmiennych, przypisywania wartości, wywoływanie metod, zapętlenie przez kolekcje i gałęzi do jednej lub drugiej bloku kodu, w zależności od danego warunku. Kolejność, w którym wykonywane są instrukcje w programie nosi nazwę przepływu sterowania lub przepływem wykonania. Przepływ sterowania, mogą się różnić w każdym uruchomieniu programu, w zależności od tego, jak program reaguje na dane wejściowe, że będzie ona otrzymywać w czasie wykonywania.  
  
 Użycie instrukcji może składać się z jednego wiersza kodu, który kończy się średnikiem lub serię instrukcji jeden wiersz w bloku. Blok instrukcji jest ujęty w {} nawiasy kwadratowe i mogą zawierać zagnieżdżonych bloków. Poniższy kod pokazuje dwa przykłady instrukcji jeden wiersz i blok instrukcji wielowierszowe:  
  
 [!code-csharp[csProgGuideStatements#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#1)]  
  
## <a name="types-of-statements"></a>Typów instrukcji  
 W poniższej tabeli wymieniono różne rodzaje instrukcji w języku C# i ich skojarzone słów kluczowych, za pomocą łącza do tematów, które zawierają więcej informacji:  
  
|Kategoria|Słowa kluczowe języka C# / informacje o|  
|--------------|---------------------------|  
|[Instrukcje deklaracji](#declaration-statements)|Instrukcji deklaracji wprowadza nową zmienną lub stałą. Deklaracja zmiennej, można opcjonalnie przypisać wartość do zmiennej. W deklaracji stałej przydziału jest wymagana.|  
|[Instrukcje wyrażeń](expressions.md)|Instrukcje wyrażeń, które obliczają wartość wartości muszą być przechowywane w zmiennej. Aby uzyskać więcej informacji, zobacz [instrukcje wyrażeń](#expression-statements).|  
|[Instrukcje wyboru](../../../csharp/language-reference/keywords/selection-statements.md)|Instrukcje wyboru umożliwiają gałęzi do różnych sekcji kodu, w zależności od tego, co najmniej jeden określony warunek. Więcej informacji znajduje się w następujących tematach:<br /><br /> [Jeśli](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [Przełącz](../../../csharp/language-reference/keywords/switch.md), [case](../../../csharp/language-reference/keywords/switch.md)|  
|[Instrukcje iteracji](../../../csharp/language-reference/keywords/iteration-statements.md)|Iteracja — instrukcje umożliwiają jednoczesne kolekcji, takich jak tablice lub wykonać ten sam zestaw instrukcji wielokrotnie do momentu spełnienia określonego warunku. Więcej informacji znajduje się w następujących tematach:<br /><br /> [czy](../../../csharp/language-reference/keywords/do.md), [dla](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [w](../../../csharp/language-reference/keywords/foreach-in.md), [podczas](../../../csharp/language-reference/keywords/while.md)|  
|[Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)|Szybkie instrukcji transfer kontroli do innej części kodu. Więcej informacji znajduje się w następujących tematach:<br /><br /> [podział](../../../csharp/language-reference/keywords/break.md), [nadal](../../../csharp/language-reference/keywords/continue.md), [domyślne](../../../csharp/language-reference/keywords/switch.md), [przejdź do](../../../csharp/language-reference/keywords/goto.md), [zwracają](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Instrukcje obsługi wyjątków](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Instrukcje obsługi wyjątków umożliwia bezpieczne odzyskiwanie w wyjątkowych warunków, które występują w czasie wykonywania. Więcej informacji znajduje się w następujących tematach:<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch —](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked i unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Zaznaczone i niezaznaczone instrukcje umożliwiają określenie, czy wartości liczbowych operacji może spowodować przepełnienie, gdy wynik jest przechowywany w zmiennej, która jest zbyt mała do przechowywania wartości wynikowej. Aby uzyskać więcej informacji, zobacz [zaznaczone](../../../csharp/language-reference/keywords/checked.md) i [unchecked](../../../csharp/language-reference/keywords/unchecked.md).|  
|`await` — Instrukcja|Po oznaczeniu metody z [async](../../../csharp/language-reference/keywords/async.md) modyfikator, można użyć [await](../../../csharp/language-reference/keywords/await.md) operatora w metodzie. Gdy kontrola osiąga `await` wyrażenia w metodzie asynchronicznej, sterowanie powraca do obiektu wywołującego, a postęp w metodzie jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie. Kiedy zadanie zostanie ukończone, wykonanie można wznowić w metodzie.<br /><br /> Dla prostego przykładu, zobacz sekcję "Metod asynchronicznych" [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md).|  
|`yield return` — Instrukcja|Iterator wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcja zwraca każdy element w danym momencie. Gdy `yield return` osiągnięciu instrukcji zapamiętanych bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji, gdy iteratora jest wywoływana przy następnym.<br /><br /> Aby uzyskać więcej informacji, zobacz [Iteratory](../../../csharp/programming-guide/concepts/iterators.md).|  
|`fixed` — Instrukcja|Fixed — instrukcja zapobiega przemieszczanie zmienną ruchome moduł odśmiecania pamięci. Aby uzyskać więcej informacji, zobacz [stałej](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|`lock` — Instrukcja|Instrukcji "lock" można ograniczyć dostęp do bloków kodu, aby tylko jeden wątek jednocześnie. Aby uzyskać więcej informacji, zobacz [blokady](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Labeled — instrukcje|Możesz nadać instrukcję etykietę, a następnie użyć [goto](../../../csharp/language-reference/keywords/goto.md) — słowo kluczowe, aby przejść do instrukcja labeled. (Zobacz przykład w poniższym wierszu).|  
|[Pusta instrukcja](#the-empty-statement)|Pusta instrukcja składa się z pojedynczego średnikami. On nic nie robi i mogą być używane w miejscach, w której instrukcję jest wymagany, ale musi zostać wykonana żadna akcja.|  
  
## <a name="declaration-statements"></a>Instrukcje deklaracji

Poniższy kod przedstawia przykłady deklaracji zmiennych z lub bez początkowego przydziału i deklaracji stałej z inicjalizacją niezbędne.

 [!code-csharp[csProgGuideStatements#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#23)]

## <a name="expression-statements"></a>Instrukcje wyrażeń

Poniższy kod przedstawia przykładowe instrukcje wyrażeń, łącznie z przypisania, utworzenie obiektu za pomocą przydziałów i wywołanie metody.

 [!code-csharp[csProgGuideStatements#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#24)]

## <a name="the-empty-statement"></a>Pusta instrukcja

W poniższych przykładach pokazano dwa zastosowania pustą instrukcję:

 [!code-csharp[csProgGuideStatements#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#25)]

## <a name="embedded-statements"></a>Osadzone instrukcje

 Niektóre instrukcje, w tym [czy](../../../csharp/language-reference/keywords/do.md), [podczas](../../../csharp/language-reference/keywords/while.md), [dla](../../../csharp/language-reference/keywords/for.md), i [foreach](../../../csharp/language-reference/keywords/foreach-in.md), zawsze mają osadzona instrukcja, który następuje po nich. To osadzona instrukcja może być pojedynczą instrukcję lub wiele instrukcji ujęta w {} nawiasów kwadratowych w bloku instrukcji. Osadzone instrukcje nawet jednego wiersza mogą być ujęte w {} nawiasy kwadratowe, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#26)]  
  
 Osadzona instrukcja, która nie jest ujęty w {} nawiasy kwadratowe nie może być instrukcji deklaracji lub instrukcji oznaczonej etykietą. Jest to pokazane w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#27)]  
  
 W bloku, aby naprawić błąd, należy umieścić osadzona instrukcja:  
  
 [!code-csharp[csProgGuideStatements#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#28)]  
  
## <a name="nested-statement-blocks"></a>Zagnieżdżona instrukcja bloków  
 Może być zagnieżdżony bloków instrukcji, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[csProgGuideStatements#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#29)]  
  
## <a name="unreachable-statements"></a>Instrukcji jest nieosiągalny  
 Kompilator Określa, że przepływ sterowania nigdy nie może osiągnąć określonej instrukcji w żadnym, powoduje wygenerowanie ostrzeżenia CS0162, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#22)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
- [Słowa kluczowe instrukcji](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
- [Wyrażenia](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
- [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
