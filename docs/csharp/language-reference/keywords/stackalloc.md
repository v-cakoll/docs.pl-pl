---
title: stackalloc (odwołanie w C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4cde254bb6a5601d10619c4a3bd2f00f1f146d3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="8d294-102">stackalloc (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8d294-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="8d294-103">`stackalloc` — Słowo kluczowe jest używane w kontekście niebezpieczny kod można przydzielić bloku pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="8d294-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="8d294-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d294-104">Remarks</span></span>

<span data-ttu-id="8d294-105">Słowo kluczowe jest prawidłowy tylko w lokalnej zmiennej inicjatory.</span><span class="sxs-lookup"><span data-stu-id="8d294-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="8d294-106">Poniższy kod powoduje, że błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="8d294-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="8d294-107">Począwszy od 7.3 C#, można użyć składni inicjatora tablicy dla `stackalloc` tablic.</span><span class="sxs-lookup"><span data-stu-id="8d294-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="8d294-108">Następujące deklaracje zadeklarować tablicę z trzech elementów, których wartości są liczby całkowite `1`, `2`, i `3`:</span><span class="sxs-lookup"><span data-stu-id="8d294-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="8d294-109">Ponieważ są związane z typów wskaźnika, `stackalloc` wymaga [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8d294-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="8d294-110">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="8d294-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="8d294-111">`stackalloc` przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawcze języka C.</span><span class="sxs-lookup"><span data-stu-id="8d294-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="8d294-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8d294-112">Examples</span></span>

<span data-ttu-id="8d294-113">Poniższy przykład oblicza i wyświetla najpierw 20 cyfr w sekwencji Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="8d294-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="8d294-114">Każdą liczbę to suma poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="8d294-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="8d294-115">W kodzie bloku pamięci wystarczający rozmiar ma 20 elementów typu `int` został przydzielony na stosie nie stosu.</span><span class="sxs-lookup"><span data-stu-id="8d294-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="8d294-116">Adres bloku są przechowywane we wskaźniku `fib`.</span><span class="sxs-lookup"><span data-stu-id="8d294-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="8d294-117">Ta pamięć nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty (przy użyciu [stałej](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="8d294-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="8d294-118">Okres istnienia blok pamięci jest ograniczona do istnienia metody, która definiuje ją.</span><span class="sxs-lookup"><span data-stu-id="8d294-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="8d294-119">Nie można zwolnić pamięć, przed metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="8d294-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="8d294-120">W poniższym przykładzie inicjowane `stackalloc` tablica liczb całkowitych na maska bitowa o jeden bit, ustaw w każdym elemencie.</span><span class="sxs-lookup"><span data-stu-id="8d294-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="8d294-121">Oznacza to, nowej składni inicjatora dostępne począwszy od 7.3 C#:</span><span class="sxs-lookup"><span data-stu-id="8d294-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="8d294-122">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="8d294-122">Security</span></span>

<span data-ttu-id="8d294-123">Niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod.</span><span class="sxs-lookup"><span data-stu-id="8d294-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="8d294-124">Jednak użycie `stackalloc` automatycznie włączone funkcje wykrywania przepełnienie buforu w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="8d294-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="8d294-125">W przypadku wykrycia przepełnienie buforu, proces jest zakończony tak szybko jak to możliwe, aby zminimalizować ryzyko, że złośliwy kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="8d294-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d294-126">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8d294-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8d294-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d294-127">See Also</span></span>
 [<span data-ttu-id="8d294-128">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8d294-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8d294-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8d294-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8d294-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8d294-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8d294-131">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="8d294-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="8d294-132">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="8d294-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
