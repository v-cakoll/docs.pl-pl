---
title: foreach, in (odwołanie w C#)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="e75dd-102">foreach, in (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e75dd-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="e75dd-103">`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e75dd-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="e75dd-104">`foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="e75dd-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="e75dd-105">ma publiczny bez parametrów `GetEnumerator` metody, których typ zwracany jest klasy, struktury lub typ interfejsu</span><span class="sxs-lookup"><span data-stu-id="e75dd-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="e75dd-106">zwracany typ `GetEnumerator` metoda ma publicznego `Current` właściwości i publiczny bez parametrów `MoveNext` metody, których typem zwracanym jest <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="e75dd-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="e75dd-107">W dowolnym punktu w `foreach` blok instrukcji, można przerwać poza pętli przy użyciu [podziału](break.md) — słowo kluczowe lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e75dd-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span> <span data-ttu-id="e75dd-108">Możesz również zakończyć działanie `foreach` pętli przez [przejdź do](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="e75dd-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="e75dd-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e75dd-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="e75dd-110">W poniższym przykładzie przedstawiono użycie `foreach` instrukcji z wystąpieniem <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="e75dd-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="e75dd-111">W następnym przykładzie użyto `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsami:</span><span class="sxs-lookup"><span data-stu-id="e75dd-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="e75dd-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e75dd-112">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e75dd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e75dd-113">See also</span></span>

[<span data-ttu-id="e75dd-114">Instrukcja foreach (specyfikacja języka C#)</span><span class="sxs-lookup"><span data-stu-id="e75dd-114">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="e75dd-115">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="e75dd-115">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="e75dd-116">for</span><span class="sxs-lookup"><span data-stu-id="e75dd-116">for</span></span>](for.md)  
[<span data-ttu-id="e75dd-117">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="e75dd-117">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="e75dd-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e75dd-118">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="e75dd-119">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="e75dd-119">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="e75dd-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e75dd-120">C# Programming Guide</span></span>](../../programming-guide/index.md)  