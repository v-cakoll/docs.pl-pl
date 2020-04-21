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
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738814"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="2ebbd-102">foreach, w (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="2ebbd-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="2ebbd-103">Instrukcja `foreach` wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> typu, który implementuje lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="2ebbd-104">Instrukcja `foreach` nie jest ograniczona do tych typów i może być stosowana do wystąpienia dowolnego typu, które spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="2ebbd-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="2ebbd-105">ma publiczną `GetEnumerator` metodę bez parametrów, której typem zwracanym jest klasa, struktura lub typ interfejsu,</span><span class="sxs-lookup"><span data-stu-id="2ebbd-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="2ebbd-106">typ zwracany `GetEnumerator` metody ma `Current` właściwość publiczną `MoveNext` i metodę public <xref:System.Boolean>bez parametrów, której typem zwracanym jest .</span><span class="sxs-lookup"><span data-stu-id="2ebbd-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="2ebbd-107">Począwszy od języka C# 7.3, jeśli `Current` właściwość wyliczacza zwraca [wartość zwracaną odwołanie](ref.md#reference-return-values) (gdzie`ref T` `T` jest typem `ref` `ref readonly` elementu kolekcji), można zadeklarować zmienną iteracji za pomocą lub modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="2ebbd-108">Począwszy od języka C# 8.0, `await` operator `foreach` może być stosowany do <xref:System.Collections.Generic.IAsyncEnumerable%601> instrukcji, gdy typ kolekcji implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-108">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="2ebbd-109">Każda iteracja pętli może zostać zawieszona, podczas gdy następny element jest pobierany asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-109">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="2ebbd-110">Domyślnie elementy strumienia są przetwarzane w kontekście przechwycone.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-110">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="2ebbd-111">Jeśli chcesz wyłączyć przechwytywanie kontekstu, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> użyj metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-111">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="2ebbd-112">Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [korzystania z wzorca asynchronicznego opartego](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniach .</span><span class="sxs-lookup"><span data-stu-id="2ebbd-112">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="2ebbd-113">W dowolnym momencie w bloku `foreach` instrukcji można wyrwać z pętli przy użyciu [break](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [continue](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-113">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="2ebbd-114">Można również wyjść `foreach` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-114">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="2ebbd-115">Jeśli `foreach` instrukcja jest `null`stosowana <xref:System.NullReferenceException> do , a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-115">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="2ebbd-116">Jeśli kolekcja źródło `foreach` instrukcji jest pusta, `foreach` treść pętli nie jest wykonywana i pomijana.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-116">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="2ebbd-117">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2ebbd-117">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="2ebbd-118">Poniższy przykład pokazuje `foreach` użycie instrukcji z <xref:System.Collections.Generic.List%601> wystąpieniem typu, <xref:System.Collections.Generic.IEnumerable%601> który implementuje interfejs:</span><span class="sxs-lookup"><span data-stu-id="2ebbd-118">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="2ebbd-119">W następnym przykładzie `foreach` użyto instrukcji <xref:System.Span%601?displayProperty=nameWithType> z wystąpieniem typu, które nie implementuje żadnych interfejsów:</span><span class="sxs-lookup"><span data-stu-id="2ebbd-119">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="2ebbd-120">W poniższym przykładzie użyto zmiennej `ref` iteracji, aby ustawić wartość każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-120">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="2ebbd-121">Wersja `ref readonly` iteruje kolekcji, aby wydrukować wszystkie wartości.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-121">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="2ebbd-122">Deklaracja `readonly` używa niejawnej deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-122">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="2ebbd-123">Niejawne deklaracje zmiennych `ref` mogą `ref readonly` być używane z deklaracjami lub deklaracjami, podobnie jak jawnie wpisane deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-123">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

<span data-ttu-id="2ebbd-124">Poniższy `await foreach` przykład używa do iteracji kolekcji, która generuje każdy element asynchronicznie:</span><span class="sxs-lookup"><span data-stu-id="2ebbd-124">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a><span data-ttu-id="2ebbd-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2ebbd-125">C# language specification</span></span>

<span data-ttu-id="2ebbd-126">Aby uzyskać więcej informacji, zobacz [foreach instrukcji](~/_csharplang/spec/statements.md#the-foreach-statement) sekcji [specyfikacji języka języka C #,](/dotnet/csharp/language-reference/language-specification/introduction)aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="2ebbd-126">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ebbd-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ebbd-127">See also</span></span>

- [<span data-ttu-id="2ebbd-128">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="2ebbd-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2ebbd-129">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="2ebbd-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2ebbd-130">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2ebbd-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2ebbd-131">Korzystanie z foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="2ebbd-131">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="2ebbd-132">dla oświadczenia</span><span class="sxs-lookup"><span data-stu-id="2ebbd-132">for statement</span></span>](for.md)
