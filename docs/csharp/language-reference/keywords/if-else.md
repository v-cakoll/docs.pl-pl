---
title: "if-else (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a0ecc915af00caffeba92a8308a60bc24198d477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="if-else-c-reference"></a>if-else (odwołanie w C#)
`if` Identyfikuje instrukcji, które instrukcji do uruchomienia na podstawie wartości z `Boolean` wyrażenia. W poniższym przykładzie `Boolean` zmiennej `result` ustawiono `true` , a następnie zaewidencjonowany `if` instrukcji. Dane wyjściowe `The condition is true`.  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 Przykłady można uruchomić w tym temacie, umieszczając je w `Main` metoda aplikacji konsoli.  
  
 `if` Instrukcji w języku C# może zająć dwie formy, jak przedstawiono na poniższym przykładzie.  
  
```csharp  
// if-else statement  
if (condition)  
{  
    then-statement;  
}  
else  
{  
    else-statement;  
}  
// Next statement in the program.  
  
// if statement without an else  
if (condition)  
{  
    then-statement;  
}  
// Next statement in the program.  
```  
  
 W `if-else` instrukcji, jeśli `condition` zwraca wartość true, `then-statement` działa. Jeśli `condition` ma wartość false, `else-statement` działa. Ponieważ `condition` nie może być jednocześnie true i false, `then-statement` i `else-statement` z `if-else` instrukcji nigdy oba uruchomić. Po `then-statement` lub `else-statement` działa, kontroli są przesyłane do następnej instrukcji po `if` instrukcji.  
  
 W `if` instrukcji, która nie zawiera `else` instrukcji, jeśli `condition` ma wartość true, `then-statement` działa. Jeśli `condition` ma wartość false, sterowania są przesyłane do następnej instrukcji po `if` instrukcji.  
  
 Zarówno `then-statement` i `else-statement` składa się z jednej instrukcji lub wiele instrukcji, które są ujęte w nawiasy klamrowe (`{}`). Dla jednej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.  
  
 Instrukcji lub instrukcjach w `then-statement` i `else-statement` mogą być dowolnego rodzaju, włącznie z innego `if` zagnieżdżonych instrukcji w oryginalnej `if` instrukcji. Zagnieżdżone w `if` instrukcji każdego `else` klauzuli należy do ostatniego `if` który nie ma odpowiedniego elementu `else`. W poniższym przykładzie `Result1` jest wyświetlany, jeśli obie `m > 10` i `n > 20` zwrócić wartość true. Jeśli `m > 10` ma wartość true, ale `n > 20` ma wartość false, `Result2` pojawi się.  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 Jeśli natomiast ma `Result2` się pojawiać, gdy `(m > 10)` ma wartość false, to skojarzenie można określić za pomocą nawiasów klamrowych ustanowienie początek i koniec zagnieżdżone `if` instrukcji, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 `Result2`jest wyświetlana, gdy warunek `(m > 10)` daje w wyniku wartość false.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, wpisz znak z klawiatury, a program używa zagnieżdżoną `if` instrukcji, aby określić, czy znak wejściowy jest znakiem alfabetycznym. Jeśli znak wejściowy jest litera, program sprawdza, czy znak wejściowy jest małe lub wielkie litery. Pojawi się komunikat dla każdego przypadku.  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a>Przykład  
 Ponadto można zagnieżdżać `if` instrukcji wewnątrz innego bloku, jak przedstawiono na poniższym kodu częściowej. Przykład zagnieżdża `if` instrukcje wewnątrz dwa bloki else i jeden blok następnie. Komentarze Określ warunki, które są true lub false w każdym bloku.  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa, czy znak wejściowy jest mała litera, wielką literą lub cyfrą. Jeśli wszystkie trzy warunki false, znak nie jest znakiem alfanumerycznym. Przykład wyświetla komunikat dla każdego przypadku.  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 Tak samo, jak instrukcji else bloku lub następnie bloku może być dowolnym prawidłową instrukcję, używając dowolne prawidłowe wyrażenie logiczne dla warunku. Można użyć operatorów logicznych, takich jak [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md), [ & ](../../../csharp/language-reference/operators/and-operator.md), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) i [!](../../../csharp/language-reference/operators/logical-negation-operator.md) Aby można było złożonych warunków. Poniższy kod przedstawia przykłady.  
  
```csharp  
// NOT  
bool result = true;  
if (!result)  
{  
    Console.WriteLine("The condition is true (result is false).");  
}  
else  
{  
    Console.WriteLine("The condition is false (result is true).");  
}  
  
// Short-circuit AND  
int m = 9;  
int n = 7;  
int p = 5;  
if (m >= n && m >= p)  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// AND and NOT  
if (m >= n && !(p > m))  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// Short-circuit OR  
if (m > n || m > p)  
{  
    Console.WriteLine("m isn't the smallest.");  
}  
  
// NOT and OR  
m = 4;  
if (!(m >= n || m >= p))  
{  
    Console.WriteLine("Now m is the smallest.");  
}  
// Output:  
// The condition is false (result is true).  
// Nothing is larger than m.  
// Nothing is larger than m.  
// m isn't the smallest.  
// Now m is the smallest.  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [?: — Operator](../../../csharp/language-reference/operators/conditional-operator.md)  
 [if-else — instrukcja (C++)](/cpp/cpp/if-else-statement-cpp)  
 [Przełącznik](../../../csharp/language-reference/keywords/switch.md)
