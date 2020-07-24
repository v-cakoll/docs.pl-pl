---
title: Instrukcja "foreach" języka C#
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 4af431d29e538c1516efeaad3008eaa3b2229ece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104244"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="1c9e8-102">foreach, in (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1c9e8-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="1c9e8-103">`foreach`Instrukcja wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs lub, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="1c9e8-104">`foreach`Instrukcja nie jest ograniczona do tych typów.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-104">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="1c9e8-105">Można jej użyć z wystąpieniem dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-105">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="1c9e8-106">Typ ma publiczną metodę bez parametrów `GetEnumerator` , której typem zwracanym jest Klasa, struktura lub typ interfejsu,</span><span class="sxs-lookup"><span data-stu-id="1c9e8-106">a type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="1c9e8-107">zwracany typ `GetEnumerator` metody ma właściwość publiczną `Current` i publiczną metodę bez parametrów, `MoveNext` której typem zwracanym jest <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-107">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="1c9e8-108">Poniższy przykład używa `foreach` instrukcji z wystąpieniem <xref:System.Span%601?displayProperty=nameWithType> typu, który nie implementuje interfejsów:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-108">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="1c9e8-109">Począwszy od języka C# 7,3, jeśli właściwość modułu wyliczającego `Current` zwróci [wartość zwracaną odwołania](ref.md#reference-return-values) ( `ref T` gdzie `T` jest typem elementu kolekcji), można zadeklarować zmienną iteracji z `ref` `ref readonly` modyfikatorem or, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-109">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="1c9e8-110">Począwszy od języka C# 8,0, można użyć `await foreach` instrukcji, aby wykorzystać asynchroniczny strumień danych, czyli typ kolekcji implementującej <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-110">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="1c9e8-111">Każda iteracja pętli może zostać zawieszona, podczas gdy następny element jest pobierany asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-111">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="1c9e8-112">Poniższy przykład pokazuje, jak używać `await foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-112">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="1c9e8-113">Domyślnie elementy strumienia są przetwarzane w przechwyconym kontekście.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-113">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="1c9e8-114">Jeśli chcesz wyłączyć przechwytywanie kontekstu, użyj <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-114">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="1c9e8-115">Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz [Używanie wzorca asynchronicznego opartego na zadaniach](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-115">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="1c9e8-116">Aby uzyskać więcej informacji o strumieniach asynchronicznych, zobacz sekcję " [strumienie asynchroniczne](../../whats-new/csharp-8.md#asynchronous-streams) " [w artykule Co nowego w języku C# 8,0](../../whats-new/csharp-8.md) .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-116">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="1c9e8-117">W dowolnym momencie w `foreach` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-117">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="1c9e8-118">Możesz również wyjść z `foreach` pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-118">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="1c9e8-119">Jeśli `foreach` instrukcja jest zastosowana do `null` , <xref:System.NullReferenceException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-119">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="1c9e8-120">Jeśli kolekcja źródłowa `foreach` instrukcji jest pusta, treść `foreach` pętli nie zostanie wykonana i pominięta.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-120">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="1c9e8-121">Typ zmiennej iteracji</span><span class="sxs-lookup"><span data-stu-id="1c9e8-121">Type of an iteration variable</span></span>

<span data-ttu-id="1c9e8-122">Możesz użyć `var` słowa kluczowego, aby zezwolić kompilatorowi na wnioskowanie typu zmiennej iteracji w `foreach` instrukcji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-122">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="1c9e8-123">Można również jawnie określić typ zmiennej iteracji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="1c9e8-123">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="1c9e8-124">W poprzednim formularzu typ `T` elementu kolekcji musi być niejawnie lub jawnie konwertowany na typ `V` zmiennej iteracji.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-124">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="1c9e8-125">Jeśli jawna konwersja z elementu `T` do `V` nie powiedzie się w czasie wykonywania, `foreach` instrukcja zgłosi <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-125">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="1c9e8-126">Na przykład, jeśli `T` jest typem klasy niezapieczętowanej, `V` może być dowolnego typu interfejsu, nawet tego, który `T` nie implementuje.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-126">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="1c9e8-127">W czasie wykonywania, typ elementu kolekcji może być tym, który pochodzi od `T` i faktycznie implementuje `V` .</span><span class="sxs-lookup"><span data-stu-id="1c9e8-127">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="1c9e8-128">Jeśli tak się nie dzieje, <xref:System.InvalidCastException> jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="1c9e8-128">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c9e8-129">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1c9e8-129">C# language specification</span></span>

<span data-ttu-id="1c9e8-130">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1c9e8-130">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c9e8-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c9e8-131">See also</span></span>

- [<span data-ttu-id="1c9e8-132">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1c9e8-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1c9e8-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1c9e8-133">C# keywords</span></span>](index.md)
- [<span data-ttu-id="1c9e8-134">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="1c9e8-134">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="1c9e8-135">for, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1c9e8-135">for statement</span></span>](for.md)
