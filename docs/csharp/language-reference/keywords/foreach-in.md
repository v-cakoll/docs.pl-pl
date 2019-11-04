---
title: C#Instrukcja foreach
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422799"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="9c936-102">foreach, in (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="9c936-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="9c936-103">Instrukcja `foreach` wykonuje instrukcję lub blok instrukcji dla każdego elementu w wystąpieniu typu, który implementuje interfejs <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9c936-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="9c936-104">Instrukcje `foreach` nie są ograniczone do tych typów i mogą być stosowane do wystąpienia dowolnego typu, który spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="9c936-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="9c936-105">ma publiczną metodę `GetEnumerator` bez parametrów, której typem zwracanym jest Klasa, struktura lub typ interfejsu,</span><span class="sxs-lookup"><span data-stu-id="9c936-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="9c936-106">zwracany typ metody `GetEnumerator` ma Właściwość Public `Current` i publiczną metodę `MoveNext` bezparametrową, której typem zwracanym jest <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="9c936-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="9c936-107">Począwszy od C# 7,3, jeśli właściwość `Current` modułu wyliczającego zwróci [wartość zwracaną odwołania](ref.md#reference-return-values) (`ref T` gdzie `T` jest typem elementu kolekcji), Zmienna iteracji można zadeklarować za pomocą modyfikatora `ref` lub `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="9c936-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="9c936-108">W dowolnym momencie w bloku instrukcji `foreach` można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="9c936-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="9c936-109">Możesz również wyjść z pętli `foreach` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="9c936-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="9c936-110">Jeśli do `null`zostanie zastosowana instrukcja `foreach`, zostanie zgłoszony <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="9c936-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="9c936-111">Jeśli kolekcja źródłowa instrukcji `foreach` jest pusta, treść pętli `foreach` nie zostanie wykonana i pominięta.</span><span class="sxs-lookup"><span data-stu-id="9c936-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="9c936-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="9c936-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="9c936-113">W poniższym przykładzie pokazano użycie instrukcji `foreach` z wystąpieniem typu <xref:System.Collections.Generic.List%601>, który implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="9c936-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="9c936-114">W następnym przykładzie używamy instrukcji `foreach` z wystąpieniem typu <xref:System.Span%601?displayProperty=nameWithType>, który nie implementuje interfejsów:</span><span class="sxs-lookup"><span data-stu-id="9c936-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="9c936-115">Poniższy przykład używa zmiennej iteracji `ref`, aby ustawić wartość każdego elementu w tablicy stackalloc.</span><span class="sxs-lookup"><span data-stu-id="9c936-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="9c936-116">Wersja `ref readonly` wykonuje iterację kolekcji w celu wydrukowania wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="9c936-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="9c936-117">Deklaracja `readonly` używa niejawnej deklaracji zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="9c936-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="9c936-118">Deklaracje zmiennych niejawnych mogą być używane z deklaracjami `ref` lub `ref readonly`, jak można jawnie wprowadzać deklaracje zmiennych.</span><span class="sxs-lookup"><span data-stu-id="9c936-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="9c936-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9c936-119">C# language specification</span></span>

<span data-ttu-id="9c936-120">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja foreach](~/_csharplang/spec/statements.md#the-foreach-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="9c936-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c936-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c936-121">See also</span></span>

- [<span data-ttu-id="9c936-122">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="9c936-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9c936-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9c936-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9c936-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9c936-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9c936-125">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="9c936-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="9c936-126">for — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c936-126">for statement</span></span>](for.md)
