---
title: "stackalloc (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="d15a4-102">stackalloc (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d15a4-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="d15a4-103">`stackalloc` — Słowo kluczowe jest używane w kontekście niebezpieczny kod można przydzielić bloku pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="d15a4-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="d15a4-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d15a4-104">Remarks</span></span>  
 <span data-ttu-id="d15a4-105">Słowo kluczowe jest prawidłowy tylko w lokalnej zmiennej inicjatory.</span><span class="sxs-lookup"><span data-stu-id="d15a4-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="d15a4-106">Poniższy kod powoduje, że błędy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d15a4-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="d15a4-107">Ponieważ są związane z typów wskaźnika, `stackalloc` wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d15a4-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="d15a4-108">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d15a4-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="d15a4-109">`stackalloc`przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawcze języka C.</span><span class="sxs-lookup"><span data-stu-id="d15a4-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="d15a4-110">Poniższy przykład oblicza i wyświetla najpierw 20 cyfr w sekwencji Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="d15a4-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="d15a4-111">Każdą liczbę to suma poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="d15a4-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="d15a4-112">W kodzie bloku pamięci wystarczający rozmiar ma 20 elementów typu `int` został przydzielony na stosie nie stosu.</span><span class="sxs-lookup"><span data-stu-id="d15a4-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="d15a4-113">Adres bloku są przechowywane we wskaźniku `fib`.</span><span class="sxs-lookup"><span data-stu-id="d15a4-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="d15a4-114">Ta pamięć nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty (przy użyciu [stałej](../../../csharp/language-reference/keywords/fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="d15a4-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="d15a4-115">Okres istnienia blok pamięci jest ograniczona do istnienia metody, która definiuje ją.</span><span class="sxs-lookup"><span data-stu-id="d15a4-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="d15a4-116">Nie można zwolnić pamięć, przed metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="d15a4-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d15a4-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d15a4-117">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a><span data-ttu-id="d15a4-118">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d15a4-118">Security</span></span>  
 <span data-ttu-id="d15a4-119">Niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod.</span><span class="sxs-lookup"><span data-stu-id="d15a4-119">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="d15a4-120">Jednak użycie `stackalloc` automatycznie włączone funkcje wykrywania przepełnienie buforu w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="d15a4-120">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="d15a4-121">W przypadku wykrycia przepełnienie buforu, proces jest zakończony tak szybko jak to możliwe, aby zminimalizować ryzyko, że złośliwy kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="d15a4-121">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d15a4-122">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d15a4-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d15a4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d15a4-123">See Also</span></span>  
 [<span data-ttu-id="d15a4-124">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d15a4-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d15a4-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d15a4-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d15a4-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d15a4-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d15a4-127">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="d15a4-127">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="d15a4-128">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="d15a4-128">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
