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
# <a name="if-else-c-reference"></a><span data-ttu-id="f7244-102">if-else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f7244-102">if-else (C# Reference)</span></span>

<span data-ttu-id="f7244-103">Instrukcja `if` określa, która instrukcja ma być uruchamiana na podstawie wartości wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="f7244-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="f7244-104">W poniższym przykładzie zmienna `bool` `condition` jest ustawiona na `true`, a następnie zaewidencjonowana w instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="f7244-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="f7244-105">Dane wyjściowe są `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="f7244-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="f7244-106">Przykłady w tym temacie można uruchomić, umieszczając je w `Main` metodzie aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="f7244-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="f7244-107">Instrukcja `if` w C# może przyjmować dwie formy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f7244-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="f7244-108">W instrukcji `if-else`, jeśli `condition` ma wartość true, `then-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="f7244-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="f7244-109">Jeśli `condition` ma wartość false, `else-statement` zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f7244-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="f7244-110">Ponieważ `condition` nie może mieć jednocześnie wartości true i false, `then-statement` i `else-statement` instrukcji `if-else` nigdy nie mogą być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="f7244-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="f7244-111">Po uruchomieniu `then-statement` lub `else-statement`, formant zostanie przeniesiony do następnej instrukcji po instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="f7244-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="f7244-112">W instrukcji `if`, która nie zawiera instrukcji `else`, jeśli `condition` ma wartość true, `then-statement` zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f7244-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="f7244-113">Jeśli `condition` ma wartość false, sterowanie jest przekazywane do następnej instrukcji po instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="f7244-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="f7244-114">Zarówno `then-statement`, jak i `else-statement` mogą składać się z pojedynczej instrukcji lub wielu instrukcji, które są ujęte w nawiasy klamrowe (`{}`).</span><span class="sxs-lookup"><span data-stu-id="f7244-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="f7244-115">W przypadku pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.</span><span class="sxs-lookup"><span data-stu-id="f7244-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="f7244-116">Instrukcja lub instrukcje w `then-statement` i `else-statement` mogą być dowolnego rodzaju, łącznie z inną instrukcją `if` zagnieżdżoną wewnątrz oryginalnej instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="f7244-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="f7244-117">W zagnieżdżonych instrukcjach `if` Każda klauzula `else` należy do ostatniej `if`, która nie ma odpowiedniego `else`.</span><span class="sxs-lookup"><span data-stu-id="f7244-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="f7244-118">W poniższym przykładzie `Result1` pojawia się, jeśli oba `m > 10` i `n > 20` mają wartość true.</span><span class="sxs-lookup"><span data-stu-id="f7244-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="f7244-119">Jeśli `m > 10` ma wartość true, ale `n > 20` ma wartość false, `Result2` pojawia się.</span><span class="sxs-lookup"><span data-stu-id="f7244-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="f7244-120">Jeśli zamiast tego chcesz, aby `Result2` pojawiał się, gdy `(m > 10)` ma wartość false, możesz określić to skojarzenie przy użyciu nawiasów klamrowych, aby ustalić początkową i końcową zagnieżdżoną instrukcję `if`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f7244-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="f7244-121">`Result2` pojawia się, jeśli warunek `(m > 10)` wartość false.</span><span class="sxs-lookup"><span data-stu-id="f7244-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="f7244-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7244-122">Example</span></span>

<span data-ttu-id="f7244-123">W poniższym przykładzie wprowadzasz znak z klawiatury, a program używa zagnieżdżonej instrukcji `if`, aby określić, czy znak wejściowy jest znakiem alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="f7244-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="f7244-124">Jeśli znak wejściowy jest znakiem alfabetycznym, program sprawdza, czy znak wejściowy jest pisany małymi lub wielką literą.</span><span class="sxs-lookup"><span data-stu-id="f7244-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="f7244-125">W każdym przypadku pojawia się komunikat.</span><span class="sxs-lookup"><span data-stu-id="f7244-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="f7244-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7244-126">Example</span></span>

<span data-ttu-id="f7244-127">Można również zagnieżdżać instrukcję `if` wewnątrz bloku else, jak pokazano Poniższy kod częściowy.</span><span class="sxs-lookup"><span data-stu-id="f7244-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="f7244-128">Przykład zagnieżdża instrukcje `if` w dwóch blokach else i jednym bloku then.</span><span class="sxs-lookup"><span data-stu-id="f7244-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="f7244-129">Komentarze określają, które warunki mają wartość PRAWDA lub FAŁSZ w każdym bloku.</span><span class="sxs-lookup"><span data-stu-id="f7244-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="f7244-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7244-130">Example</span></span>

<span data-ttu-id="f7244-131">Poniższy przykład określa, czy znak wejściowy jest małą literą, wielką literą lub cyfrą.</span><span class="sxs-lookup"><span data-stu-id="f7244-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="f7244-132">Jeśli wszystkie trzy warunki mają wartość FAŁSZ, znak nie jest znakiem alfanumerycznym.</span><span class="sxs-lookup"><span data-stu-id="f7244-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="f7244-133">Przykład wyświetla komunikat dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="f7244-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="f7244-134">Podobnie jak instrukcja w bloku else lub blok then może być dowolną prawidłową instrukcją, można użyć dowolnego prawidłowego wyrażenia logicznego dla warunku.</span><span class="sxs-lookup"><span data-stu-id="f7244-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="f7244-135">Do wprowadzania warunków złożonych można użyć [operatorów logicznych](../operators/boolean-logical-operators.md) , takich jak `!`, `&&`, `||`, `&`, `|`i `^`.</span><span class="sxs-lookup"><span data-stu-id="f7244-135">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="f7244-136">Poniższy kod przedstawia przykłady.</span><span class="sxs-lookup"><span data-stu-id="f7244-136">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="f7244-137">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f7244-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f7244-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7244-138">See also</span></span>

- [<span data-ttu-id="f7244-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f7244-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f7244-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f7244-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f7244-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f7244-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f7244-142">?:, operator</span><span class="sxs-lookup"><span data-stu-id="f7244-142">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="f7244-143">if-else, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="f7244-143">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="f7244-144">switch</span><span class="sxs-lookup"><span data-stu-id="f7244-144">switch</span></span>](switch.md)
