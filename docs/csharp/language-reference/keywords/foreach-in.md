---
title: Instrukcja foreach języka C#
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d84c68eb102d55b31ba20a6b6b5c01b96963924d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524252"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="93abb-102">Instrukcja foreach w (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="93abb-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="93abb-103">`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w określonym wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="93abb-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="93abb-104">`foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="93abb-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="93abb-105">ma publiczny bez parametrów `GetEnumerator` metody, którego typem zwracanym jest klasy, struktury lub typ interfejsu</span><span class="sxs-lookup"><span data-stu-id="93abb-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="93abb-106">zwracany typ `GetEnumerator` metoda ma publiczny `Current` właściwość i publiczny bez parametrów `MoveNext` metody, którego typem zwracanym jest <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="93abb-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="93abb-107">W dowolnym punkcie w `foreach` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli za pomocą [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="93abb-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="93abb-108">Możesz również wyjść `foreach` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="93abb-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="93abb-109">Przykłady</span><span class="sxs-lookup"><span data-stu-id="93abb-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="93abb-110">W poniższym przykładzie pokazano użycie `foreach` instrukcję, określając wystąpienie <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="93abb-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="93abb-111">W następnym przykładzie użyto `foreach` instrukcję, określając wystąpienie <xref:System.Span%601?displayProperty=nameWithType> typ, który nie implementuje żadnych interfejsów:</span><span class="sxs-lookup"><span data-stu-id="93abb-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="93abb-112">Począwszy od C# 7.3, jeśli moduł wyliczający `Current` właściwość zwraca [odwoływać się do wartości zwracanej](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` gdzie `T` jest typ elementu kolekcji), można zadeklarować zmiennej iteracji `ref` lub `ref readonly` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="93abb-112">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="93abb-113">W poniższym przykładzie użyto `ref` Zmienna iteracji można ustawić wartości dla każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="93abb-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="93abb-114">`ref readonly` Wersji iteruje po kolekcji do wyświetlania wartości.</span><span class="sxs-lookup"><span data-stu-id="93abb-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="93abb-115">`readonly` Deklaracji używa niejawne deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="93abb-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="93abb-116">Niejawne deklaracje zmiennej może być używany z albo `ref` lub `ref readonly` deklaracji, jak można jawnie wpisane deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="93abb-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="93abb-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="93abb-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="93abb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93abb-118">See also</span></span>

- [<span data-ttu-id="93abb-119">Instrukcja foreach (specyfikacja języka C#)</span><span class="sxs-lookup"><span data-stu-id="93abb-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)
- [<span data-ttu-id="93abb-120">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="93abb-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="93abb-121">for</span><span class="sxs-lookup"><span data-stu-id="93abb-121">for</span></span>](for.md)
- [<span data-ttu-id="93abb-122">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="93abb-122">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="93abb-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="93abb-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="93abb-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="93abb-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="93abb-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="93abb-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
