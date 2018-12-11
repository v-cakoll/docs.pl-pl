---
title: słowo kluczowe stackalloc — C# odwołania
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 31fdbacb01d1f6052c86d40c0bffc903130f216c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245512"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="2fcd3-102">stackalloc (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2fcd3-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="2fcd3-103">`stackalloc` Słowo kluczowe jest używane w kontekście niebezpieczny kod można przydzielić blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="2fcd3-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fcd3-104">Remarks</span></span>

<span data-ttu-id="2fcd3-105">Słowo kluczowe jest prawidłowy tylko w inicjatorach zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="2fcd3-106">Poniższy kod powoduje błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="2fcd3-107">Począwszy od języka C# 7.3, można użyć składni inicjatora tablicy dla `stackalloc` tablic.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="2fcd3-108">Następujące deklaracje jest zadeklarowanie tablicy za pomocą trzech elementów, których wartości są liczbami całkowitymi `1`, `2`, i `3`:</span><span class="sxs-lookup"><span data-stu-id="2fcd3-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="2fcd3-109">Ponieważ typy wskaźników, `stackalloc` wymaga [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="2fcd3-110">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="2fcd3-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="2fcd3-111">`stackalloc` przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawczej C.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="2fcd3-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2fcd3-112">Examples</span></span>

<span data-ttu-id="2fcd3-113">Poniższy przykład oblicza i wyświetla pierwszych 20 cyfr w sekwencji Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="2fcd3-114">Każdy numer to suma poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="2fcd3-115">W kodzie, blok pamięci wystarczająco duży, aby zawierała 20 elementów typu `int` jest przydzielony na stosie nie sterty.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="2fcd3-116">Adres bloku jest przechowywany we wskaźniku `fib`.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="2fcd3-117">Ta pamięć nie podlega wyrzucania elementów bezużytecznych i w związku z tym nie trzeba przypiąć (przy użyciu [stałej](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="2fcd3-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="2fcd3-118">Okres istnienia blok pamięci jest ograniczona do okresu istnienia metody, który go definiuje.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="2fcd3-119">Nie można zwolnić pamięć, przed powrotem z metody.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="2fcd3-120">Poniższy przykład inicjuje `stackalloc` tablica liczb całkowitych do maski bitowej o jeden bit ustawiona w każdym elemencie.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="2fcd3-121">W tym przykładzie pokazano, jak nowa składnia inicjatora dostępnych w języku C# 7.3:</span><span class="sxs-lookup"><span data-stu-id="2fcd3-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="2fcd3-122">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="2fcd3-122">Security</span></span>

<span data-ttu-id="2fcd3-123">Niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="2fcd3-124">Jednak użycie `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu, w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="2fcd3-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="2fcd3-125">W przypadku wykrycia przepełnienie buforu tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo, że złośliwy kod jest wykonywany zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="2fcd3-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2fcd3-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2fcd3-126">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2fcd3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fcd3-127">See also</span></span>

- [<span data-ttu-id="2fcd3-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2fcd3-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="2fcd3-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2fcd3-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2fcd3-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2fcd3-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="2fcd3-131">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="2fcd3-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
- [<span data-ttu-id="2fcd3-132">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="2fcd3-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)