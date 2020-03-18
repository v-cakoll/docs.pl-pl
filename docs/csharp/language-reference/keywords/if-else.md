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
ms.openlocfilehash: 98c1a8dceec3e5a47627841988e2d722c56fc36c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715262"
---
# <a name="if-else-c-reference"></a>if-else (odwołanie w C#)

Instrukcja `if` określa, która instrukcja do uruchomienia na podstawie wartości wyrażenia logicznego. W poniższym przykładzie `bool` `condition` zmienna `true` jest ustawiona na, `if` a następnie zaewidencjonowana w instrukcji. Wyjście jest `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Przykłady w tym temacie można uruchomić, umieszczając `Main` je w metodzie aplikacji konsoli.

Instrukcja `if` w języku C# może mieć dwie formy, jak pokazano w poniższym przykładzie.

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

W `if-else` instrukcji, `condition` jeśli ocenia true, `then-statement` działa. Jeśli `condition` jest false, `else-statement` działa. Ponieważ `condition` nie może być jednocześnie prawdziwe `then-statement` i `else-statement` fałszywe, `if-else` i instrukcji nigdy nie można uruchomić. Po `then-statement` lub `else-statement` przebiegów, kontrola jest przekazywana do `if` następnej instrukcji po instrukcji.

W `if` instrukcji, która nie `else` zawiera instrukcji, jeśli `condition` `then-statement` jest true, działa. Jeśli `condition` jest false, kontrola jest przekazywana `if` do następnej instrukcji po instrukcji.

Zarówno `then-statement` i `else-statement` może składać się z jednej instrukcji lub wiele`{}`instrukcji, które są ujęte w nawiasach klamrowych ( ). Dla pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.

Instrukcji lub instrukcji `then-statement` w `else-statement` i może być dowolnego `if` rodzaju, w tym `if` innej instrukcji zagnieżdżonych wewnątrz oryginalnej instrukcji. W `if` zagnieżdżonych instrukcjach każda `else` klauzula należy do ostatniego, `if` który nie ma odpowiedniego `else`. W poniższym `Result1` przykładzie pojawia `m > 10` `n > 20` się, jeśli oba i ocenić true. Jeśli `m > 10` jest `n > 20` true, `Result2` ale jest false, pojawia się.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Jeśli zamiast tego `Result2` chcesz pojawić `(m > 10)` się, gdy jest false, można określić tego skojarzenia za `if` pomocą nawiasów klamrowych, aby ustanowić początek i koniec zagnieżdżone instrukcji, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2`pojawia się, `(m > 10)` jeśli warunek zostanie błędnie podjęta.

## <a name="example"></a>Przykład

W poniższym przykładzie należy wprowadzić znak z klawiatury, a `if` program używa zagnieżdżonej instrukcji, aby określić, czy znak wejściowy jest znakiem alfabetycznym. Jeśli znak wejściowy jest znakiem alfabetycznym, program sprawdza, czy znak wejściowy jest małych, czy wielkich. Dla każdego przypadku zostanie wyświetlony komunikat.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Przykład

Można również zagnieździć instrukcję `if` wewnątrz bloku else, jak pokazano w poniższym kodzie częściowym. Przykład gniazduje `if` instrukcje wewnątrz dwóch bloków else i jeden następnie bloku. Komentarze określają, które warunki są prawdziwe lub fałszywe w każdym bloku.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Przykład

Poniższy przykład określa, czy znak wejściowy jest literą pisaną, wielkimi literami czy liczbą. Jeśli wszystkie trzy warunki są fałszywe, znak nie jest znakiem alfanumerycznym. W przykładzie jest wyświetlany komunikat dla każdego przypadku.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Podobnie jak instrukcja w innym bloku lub następnie bloku może być dowolna prawidłowa instrukcja, można użyć dowolnego prawidłowego wyrażenia logicznego dla warunku. Do tworzenia warunków złożonych można `&` `|`używać `^` [operatorów logicznych,](../operators/boolean-logical-operators.md) takich jak `!`, `&&`, `||`, i do tworzenia warunków złożonych. Poniższy kod zawiera przykłady.

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
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [?: Operator](../operators/conditional-operator.md)
- [if-else — instrukcja (C++)](/cpp/cpp/if-else-statement-cpp)
- [Przełącznik](switch.md)
