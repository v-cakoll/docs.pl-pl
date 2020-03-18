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
# <a name="if-else-c-reference"></a><span data-ttu-id="f69cc-102">if-else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f69cc-102">if-else (C# Reference)</span></span>

<span data-ttu-id="f69cc-103">Instrukcja `if` określa, która instrukcja do uruchomienia na podstawie wartości wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="f69cc-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="f69cc-104">W poniższym przykładzie `bool` `condition` zmienna `true` jest ustawiona na, `if` a następnie zaewidencjonowana w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f69cc-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="f69cc-105">Wyjście jest `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="f69cc-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="f69cc-106">Przykłady w tym temacie można uruchomić, umieszczając `Main` je w metodzie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="f69cc-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="f69cc-107">Instrukcja `if` w języku C# może mieć dwie formy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f69cc-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="f69cc-108">W `if-else` instrukcji, `condition` jeśli ocenia true, `then-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="f69cc-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="f69cc-109">Jeśli `condition` jest false, `else-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="f69cc-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="f69cc-110">Ponieważ `condition` nie może być jednocześnie prawdziwe `then-statement` i `else-statement` fałszywe, `if-else` i instrukcji nigdy nie można uruchomić.</span><span class="sxs-lookup"><span data-stu-id="f69cc-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="f69cc-111">Po `then-statement` lub `else-statement` przebiegów, kontrola jest przekazywana do `if` następnej instrukcji po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f69cc-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="f69cc-112">W `if` instrukcji, która nie `else` zawiera instrukcji, jeśli `condition` `then-statement` jest true, działa.</span><span class="sxs-lookup"><span data-stu-id="f69cc-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="f69cc-113">Jeśli `condition` jest false, kontrola jest przekazywana `if` do następnej instrukcji po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f69cc-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="f69cc-114">Zarówno `then-statement` i `else-statement` może składać się z jednej instrukcji lub wiele`{}`instrukcji, które są ujęte w nawiasach klamrowych ( ).</span><span class="sxs-lookup"><span data-stu-id="f69cc-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="f69cc-115">Dla pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.</span><span class="sxs-lookup"><span data-stu-id="f69cc-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="f69cc-116">Instrukcji lub instrukcji `then-statement` w `else-statement` i może być dowolnego `if` rodzaju, w tym `if` innej instrukcji zagnieżdżonych wewnątrz oryginalnej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f69cc-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="f69cc-117">W `if` zagnieżdżonych instrukcjach każda `else` klauzula należy do ostatniego, `if` który nie ma odpowiedniego `else`.</span><span class="sxs-lookup"><span data-stu-id="f69cc-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="f69cc-118">W poniższym `Result1` przykładzie pojawia `m > 10` `n > 20` się, jeśli oba i ocenić true.</span><span class="sxs-lookup"><span data-stu-id="f69cc-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="f69cc-119">Jeśli `m > 10` jest `n > 20` true, `Result2` ale jest false, pojawia się.</span><span class="sxs-lookup"><span data-stu-id="f69cc-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="f69cc-120">Jeśli zamiast tego `Result2` chcesz pojawić `(m > 10)` się, gdy jest false, można określić tego skojarzenia za `if` pomocą nawiasów klamrowych, aby ustanowić początek i koniec zagnieżdżone instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f69cc-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="f69cc-121">`Result2`pojawia się, `(m > 10)` jeśli warunek zostanie błędnie podjęta.</span><span class="sxs-lookup"><span data-stu-id="f69cc-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="f69cc-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f69cc-122">Example</span></span>

<span data-ttu-id="f69cc-123">W poniższym przykładzie należy wprowadzić znak z klawiatury, a `if` program używa zagnieżdżonej instrukcji, aby określić, czy znak wejściowy jest znakiem alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="f69cc-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="f69cc-124">Jeśli znak wejściowy jest znakiem alfabetycznym, program sprawdza, czy znak wejściowy jest małych, czy wielkich.</span><span class="sxs-lookup"><span data-stu-id="f69cc-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="f69cc-125">Dla każdego przypadku zostanie wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="f69cc-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="f69cc-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f69cc-126">Example</span></span>

<span data-ttu-id="f69cc-127">Można również zagnieździć instrukcję `if` wewnątrz bloku else, jak pokazano w poniższym kodzie częściowym.</span><span class="sxs-lookup"><span data-stu-id="f69cc-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="f69cc-128">Przykład gniazduje `if` instrukcje wewnątrz dwóch bloków else i jeden następnie bloku.</span><span class="sxs-lookup"><span data-stu-id="f69cc-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="f69cc-129">Komentarze określają, które warunki są prawdziwe lub fałszywe w każdym bloku.</span><span class="sxs-lookup"><span data-stu-id="f69cc-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="f69cc-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="f69cc-130">Example</span></span>

<span data-ttu-id="f69cc-131">Poniższy przykład określa, czy znak wejściowy jest literą pisaną, wielkimi literami czy liczbą.</span><span class="sxs-lookup"><span data-stu-id="f69cc-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="f69cc-132">Jeśli wszystkie trzy warunki są fałszywe, znak nie jest znakiem alfanumerycznym.</span><span class="sxs-lookup"><span data-stu-id="f69cc-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="f69cc-133">W przykładzie jest wyświetlany komunikat dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="f69cc-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="f69cc-134">Podobnie jak instrukcja w innym bloku lub następnie bloku może być dowolna prawidłowa instrukcja, można użyć dowolnego prawidłowego wyrażenia logicznego dla warunku.</span><span class="sxs-lookup"><span data-stu-id="f69cc-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="f69cc-135">Do tworzenia warunków złożonych można `&` `|`używać `^` [operatorów logicznych,](../operators/boolean-logical-operators.md) takich jak `!`, `&&`, `||`, i do tworzenia warunków złożonych.</span><span class="sxs-lookup"><span data-stu-id="f69cc-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="f69cc-136">Poniższy kod zawiera przykłady.</span><span class="sxs-lookup"><span data-stu-id="f69cc-136">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="f69cc-137">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f69cc-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f69cc-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f69cc-138">See also</span></span>

- [<span data-ttu-id="f69cc-139">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="f69cc-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f69cc-140">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f69cc-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f69cc-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f69cc-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f69cc-142">?: Operator</span><span class="sxs-lookup"><span data-stu-id="f69cc-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="f69cc-143">if-else — instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="f69cc-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="f69cc-144">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="f69cc-144">switch</span></span>](switch.md)
