---
title: słowo kluczowe stackalloc — C# odwołania
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 61a27e777a1919a2a6fc5140a311835a8f3daba9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660713"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="05162-102">stackalloc (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="05162-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="05162-103">`stackalloc` — Słowo kluczowe jest używany do alokowania blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="05162-103">The `stackalloc` keyword is used to allocate a block of memory on the stack.</span></span>

```csharp
Span<int> block = stackalloc int[100];
```

<span data-ttu-id="05162-104">Przypisywanie przydzielonego bloku <xref:System.Span%601?displayName=nameWithType> zamiast `int*` umożliwia twórz stos z alokacji w bezpiecznym bloku.</span><span class="sxs-lookup"><span data-stu-id="05162-104">Assigning the allocated block to a <xref:System.Span%601?displayName=nameWithType> instead of an `int*` allows stack allocations in a safe block.</span></span> <span data-ttu-id="05162-105">`unsafe` Kontekst nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="05162-105">The `unsafe` context is not required.</span></span>

## <a name="remarks"></a><span data-ttu-id="05162-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05162-106">Remarks</span></span>

<span data-ttu-id="05162-107">Słowo kluczowe jest prawidłowy tylko w inicjatorach zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="05162-107">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="05162-108">Poniższy kod powoduje błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="05162-108">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

<span data-ttu-id="05162-109">Począwszy od języka C# 7.3, można użyć składni inicjatora tablicy dla `stackalloc` tablic.</span><span class="sxs-lookup"><span data-stu-id="05162-109">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="05162-110">Następujące deklaracje jest zadeklarowanie tablicy za pomocą trzech elementów, których wartości są liczbami całkowitymi `1`, `2`, i `3`.</span><span class="sxs-lookup"><span data-stu-id="05162-110">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`.</span></span> <span data-ttu-id="05162-111">Drugi inicjowania przypisuje pamięci, aby <xref:System.ReadOnlySpan%601>, wskazujący, że pamięć nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="05162-111">The second initialization assigns the memory to a <xref:System.ReadOnlySpan%601>, indicating that the memory cannot be modified.</span></span>

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="05162-112">W przypadku typów wskaźnika `stackalloc` wymaga [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="05162-112">When pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="05162-113">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="05162-113">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="05162-114">`stackalloc` przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawczej C.</span><span class="sxs-lookup"><span data-stu-id="05162-114">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="05162-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="05162-115">Examples</span></span>

<span data-ttu-id="05162-116">Poniższy przykład oblicza i wyświetla pierwszych 20 cyfr w sekwencji Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="05162-116">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="05162-117">Każdy numer to suma poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="05162-117">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="05162-118">W kodzie, blok pamięci wystarczająco duży, aby zawierała 20 elementów typu `int` jest przydzielony na stosie nie sterty.</span><span class="sxs-lookup"><span data-stu-id="05162-118">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="05162-119">Adres bloku są przechowywane w `Span` `fib`.</span><span class="sxs-lookup"><span data-stu-id="05162-119">The address of the block is stored in the `Span` `fib`.</span></span> <span data-ttu-id="05162-120">Ta pamięć nie podlega wyrzucania elementów bezużytecznych i w związku z tym nie trzeba przypiąć (przy użyciu [stałej](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="05162-120">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="05162-121">Okres istnienia blok pamięci jest ograniczona do okresu istnienia metody, który go definiuje.</span><span class="sxs-lookup"><span data-stu-id="05162-121">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="05162-122">Nie można zwolnić pamięć, przed powrotem z metody.</span><span class="sxs-lookup"><span data-stu-id="05162-122">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="05162-123">Poniższy przykład inicjuje `stackalloc` tablica liczb całkowitych do maski bitowej o jeden bit ustawiona w każdym elemencie.</span><span class="sxs-lookup"><span data-stu-id="05162-123">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="05162-124">W tym przykładzie pokazano, jak nowa składnia inicjatora dostępnych w języku C# 7.3:</span><span class="sxs-lookup"><span data-stu-id="05162-124">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="05162-125">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="05162-125">Security</span></span>

<span data-ttu-id="05162-126">Należy używać <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> Jeśli to możliwe, ponieważ niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod.</span><span class="sxs-lookup"><span data-stu-id="05162-126">You should use <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> when possible because unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="05162-127">Nawet wtedy, gdy jest używane z wskaźników, użycie `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu, w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="05162-127">Even when used with pointers, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="05162-128">W przypadku wykrycia przepełnienie buforu tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo, że złośliwy kod jest wykonywany zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="05162-128">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="05162-129">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05162-129">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="05162-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05162-130">See also</span></span>

- [<span data-ttu-id="05162-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05162-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05162-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="05162-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05162-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="05162-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="05162-134">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="05162-134">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="05162-135">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="05162-135">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
