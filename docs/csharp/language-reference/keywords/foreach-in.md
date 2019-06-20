---
title: Instrukcja foreach języka C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: af4850b4c33727c818fb5a67d17fb6146627fa06
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267737"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="43602-102">Instrukcja foreach w (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="43602-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="43602-103">`foreach` Instrukcji wykonuje instrukcję lub blok instrukcji dla każdego elementu w określonym wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="43602-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="43602-104">`foreach` Instrukcja nie jest ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="43602-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="43602-105">ma publiczny bez parametrów `GetEnumerator` metody, którego typem zwracanym jest klasy, struktury lub typ interfejsu</span><span class="sxs-lookup"><span data-stu-id="43602-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="43602-106">zwracany typ `GetEnumerator` metoda ma publiczny `Current` właściwość i publiczny bez parametrów `MoveNext` metody, którego typem zwracanym jest <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="43602-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="43602-107">Począwszy od C# 7.3, jeśli moduł wyliczający `Current` właściwość zwraca [odwoływać się do wartości zwracanej](ref.md#reference-return-values) (`ref T` gdzie `T` jest typ elementu kolekcji), można zadeklarować zmiennej iteracji `ref` lub `ref readonly` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="43602-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="43602-108">W dowolnym punkcie w `foreach` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli za pomocą [nadal](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43602-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="43602-109">Możesz również wyjść `foreach` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43602-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="43602-110">Jeśli `foreach` instrukcji jest stosowany do `null`, <xref:System.NullReferenceException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="43602-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="43602-111">Jeśli źródło zbiór `foreach` instrukcja jest pusta, treść `foreach` pętli nie jest wykonywane i pominięte.</span><span class="sxs-lookup"><span data-stu-id="43602-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="43602-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="43602-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="43602-113">W poniższym przykładzie pokazano użycie `foreach` instrukcję, określając wystąpienie <xref:System.Collections.Generic.List%601> typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="43602-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="43602-114">W następnym przykładzie użyto `foreach` instrukcję, określając wystąpienie <xref:System.Span%601?displayProperty=nameWithType> typ, który nie implementuje żadnych interfejsów:</span><span class="sxs-lookup"><span data-stu-id="43602-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="43602-115">W poniższym przykładzie użyto `ref` Zmienna iteracji można ustawić wartości dla każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="43602-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="43602-116">`ref readonly` Wersji iteruje po kolekcji do wyświetlania wartości.</span><span class="sxs-lookup"><span data-stu-id="43602-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="43602-117">`readonly` Deklaracji używa niejawne deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="43602-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="43602-118">Niejawne deklaracje zmiennej może być używany z albo `ref` lub `ref readonly` deklaracji, jak można jawnie wpisane deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="43602-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="43602-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="43602-119">C# language specification</span></span>

<span data-ttu-id="43602-120">Aby uzyskać więcej informacji, zobacz [Instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="43602-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43602-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43602-121">See also</span></span>

- [<span data-ttu-id="43602-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="43602-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43602-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="43602-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43602-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="43602-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="43602-125">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="43602-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="43602-126">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="43602-126">for statement</span></span>](for.md)
