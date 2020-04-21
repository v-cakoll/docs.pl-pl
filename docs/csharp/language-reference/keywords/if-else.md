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
# <a name="if-else-c-reference"></a><span data-ttu-id="ae4a4-102">if-else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ae4a4-102">if-else (C# Reference)</span></span>

<span data-ttu-id="ae4a4-103">Instrukcja `if` określa, która instrukcja do uruchomienia na podstawie wartości wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="ae4a4-104">W poniższym przykładzie `condition` zmienna `true` jest ustawiona, `if` `bool` a następnie zaewidencjonowana w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="ae4a4-105">Wyjście jest `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="ae4a4-106">Przykłady w tym temacie można uruchomić, `Main` umieszczając je w metodzie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="ae4a4-107">Instrukcja `if` w języku C# może przybierać dwie formy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="ae4a4-108">W `if-else` instrukcji, `condition` jeśli ma wartość `then-statement` true, przebiegi.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="ae4a4-109">Jeśli `condition` jest false, przebiegi. `else-statement`</span><span class="sxs-lookup"><span data-stu-id="ae4a4-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="ae4a4-110">Ponieważ `condition` nie może być jednocześnie prawdziwe `then-statement` i `else-statement` fałszywe, i instrukcji `if-else` nigdy nie można uruchomić.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="ae4a4-111">Po `then-statement` lub `else-statement` uruchamia, kontrola jest przenoszona do `if` następnej instrukcji po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="ae4a4-112">W `if` instrukcji, która nie `else` zawiera instrukcji, jeśli `condition` `then-statement` jest true, przebiegi.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="ae4a4-113">Jeśli `condition` jest false, kontrola jest przenoszona `if` do następnej instrukcji po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="ae4a4-114">Zarówno `then-statement` i `else-statement` może składać się z pojedynczej instrukcji lub wielu`{}`instrukcji, które są ujęte w nawiasy klamrowe ( ).</span><span class="sxs-lookup"><span data-stu-id="ae4a4-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="ae4a4-115">Dla pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="ae4a4-116">Instrukcja lub `then-statement` instrukcje `else-statement` w i może być `if` dowolnego rodzaju, w `if` tym innej instrukcji zagnieżdżone wewnątrz oryginalnej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="ae4a4-117">W `if` instrukcjach zagnieżdżonych każda `else` klauzula należy do ostatniej, `if` która nie ma odpowiedniego `else`.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="ae4a4-118">W poniższym `Result1` przykładzie `m > 10` pojawia `n > 20` się, jeśli oba i ocenić true.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="ae4a4-119">Jeśli `m > 10` jest `n > 20` prawdziwa, `Result2` ale jest false, pojawia się.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="ae4a4-120">Jeśli zamiast tego chcesz `Result2` pojawić `(m > 10)` się, gdy jest false, można określić, że skojarzenie za `if` pomocą nawiasów klamrowych do ustanowienia początku i końca instrukcji zagnieżdżonej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="ae4a4-121">`Result2`pojawia się, `(m > 10)` jeśli warunek ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="ae4a4-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae4a4-122">Example</span></span>

<span data-ttu-id="ae4a4-123">W poniższym przykładzie należy wprowadzić znak z klawiatury, a `if` program używa instrukcji zagnieżdżonej, aby określić, czy znak wejściowy jest znakiem alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="ae4a4-124">Jeśli znak wejściowy jest znakiem alfabetycznym, program sprawdza, czy znak wejściowy jest małe, czy wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="ae4a4-125">Dla każdego przypadku zostanie wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="ae4a4-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae4a4-126">Example</span></span>

<span data-ttu-id="ae4a4-127">Można również zagnieżdżać instrukcję `if` wewnątrz bloku else, jak pokazano w poniższym kodzie częściowym.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-127">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="ae4a4-128">Przykład zagnieżdża instrukcje `if` wewnątrz dwóch innych bloków i jeden następnie blokować.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="ae4a4-129">Komentarze określają, które warunki są prawdziwe lub fałszywe w każdym bloku.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="ae4a4-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae4a4-130">Example</span></span>

<span data-ttu-id="ae4a4-131">Poniższy przykład określa, czy znak wejściowy jest pisakiem wielkim, wielką literą czy liczbą.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="ae4a4-132">Jeśli wszystkie trzy warunki są false, znak nie jest znakiem alfanumerycznym.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="ae4a4-133">W przykładzie jest wyświetlany komunikat dla każdej sprawy.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="ae4a4-134">Podobnie jak instrukcja w bloku else lub następnie bloku może być dowolną prawidłową instrukcję, można użyć dowolnego prawidłowego wyrażenia logicznego dla warunku.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="ae4a4-135">Można użyć [operatorów logicznych,](../operators/boolean-logical-operators.md) `|`takich `^` jak `!`, `&&`, `||` `&`, i do tworzenia warunków złożonych.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="ae4a4-136">Poniższy kod przedstawia przykłady.</span><span class="sxs-lookup"><span data-stu-id="ae4a4-136">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="ae4a4-137">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ae4a4-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ae4a4-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae4a4-138">See also</span></span>

- [<span data-ttu-id="ae4a4-139">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ae4a4-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ae4a4-140">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="ae4a4-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ae4a4-141">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ae4a4-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ae4a4-142">?: Operator</span><span class="sxs-lookup"><span data-stu-id="ae4a4-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="ae4a4-143">if-else — instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="ae4a4-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="ae4a4-144">switch</span><span class="sxs-lookup"><span data-stu-id="ae4a4-144">switch</span></span>](switch.md)
