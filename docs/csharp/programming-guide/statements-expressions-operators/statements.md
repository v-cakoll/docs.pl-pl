---
title: Instrukcje (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 68f7f799ebbfe52c99820083eb22761c79f66483
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statements-c-programming-guide"></a>Instrukcje (Przewodnik programowania w języku C#)
Akcje, które przyjmuje programu są wyrażane w instrukcjach. Typowe akcje obejmują deklarowania zmiennych, przypisywanie wartości, wywołanie metody zapętlenie przez kolekcje i rozgałęziania do jednej lub drugiej bloku kodu, w zależności od dany warunek. Kolejność wykonywania instrukcji w programie nosi nazwę przepływu sterowania lub przepływ wykonania. Przepływ sterowania mogą różnić się zawsze uruchamiany program, w zależności od tego, jak program reaguje na dane wejściowe odbiór w czasie wykonywania.  
  
 Instrukcja może zawierać pojedynczy wiersz kodu, który kończy się średnikiem lub serii jednowierszowe instrukcje w bloku. Blok instrukcji jest ujęta w {} nawiasy i mogą zawierać zagnieżdżonych bloków. Poniższy kod przedstawia dwa przykłady jednowierszowe instrukcje i blok instrukcji wiele wierszy:  
  
 [!code-csharp[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Typy instrukcji  
 W poniższej tabeli wymieniono różne rodzaje instrukcje w C# i ich skojarzonych słów kluczowych, linki do tematów, które zawierają więcej informacji:  
  
|Kategoria|Słowa kluczowe języka C# / uwagi|  
|--------------|---------------------------|  
|Instrukcje deklaracji|Instrukcja deklaracji wprowadza nową zmienną lub stałą. Deklaracja zmiennej można opcjonalnie przypisać wartości do zmiennej. W deklaracji stałej przypisanie nie jest wymagana.<br /><br /> [!code-csharp[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|Instrukcje wyrażeń|Instrukcje wyrażeń, które obliczyć wartość wartości muszą być przechowywane w zmiennej.<br /><br /> [!code-csharp[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[Zaznaczenie — instrukcje](../../../csharp/language-reference/keywords/selection-statements.md)|Zaznaczenie — instrukcje umożliwiają gałęzi do różnych fragmentów kodu, w zależności od tego, co najmniej jednego określonego warunku. Więcej informacji znajduje się w następujących tematach:<br /><br /> [Jeśli](../../../csharp/language-reference/keywords/if-else.md), [else](../../../csharp/language-reference/keywords/if-else.md), [przełącznika](../../../csharp/language-reference/keywords/switch.md), [case](../../../csharp/language-reference/keywords/switch.md)|  
|[Iteracja — instrukcje](../../../csharp/language-reference/keywords/iteration-statements.md)|Iteracja — instrukcje umożliwiają za pomocą kolekcji, takie jak tablic w pętli lub wielokrotnie wykonać ten sam zestaw instrukcji, dopóki nie zostanie spełniony określony warunek. Więcej informacji znajduje się w następujących tematach:<br /><br /> [czy](../../../csharp/language-reference/keywords/do.md), [dla](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [w](../../../csharp/language-reference/keywords/foreach-in.md), [podczas](../../../csharp/language-reference/keywords/while.md)|  
|[Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)|Przejście instrukcje transfer kontroli do innej sekcji kodu. Więcej informacji znajduje się w następujących tematach:<br /><br /> [podział](../../../csharp/language-reference/keywords/break.md), [kontynuować](../../../csharp/language-reference/keywords/continue.md), [domyślne](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Instrukcje obsługi wyjątków](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Instrukcje obsługi wyjątków umożliwiają bezpieczne odzyskiwanie w wyjątkowych warunków, które występują w czasie wykonywania. Więcej informacji znajduje się w następujących tematach:<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Zaznaczony i niezaznaczony](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Zaznaczone i niezaznaczone instrukcje umożliwiają określenie, czy operacje numeryczne mogą powodować przepełnienia, gdy wynik jest przechowywana w zmiennej, która jest zbyt mały, aby pomieścić wynikowej wartości. Aby uzyskać więcej informacji, zobacz [zaznaczone](../../../csharp/language-reference/keywords/checked.md) i [niezaznaczone](../../../csharp/language-reference/keywords/unchecked.md).|  
|`await` — Instrukcja|Po zaznaczeniu metodę o [async](../../../csharp/language-reference/keywords/async.md) modyfikator, można użyć [await](../../../csharp/language-reference/keywords/await.md) operatora w metodzie. Gdy kontrolować osiągnie `await` wyrażenie w metodzie asynchronicznej, zwraca sterowania do obiektu wywołującego i postępu w metodzie jest wstrzymana, aż do zakończenia zadań oczekiwano. Po zakończeniu zadania wykonywania można wznowić w metodzie.<br /><br /> Na przykład prosty, zobacz sekcję "Metod asynchronicznych" [metody](../../../csharp/programming-guide/classes-and-structs/methods.md). Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md).|  
|`yield return` — Instrukcja|Iteratora wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element jednym naraz. Gdy `yield return` osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie. Wykonanie zostanie ponownie z tej lokalizacji, gdy iteratora jest wywoływana przy następnym.<br /><br /> Aby uzyskać więcej informacji, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).|  
|`fixed` — Instrukcja|Fixed — instrukcja uniemożliwia przemieszczanie zmienną ruchomy moduł garbage collector. Aby uzyskać więcej informacji, zobacz [stałej](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|`lock` — Instrukcja|Blokada — instrukcja pozwala ograniczyć dostęp do bloki kodu, aby tylko jeden wątek na raz. Aby uzyskać więcej informacji, zobacz [blokady](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Labeled — instrukcje|Można podać instrukcję etykietę, a następnie użyć [goto](../../../csharp/language-reference/keywords/goto.md) — słowo kluczowe, aby przejść do etykietą instrukcji. (Zobacz przykład w następującym wierszem).|  
|Pusta instrukcja|Pusta instrukcja składa się z jednego średnikami. Nic nie i mogą być używane w miejscach, gdzie instrukcji jest wymagany, ale musi zostać wykonana żadna akcja. W poniższych przykładach pokazano dwa zastosowania pustą instrukcję:<br /><br /> [!code-csharp[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## <a name="embedded-statements"></a>Instrukcje osadzonych  
 Niektóre instrukcje w tym [czy](../../../csharp/language-reference/keywords/do.md), [podczas](../../../csharp/language-reference/keywords/while.md), [dla](../../../csharp/language-reference/keywords/for.md), i [foreach](../../../csharp/language-reference/keywords/foreach-in.md), zawsze mieć osadzona instrukcja je poniżej. To osadzona instrukcja może być pojedyncza instrukcja lub użycie wielu instrukcji ujęty w {} nawiasów kwadratowych w bloku instrukcji. Nawet jednowierszowe instrukcje osadzonych mogą być ujęte w {} nawiasy, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 Osadzona instrukcja, która nie jest zawarta w {} nawiasy kwadratowe nie może być etykietą instrukcji lub instrukcji deklaracji. Przedstawiono to w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 W bloku, aby naprawić błąd, należy umieścić osadzona instrukcja:  
  
 [!code-csharp[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>Zagnieżdżona instrukcja bloków  
 Może być zagnieżdżone bloki instrukcji, jak pokazano w poniższym kodzie:  
  
 [!code-csharp[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Nieosiągalny — instrukcje  
 Kompilator Określa, że przepływu sterowania nigdy nie może nawiązać połączenie określonej instrukcji w żadnym, powoduje wygenerowanie ostrzeżenia CS0162, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
-   [Słowa kluczowe instrukcji](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [Wyrażenia](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
