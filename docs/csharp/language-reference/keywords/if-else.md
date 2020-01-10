---
title: if-else- C# Reference
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: 98c1a8dceec3e5a47627841988e2d722c56fc36c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715262"
---
# <a name="if-else-c-reference"></a>if-else (odwołanie w C#)

Instrukcja `if` określa, która instrukcja ma być uruchamiana na podstawie wartości wyrażenia logicznego. W poniższym przykładzie zmienna `bool` `condition` jest ustawiona na `true`, a następnie zaewidencjonowana w instrukcji `if`. Dane wyjściowe są `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Przykłady w tym temacie można uruchomić, umieszczając je w `Main` metodzie aplikacji konsolowej.

Instrukcja `if` w C# może przyjmować dwie formy, jak pokazano w poniższym przykładzie.

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

W instrukcji `if-else`, jeśli `condition` ma wartość true, `then-statement` działa. Jeśli `condition` ma wartość false, `else-statement` zostanie uruchomiony. Ponieważ `condition` nie może mieć jednocześnie wartości true i false, `then-statement` i `else-statement` instrukcji `if-else` nigdy nie mogą być uruchamiane. Po uruchomieniu `then-statement` lub `else-statement`, formant zostanie przeniesiony do następnej instrukcji po instrukcji `if`.

W instrukcji `if`, która nie zawiera instrukcji `else`, jeśli `condition` ma wartość true, `then-statement` zostanie uruchomiony. Jeśli `condition` ma wartość false, sterowanie jest przekazywane do następnej instrukcji po instrukcji `if`.

Zarówno `then-statement`, jak i `else-statement` mogą składać się z pojedynczej instrukcji lub wielu instrukcji, które są ujęte w nawiasy klamrowe (`{}`). W przypadku pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.

Instrukcja lub instrukcje w `then-statement` i `else-statement` mogą być dowolnego rodzaju, łącznie z inną instrukcją `if` zagnieżdżoną wewnątrz oryginalnej instrukcji `if`. W zagnieżdżonych instrukcjach `if` Każda klauzula `else` należy do ostatniej `if`, która nie ma odpowiedniego `else`. W poniższym przykładzie `Result1` pojawia się, jeśli oba `m > 10` i `n > 20` mają wartość true. Jeśli `m > 10` ma wartość true, ale `n > 20` ma wartość false, `Result2` pojawia się.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Jeśli zamiast tego chcesz, aby `Result2` pojawiał się, gdy `(m > 10)` ma wartość false, możesz określić to skojarzenie przy użyciu nawiasów klamrowych, aby ustalić początkową i końcową zagnieżdżoną instrukcję `if`, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` pojawia się, jeśli warunek `(m > 10)` wartość false.

## <a name="example"></a>Przykład

W poniższym przykładzie wprowadzasz znak z klawiatury, a program używa zagnieżdżonej instrukcji `if`, aby określić, czy znak wejściowy jest znakiem alfabetycznym. Jeśli znak wejściowy jest znakiem alfabetycznym, program sprawdza, czy znak wejściowy jest pisany małymi lub wielką literą. W każdym przypadku pojawia się komunikat.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Przykład

Można również zagnieżdżać instrukcję `if` wewnątrz bloku else, jak pokazano Poniższy kod częściowy. Przykład zagnieżdża instrukcje `if` w dwóch blokach else i jednym bloku then. Komentarze określają, które warunki mają wartość PRAWDA lub FAŁSZ w każdym bloku.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład określa, czy znak wejściowy jest małą literą, wielką literą lub cyfrą. Jeśli wszystkie trzy warunki mają wartość FAŁSZ, znak nie jest znakiem alfanumerycznym. Przykład wyświetla komunikat dla każdego przypadku.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Podobnie jak instrukcja w bloku else lub blok then może być dowolną prawidłową instrukcją, można użyć dowolnego prawidłowego wyrażenia logicznego dla warunku. Do wprowadzania warunków złożonych można użyć [operatorów logicznych](../operators/boolean-logical-operators.md) , takich jak `!`, `&&`, `||`, `&`, `|`i `^`. Poniższy kod przedstawia przykłady.

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

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [?:, operator](../operators/conditional-operator.md)
- [if-else, instrukcja (C++)](/cpp/cpp/if-else-statement-cpp)
- [switch](switch.md)
