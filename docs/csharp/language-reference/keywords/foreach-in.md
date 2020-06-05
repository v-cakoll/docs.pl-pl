---
title: Instrukcja "foreach" języka C#
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401891"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="dd82a-102">foreach, in (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dd82a-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="dd82a-103">`foreach`Instrukcja wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs lub.</span><span class="sxs-lookup"><span data-stu-id="dd82a-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="dd82a-104">`foreach`Instrukcja nie jest ograniczona do tych typów i może być stosowana do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="dd82a-104">The `foreach` statement isn't limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="dd82a-105">ma publiczną metodę bez parametrów `GetEnumerator` , której typem zwracanym jest Klasa, struktura lub typ interfejsu,</span><span class="sxs-lookup"><span data-stu-id="dd82a-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="dd82a-106">zwracany typ `GetEnumerator` metody ma właściwość publiczną `Current` i publiczną metodę bez parametrów, `MoveNext` której typem zwracanym jest <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="dd82a-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="dd82a-107">W większości przypadków, `foreach` iteruje `IEnumerable<T>` wyrażenie, gdzie każdy element jest typu `T` .</span><span class="sxs-lookup"><span data-stu-id="dd82a-107">In most uses, `foreach` iterates an `IEnumerable<T>` expression where each element is of type `T`.</span></span> <span data-ttu-id="dd82a-108">Jednakże elementy mogą być dowolnego typu, który ma niejawną lub jawną konwersję z typu `Current` właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd82a-108">However, the elements may be any type that has an implicit or explicit conversion from the type of the `Current` property.</span></span> <span data-ttu-id="dd82a-109">Jeśli `Current` właściwość zwróci wartość `SomeType` , typem elementów mogą być:</span><span class="sxs-lookup"><span data-stu-id="dd82a-109">If the `Current` property returns `SomeType`, the type of the elements may be:</span></span>

- <span data-ttu-id="dd82a-110">Dowolna z klas bazowych `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="dd82a-110">Any of the base classes of `SomeType`.</span></span>
- <span data-ttu-id="dd82a-111">Wszystkie interfejsy zaimplementowane przez `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="dd82a-111">Any of the interfaces implemented by `SomeType`.</span></span>

<span data-ttu-id="dd82a-112">Ponadto, jeśli `SomeType` jest `class` lub `interface` a i nie `sealed` , typ elementów może obejmować:</span><span class="sxs-lookup"><span data-stu-id="dd82a-112">Furthermore, if `SomeType` is a `class` or an `interface` and not `sealed`, the type of elements may include:</span></span>

- <span data-ttu-id="dd82a-113">Dowolny typ pochodzący od `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="dd82a-113">Any type derived from `SomeType`.</span></span>
- <span data-ttu-id="dd82a-114">Dowolny dowolny interfejs.</span><span class="sxs-lookup"><span data-stu-id="dd82a-114">Any arbitrary interface.</span></span> <span data-ttu-id="dd82a-115">Dowolny interfejs jest dozwolony, ponieważ dowolny interfejs może być zaimplementowany przez klasę pochodną lub implementującą `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="dd82a-115">Any interface is allowed because any interface may be implemented by a class derived from or implementing `SomeType`.</span></span>

<span data-ttu-id="dd82a-116">Można zadeklarować zmienną iteracji przy użyciu dowolnego typu, który jest zgodny z poprzednimi regułami.</span><span class="sxs-lookup"><span data-stu-id="dd82a-116">You may declare the iteration variable using any type that matches the preceding rules.</span></span> <span data-ttu-id="dd82a-117">Jeśli konwersja z `SomeType` do typu zmiennej iteracji wymaga jawnego rzutowania, operacja może zgłosić wyjątek, <xref:System.InvalidCastException> gdy konwersja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="dd82a-117">If the conversion from `SomeType` to the type of the iteration variable requires an explicit cast, that operation may throw an <xref:System.InvalidCastException> when the conversion fails.</span></span>

<span data-ttu-id="dd82a-118">Począwszy od języka C# 7,3, jeśli właściwość modułu wyliczającego `Current` zwróci [wartość zwracaną odwołania](ref.md#reference-return-values) ( `ref T` gdzie `T` jest typem elementu kolekcji), można zadeklarować zmienną iteracji za pomocą `ref` `ref readonly` modyfikatora or.</span><span class="sxs-lookup"><span data-stu-id="dd82a-118">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="dd82a-119">Począwszy od języka C# 8,0, `await` operator może zostać zastosowany do `foreach` instrukcji, gdy typ kolekcji implementuje <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs.</span><span class="sxs-lookup"><span data-stu-id="dd82a-119">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="dd82a-120">Każda iteracja pętli może zostać zawieszona, podczas gdy następny element jest pobierany asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="dd82a-120">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="dd82a-121">Domyślnie elementy strumienia są przetwarzane w przechwyconym kontekście.</span><span class="sxs-lookup"><span data-stu-id="dd82a-121">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="dd82a-122">Jeśli chcesz wyłączyć przechwytywanie kontekstu, użyj <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="dd82a-122">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="dd82a-123">Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [konsumowania wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="dd82a-123">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="dd82a-124">W dowolnym momencie w `foreach` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="dd82a-124">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="dd82a-125">Możesz również wyjść z `foreach` pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="dd82a-125">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="dd82a-126">Jeśli `foreach` instrukcja jest zastosowana do `null` , <xref:System.NullReferenceException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="dd82a-126">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="dd82a-127">Jeśli kolekcja źródłowa `foreach` instrukcji jest pusta, treść `foreach` pętli nie zostanie wykonana i pominięta.</span><span class="sxs-lookup"><span data-stu-id="dd82a-127">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="dd82a-128">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dd82a-128">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="dd82a-129">W poniższym przykładzie pokazano użycie `foreach` instrukcji z wystąpieniem <xref:System.Collections.Generic.List%601> typu implementującego <xref:System.Collections.Generic.IEnumerable%601> Interfejs:</span><span class="sxs-lookup"><span data-stu-id="dd82a-129">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="dd82a-130">W następnym przykładzie używa się `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsów:</span><span class="sxs-lookup"><span data-stu-id="dd82a-130">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="dd82a-131">Poniższy przykład używa `ref` zmiennej iteracji w celu ustawienia wartości każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="dd82a-131">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="dd82a-132">`ref readonly`Wersja wykonuje iterację kolekcji w celu wydrukowania wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="dd82a-132">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="dd82a-133">`readonly`Deklaracja używa niejawnej deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="dd82a-133">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="dd82a-134">Deklaracje zmiennych niejawnych mogą być używane z deklaracjami `ref` lub `ref readonly` , jak można jawnie wpisać deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="dd82a-134">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="dd82a-135">Poniższy przykład używa `await foreach` do iterowania kolekcji, która generuje każdy element asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="dd82a-135">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a><span data-ttu-id="dd82a-136">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dd82a-136">C# language specification</span></span>

<span data-ttu-id="dd82a-137">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="dd82a-137">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd82a-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd82a-138">See also</span></span>

- [<span data-ttu-id="dd82a-139">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="dd82a-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dd82a-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dd82a-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dd82a-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="dd82a-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="dd82a-142">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="dd82a-142">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="dd82a-143">for, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dd82a-143">for statement</span></span>](for.md)
