---
title: if-else - C# odwołania
ms.custom: seodec18
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
ms.openlocfilehash: a205ee04d1b0b68666ca50109001e71288d7f434
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517841"
---
# <a name="if-else-c-reference"></a>if-else (odwołanie w C#)

`if` Instrukcja identyfikuje, które instrukcji do uruchomienia na podstawie wartości wyrażenia logicznego. W poniższym przykładzie `bool` zmiennej `condition` ustawiono `true` i następnie zaewidencjonować `if` instrukcji. Dane wyjściowe są `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Można uruchomić przykłady w tym temacie, umieszczając je w `Main` metoda aplikacji konsoli.

`if` Instrukcji w języku C# może potrwać dwie formy, co ilustruje poniższy przykład.

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

W `if-else` instrukcji, jeśli `condition` zwraca wartość true, `then-statement` działa. Jeśli `condition` ma wartość FAŁSZ, `else-statement` działa. Ponieważ `condition` nie może być jednocześnie true i false, `then-statement` i `else-statement` z `if-else` instrukcji może nigdy nie jednocześnie uruchomione. Po `then-statement` lub `else-statement` przebiegów, kontrola jest przekazywana do następnej instrukcji po `if` instrukcji.

W `if` instrukcję, która nie obejmuje `else` instrukcji, jeśli `condition` ma wartość true, `then-statement` działa. Jeśli `condition` ma wartość FAŁSZ, kontrola jest przekazywana do następnej instrukcji po `if` instrukcji.

Zarówno `then-statement` i `else-statement` składa się z pojedynczej instrukcji lub wiele instrukcji, które są ujęte w nawiasy klamrowe (`{}`). W przypadku pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.

Instrukcji lub instrukcji w `then-statement` i `else-statement` mogą być dowolnego rodzaju, w tym innego `if` instrukcji zagnieżdżonych w oryginalnym `if` instrukcji. W zagnieżdżonej `if` instrukcji każdego `else` klauzuli należy do ostatniego `if` , która nie ma odpowiadającej `else`. W poniższym przykładzie `Result1` jest wyświetlana, gdy oba `m > 10` i `n > 20` przyjmowało wartość true. Jeśli `m > 10` ma wartość true, ale `n > 20` ma wartość FAŁSZ, `Result2` pojawia się.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Jeśli zamiast tego chcesz, aby `Result2` się pojawiać, gdy `(m > 10)` ma wartość FAŁSZ, można określić tego skojarzenia przy użyciu nawiasów klamrowych, można ustanowić początek i koniec zagnieżdżonego `if` instrukcji, co ilustruje poniższy przykład.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` jest wyświetlana, gdy warunek `(m > 10)` zwróci wartość false.

## <a name="example"></a>Przykład

W poniższym przykładzie, wpisz znak przy użyciu klawiatury i program używa zagnieżdżoną `if` instrukcię, aby określić, czy znak danych wejściowych jest znakiem alfabetycznym. Jeśli wejściowy znak jest znakiem alfabetycznym, program sprawdza, czy znak danych wejściowych jest wielką czy małą literą. Pojawia się komunikat dla każdego przypadku.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Przykład

Można także zagnieżdżać `if` instrukcji wewnątrz innego bloku, co ilustruje poniższy kod częściowe. Przykład zagnieżdża instrukcje `if` instrukcji wewnątrz dwóch bloków jeszcze jeden blok następnie. Komentarze Określ warunki, które są prawdziwe lub fałszywe w każdym bloku.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład określa, czy znak danych wejściowych jest mała litera, Wielka litera lub liczbą. Jeśli wszystkie trzy warunki mają wartość false, znak jest znakiem alfanumerycznym. Przykład wyświetla komunikat w każdym przypadku.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Tak, jak instrukcji else bloku lub bloku następnie może być dowolną prawidłową instrukcją, można użyć dowolne prawidłowe wyrażenie logiczne dla warunku. Można użyć operatorów logicznych, takich jak [ && ](../operators/conditional-and-operator.md), [ & ](../operators/and-operator.md), [ &#124; &#124; ](../operators/conditional-or-operator.md), [ &#124; ](../operators/or-operator.md) i [!](../operators/logical-negation-operator.md) Aby złożone warunki. Poniższy kod przedstawia przykłady.

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
- [?: operator](../operators/conditional-operator.md)
- [if-else, instrukcja (C++)](/cpp/cpp/if-else-statement-cpp)
- [switch](switch.md)
