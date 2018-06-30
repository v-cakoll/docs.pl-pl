---
title: foreach, in (odwołanie w C#)
ms.date: 06/28/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: e4b5ba6fb97d82d2b6f03e77995b9d3c2b9d68c6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104419"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="ce95b-102">foreach, in (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ce95b-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="ce95b-103">`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce95b-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="ce95b-104">`foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="ce95b-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="ce95b-105">ma publiczny bez parametrów `GetEnumerator` metody, których typ zwracany jest klasy, struktury lub typ interfejsu</span><span class="sxs-lookup"><span data-stu-id="ce95b-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="ce95b-106">zwracany typ `GetEnumerator` metoda ma publicznego `Current` właściwości i publiczny bez parametrów `MoveNext` metody, których typem zwracanym jest <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="ce95b-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="ce95b-107">W dowolnym punktu w `foreach` blok instrukcji, można przerwać poza pętli przy użyciu [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ce95b-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ce95b-108">Możesz również zakończyć działanie `foreach` pętli przez [przejdź do](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="ce95b-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="ce95b-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ce95b-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="ce95b-110">W poniższym przykładzie przedstawiono użycie `foreach` instrukcji z wystąpieniem <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="ce95b-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="ce95b-111">W następnym przykładzie użyto `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsami:</span><span class="sxs-lookup"><span data-stu-id="ce95b-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="ce95b-112">Począwszy od 7.3 C#, gdy typ kolekcji obsługuje `ref` dostęp do swoich elementów można zadeklarować zmiennej iteracji z `ref` lub `ref readonly` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="ce95b-112">Beginning with C# 7.3, when the collection type supports `ref` access to its elements, you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="ce95b-113">W poniższym przykładzie użyto `ref` zmiennej iteracji, aby ustawić wartość każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="ce95b-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="ce95b-114">`ref readonly` Wersji iteruje po kolekcji do wyświetlania wartości.</span><span class="sxs-lookup"><span data-stu-id="ce95b-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="ce95b-115">`readonly` Deklaracja korzysta z niejawnych deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="ce95b-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="ce95b-116">Niejawne deklaracji zmiennych mogą być używane z albo `ref` lub `ref readonly` deklaracje, jak można jawnie wpisana deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="ce95b-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="ce95b-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce95b-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ce95b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce95b-118">See also</span></span>

[<span data-ttu-id="ce95b-119">Instrukcja foreach (specyfikacja języka C#)</span><span class="sxs-lookup"><span data-stu-id="ce95b-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="ce95b-120">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="ce95b-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="ce95b-121">for</span><span class="sxs-lookup"><span data-stu-id="ce95b-121">for</span></span>](for.md)  
[<span data-ttu-id="ce95b-122">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="ce95b-122">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="ce95b-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ce95b-123">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="ce95b-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce95b-124">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="ce95b-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ce95b-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  