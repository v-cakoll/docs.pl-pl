---
title: Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 54c439aab8b6cd34a796db8d31f9eabeefddf9f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="bb589-102">Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bb589-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="bb589-103">W tym temacie omówiono przy użyciu operatorów arytmetycznych `+` i  **-**  do manipulowania wskaźników.</span><span class="sxs-lookup"><span data-stu-id="bb589-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb589-104">Nie można wykonać wszystkie operacje arytmetyczne na wskaźnikach void.</span><span class="sxs-lookup"><span data-stu-id="bb589-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="bb589-105">Dodawanie i odejmowanie wartości liczbowe do lub z wskaźników</span><span class="sxs-lookup"><span data-stu-id="bb589-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="bb589-106">Można dodać wartość `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md) do wskaźnika, `p`, dowolnego typu, z wyjątkiem `void*`.</span><span class="sxs-lookup"><span data-stu-id="bb589-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="bb589-107">Wynik `p+n` wskaźnika wynikające z Dodawanie `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="bb589-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="bb589-108">Podobnie `p-n` wskaźnika wynikające z odjęcie `n * sizeof(p)` z adresu `p`.</span><span class="sxs-lookup"><span data-stu-id="bb589-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="bb589-109">Odejmowanie wskaźników</span><span class="sxs-lookup"><span data-stu-id="bb589-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="bb589-110">Można również odjąć wskaźniki tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="bb589-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="bb589-111">Wynik jest zawsze typu `long`.</span><span class="sxs-lookup"><span data-stu-id="bb589-111">The result is always of the type `long`.</span></span> <span data-ttu-id="bb589-112">Na przykład jeśli `p1` i `p2` są wskaźnikami typu `pointer-type*`, następnie wyrażenie `p1-p2` wynikiem:</span><span class="sxs-lookup"><span data-stu-id="bb589-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="bb589-113">Żadne wyjątki są generowane, gdy domeny wskaźnika przepełnienie arytmetyczne operacji, a wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="bb589-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb589-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb589-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb589-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bb589-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb589-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb589-116">See Also</span></span>  
 [<span data-ttu-id="bb589-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bb589-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb589-118">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="bb589-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="bb589-119">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="bb589-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="bb589-120">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="bb589-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="bb589-121">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="bb589-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="bb589-122">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="bb589-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="bb589-123">Typy</span><span class="sxs-lookup"><span data-stu-id="bb589-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="bb589-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="bb589-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="bb589-125">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="bb589-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="bb589-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="bb589-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
