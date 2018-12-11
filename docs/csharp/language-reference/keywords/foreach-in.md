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
ms.openlocfilehash: 417a8cefbc9bc7544ae1156992e6e6c549fb828f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128625"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="18eb5-102">Instrukcja foreach w (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="18eb5-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="18eb5-103">`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w określonym wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="18eb5-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="18eb5-104">`foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="18eb5-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="18eb5-105">ma publiczny bez parametrów `GetEnumerator` metody, którego typem zwracanym jest klasy, struktury lub typ interfejsu</span><span class="sxs-lookup"><span data-stu-id="18eb5-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="18eb5-106">zwracany typ `GetEnumerator` metoda ma publiczny `Current` właściwość i publiczny bez parametrów `MoveNext` metody, którego typem zwracanym jest <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="18eb5-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="18eb5-107">Począwszy od C# 7.3, jeśli moduł wyliczający `Current` właściwość zwraca [odwoływać się do wartości zwracanej](ref.md#reference-return-values) (`ref T` gdzie `T` jest typ elementu kolekcji), można zadeklarować zmiennej iteracji `ref` lub `ref readonly` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="18eb5-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="18eb5-108">W dowolnym punkcie w `foreach` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli za pomocą [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="18eb5-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="18eb5-109">Możesz również wyjść `foreach` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="18eb5-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="18eb5-110">Przykłady</span><span class="sxs-lookup"><span data-stu-id="18eb5-110">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="18eb5-111">W poniższym przykładzie pokazano użycie `foreach` instrukcję, określając wystąpienie <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="18eb5-111">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="18eb5-112">W następnym przykładzie użyto `foreach` instrukcję, określając wystąpienie <xref:System.Span%601?displayProperty=nameWithType> typ, który nie implementuje żadnych interfejsów:</span><span class="sxs-lookup"><span data-stu-id="18eb5-112">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="18eb5-113">W poniższym przykładzie użyto `ref` Zmienna iteracji można ustawić wartości dla każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="18eb5-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="18eb5-114">`ref readonly` Wersji iteruje po kolekcji do wyświetlania wartości.</span><span class="sxs-lookup"><span data-stu-id="18eb5-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="18eb5-115">`readonly` Deklaracji używa niejawne deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="18eb5-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="18eb5-116">Niejawne deklaracje zmiennej może być używany z albo `ref` lub `ref readonly` deklaracji, jak można jawnie wpisane deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="18eb5-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="18eb5-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="18eb5-117">C# language specification</span></span>

<span data-ttu-id="18eb5-118">Aby uzyskać więcej informacji, zobacz [Instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="18eb5-118">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="18eb5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18eb5-119">See also</span></span>

- [<span data-ttu-id="18eb5-120">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="18eb5-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="18eb5-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="18eb5-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="18eb5-122">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="18eb5-122">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="18eb5-123">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="18eb5-123">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="18eb5-124">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="18eb5-124">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="18eb5-125">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="18eb5-125">for statement</span></span>](for.md)
