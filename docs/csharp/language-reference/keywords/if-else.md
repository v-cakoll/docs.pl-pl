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
ms.openlocfilehash: ccb783d8d478b14078ab6fe09f12e480c12ac06b
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084774"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="10937-102">if-else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="10937-102">if-else (C# Reference)</span></span>

<span data-ttu-id="10937-103">`if` Instrukcja identyfikuje, które instrukcji do uruchomienia na podstawie wartości wyrażenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="10937-103">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="10937-104">W poniższym przykładzie `bool` zmiennej `condition` ustawiono `true` i następnie zaewidencjonować `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="10937-104">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="10937-105">Dane wyjściowe są `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="10937-105">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="10937-106">Można uruchomić przykłady w tym temacie, umieszczając je w `Main` metoda aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="10937-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="10937-107">`if` Instrukcji w języku C# może potrwać dwie formy, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="10937-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>

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

<span data-ttu-id="10937-108">W `if-else` instrukcji, jeśli `condition` zwraca wartość true, `then-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="10937-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="10937-109">Jeśli `condition` ma wartość FAŁSZ, `else-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="10937-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="10937-110">Ponieważ `condition` nie może być jednocześnie true i false, `then-statement` i `else-statement` z `if-else` instrukcji może nigdy nie jednocześnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="10937-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="10937-111">Po `then-statement` lub `else-statement` przebiegów, kontrola jest przekazywana do następnej instrukcji po `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="10937-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="10937-112">W `if` instrukcję, która nie obejmuje `else` instrukcji, jeśli `condition` ma wartość true, `then-statement` działa.</span><span class="sxs-lookup"><span data-stu-id="10937-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="10937-113">Jeśli `condition` ma wartość FAŁSZ, kontrola jest przekazywana do następnej instrukcji po `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="10937-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="10937-114">Zarówno `then-statement` i `else-statement` składa się z pojedynczej instrukcji lub wiele instrukcji, które są ujęte w nawiasy klamrowe (`{}`).</span><span class="sxs-lookup"><span data-stu-id="10937-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="10937-115">W przypadku pojedynczej instrukcji nawiasy klamrowe są opcjonalne, ale zalecane.</span><span class="sxs-lookup"><span data-stu-id="10937-115">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="10937-116">Instrukcji lub instrukcji w `then-statement` i `else-statement` mogą być dowolnego rodzaju, w tym innego `if` instrukcji zagnieżdżonych w oryginalnym `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="10937-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="10937-117">W zagnieżdżonej `if` instrukcji każdego `else` klauzuli należy do ostatniego `if` , która nie ma odpowiadającej `else`.</span><span class="sxs-lookup"><span data-stu-id="10937-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="10937-118">W poniższym przykładzie `Result1` jest wyświetlana, gdy oba `m > 10` i `n > 20` przyjmowało wartość true.</span><span class="sxs-lookup"><span data-stu-id="10937-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="10937-119">Jeśli `m > 10` ma wartość true, ale `n > 20` ma wartość FAŁSZ, `Result2` pojawia się.</span><span class="sxs-lookup"><span data-stu-id="10937-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="10937-120">Jeśli zamiast tego chcesz, aby `Result2` się pojawiać, gdy `(m > 10)` ma wartość FAŁSZ, można określić tego skojarzenia przy użyciu nawiasów klamrowych, można ustanowić początek i koniec zagnieżdżonego `if` instrukcji, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="10937-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="10937-121">`Result2` jest wyświetlana, gdy warunek `(m > 10)` zwróci wartość false.</span><span class="sxs-lookup"><span data-stu-id="10937-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="10937-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="10937-122">Example</span></span>

<span data-ttu-id="10937-123">W poniższym przykładzie, wpisz znak przy użyciu klawiatury i program używa zagnieżdżoną `if` instrukcię, aby określić, czy znak danych wejściowych jest znakiem alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="10937-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="10937-124">Jeśli wejściowy znak jest znakiem alfabetycznym, program sprawdza, czy znak danych wejściowych jest wielką czy małą literą.</span><span class="sxs-lookup"><span data-stu-id="10937-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="10937-125">Pojawia się komunikat dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="10937-125">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="10937-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="10937-126">Example</span></span>

<span data-ttu-id="10937-127">Można także zagnieżdżać `if` instrukcji wewnątrz innego bloku, co ilustruje poniższy kod częściowe.</span><span class="sxs-lookup"><span data-stu-id="10937-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="10937-128">Przykład zagnieżdża instrukcje `if` instrukcji wewnątrz dwóch bloków jeszcze jeden blok następnie.</span><span class="sxs-lookup"><span data-stu-id="10937-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="10937-129">Komentarze Określ warunki, które są prawdziwe lub fałszywe w każdym bloku.</span><span class="sxs-lookup"><span data-stu-id="10937-129">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="10937-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="10937-130">Example</span></span>

<span data-ttu-id="10937-131">Poniższy przykład określa, czy znak danych wejściowych jest mała litera, Wielka litera lub liczbą.</span><span class="sxs-lookup"><span data-stu-id="10937-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="10937-132">Jeśli wszystkie trzy warunki mają wartość false, znak jest znakiem alfanumerycznym.</span><span class="sxs-lookup"><span data-stu-id="10937-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="10937-133">Przykład wyświetla komunikat w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="10937-133">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="10937-134">Tak, jak instrukcji else bloku lub bloku następnie może być dowolną prawidłową instrukcją, można użyć dowolne prawidłowe wyrażenie logiczne dla warunku.</span><span class="sxs-lookup"><span data-stu-id="10937-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="10937-135">Można użyć operatorów logicznych, takich jak [ && ](../operators/conditional-and-operator.md), [ & ](../operators/and-operator.md), [ &#124; &#124; ](../operators/conditional-or-operator.md), [ &#124; ](../operators/or-operator.md) i [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="10937-135">You can use logical operators such as [&&](../operators/conditional-and-operator.md), [&](../operators/and-operator.md), [&#124;&#124;](../operators/conditional-or-operator.md), [&#124;](../operators/or-operator.md) and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="10937-136">Aby złożone warunki.</span><span class="sxs-lookup"><span data-stu-id="10937-136">to make compound conditions.</span></span> <span data-ttu-id="10937-137">Poniższy kod przedstawia przykłady.</span><span class="sxs-lookup"><span data-stu-id="10937-137">The following code shows examples.</span></span>

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

## <a name="c-language-specification"></a><span data-ttu-id="10937-138">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10937-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10937-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10937-139">See Also</span></span>

- [<span data-ttu-id="10937-140">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10937-140">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="10937-141">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="10937-141">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="10937-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="10937-142">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="10937-143">?: operator</span><span class="sxs-lookup"><span data-stu-id="10937-143">?: Operator</span></span>](../operators/conditional-operator.md)  
- [<span data-ttu-id="10937-144">if-else, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="10937-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)  
- [<span data-ttu-id="10937-145">switch</span><span class="sxs-lookup"><span data-stu-id="10937-145">switch</span></span>](switch.md)  
