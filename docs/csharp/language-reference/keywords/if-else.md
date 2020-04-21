---
title: if-else - Odwołanie do języka C#
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
ms.openlocfilehash: 61b60674d3b5de4649a52d2a165265ae0a27e0be
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738849"
---
# <a name="if-else-c-reference"></a>if-else (odwołanie w C#)

Instrukcja `if` określa, która instrukcja do uruchomienia na podstawie wartości wyrażenia logicznego. W poniższym przykładzie `condition` zmienna `true` jest ustawiona, `if` `bool` a następnie zaewidencjonowana w instrukcji. Wyjście jest `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Przykłady w tym temacie można uruchomić, `Main` umieszczając je w metodzie aplikacji konsoli.

Instrukcja `if` w języku C# może przybierać dwie formy, jak pokazano w poniższym przykładzie.

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

W `if-else` instrukcji, `condition` jeśli ma wartość `then-statement` true, przebiegi. Jeśli `condition` jest false, przebiegi. `else-statement` Ponieważ `condition` nie może być jednocześnie prawdziwe `then-statement` i `else-statement` fałszywe, i instrukcji `if-else` nigdy nie można uruchomić. Po `then-statement` lub `else-statement` uruchamia, kontrola jest przenoszona do `if` następnej instrukcji po instrukcji.

W `if` instrukcji, która nie `else` zawiera instrukcji, jeśli `condition` `then-statement` jest true, przebiegi. Jeśli `condition` jest false, kontrola jest przenoszona `if` do następnej instrukcji po instrukcji.

Zarówno `then-statement` i `else-statement` może składać się z pojedynczej instrukcji lub wielu`{}`instrukcji, które są ujęte w nawiasy klamrowe ( ). Dla pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.

Instrukcja lub `then-statement` instrukcje `else-statement` w i może być `if` dowolnego rodzaju, w `if` tym innej instrukcji zagnieżdżone wewnątrz oryginalnej instrukcji. W `if` instrukcjach zagnieżdżonych każda `else` klauzula należy do ostatniej, `if` która nie ma odpowiedniego `else`. W poniższym `Result1` przykładzie `m > 10` pojawia `n > 20` się, jeśli oba i ocenić true. Jeśli `m > 10` jest `n > 20` prawdziwa, `Result2` ale jest false, pojawia się.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Jeśli zamiast tego chcesz `Result2` pojawić `(m > 10)` się, gdy jest false, można określić, że skojarzenie za `if` pomocą nawiasów klamrowych do ustanowienia początku i końca instrukcji zagnieżdżonej, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2`pojawia się, `(m > 10)` jeśli warunek ma wartość false.

## <a name="example"></a>Przykład

W poniższym przykładzie należy wprowadzić znak z klawiatury, a `if` program używa instrukcji zagnieżdżonej, aby określić, czy znak wejściowy jest znakiem alfabetycznym. Jeśli znak wejściowy jest znakiem alfabetycznym, program sprawdza, czy znak wejściowy jest małe, czy wielkie litery. Dla każdego przypadku zostanie wyświetlony komunikat.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Przykład

Można również zagnieżdżać instrukcję `if` wewnątrz bloku else, jak pokazano w poniższym kodzie częściowym. Przykład zagnieżdża instrukcje `if` wewnątrz dwóch innych bloków i jeden następnie blokować. Komentarze określają, które warunki są prawdziwe lub fałszywe w każdym bloku.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład określa, czy znak wejściowy jest pisakiem wielkim, wielką literą czy liczbą. Jeśli wszystkie trzy warunki są false, znak nie jest znakiem alfanumerycznym. W przykładzie jest wyświetlany komunikat dla każdej sprawy.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Podobnie jak instrukcja w bloku else lub następnie bloku może być dowolną prawidłową instrukcję, można użyć dowolnego prawidłowego wyrażenia logicznego dla warunku. Można użyć [operatorów logicznych,](../operators/boolean-logical-operators.md) `|`takich `^` jak `!`, `&&`, `||` `&`, i do tworzenia warunków złożonych. Poniższy kod przedstawia przykłady.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [?: Operator](../operators/conditional-operator.md)
- [if-else — instrukcja (C++)](/cpp/cpp/if-else-statement-cpp)
- [switch](switch.md)
