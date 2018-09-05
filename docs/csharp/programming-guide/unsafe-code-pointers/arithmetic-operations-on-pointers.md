---
title: Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: 3694699466f7a200eecd5eef85f60fa19f9584a8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542196"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="b32f1-102">Operacje arytmetyczne na wskaźnikach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b32f1-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="b32f1-103">W tym temacie omówiono przy użyciu operatorów arytmetycznych `+` i **-** do manipulowania wskaźników.</span><span class="sxs-lookup"><span data-stu-id="b32f1-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b32f1-104">Nie można wykonać wszystkie operacje arytmetyczne na wskaźnikach typu void.</span><span class="sxs-lookup"><span data-stu-id="b32f1-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="b32f1-105">Dodawanie i odejmowanie wartości numerycznych do i z wskaźników</span><span class="sxs-lookup"><span data-stu-id="b32f1-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="b32f1-106">Wartość zostanie dodana `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długie](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md) na wskaźnik `p`, dowolnego typu z wyjątkiem `void*`.</span><span class="sxs-lookup"><span data-stu-id="b32f1-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="b32f1-107">Wynik `p+n` jest wskaźnikiem wynikające z dodawania `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="b32f1-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="b32f1-108">Podobnie `p-n` jest wskaźnikiem wynikające z odjęcie `n * sizeof(p)` z adresu `p`.</span><span class="sxs-lookup"><span data-stu-id="b32f1-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="b32f1-109">Odjęcie wskaźników</span><span class="sxs-lookup"><span data-stu-id="b32f1-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="b32f1-110">Możliwe jest również odjęcie wskaźników tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="b32f1-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="b32f1-111">Wynik jest zawsze typu `long`.</span><span class="sxs-lookup"><span data-stu-id="b32f1-111">The result is always of the type `long`.</span></span> <span data-ttu-id="b32f1-112">Na przykład jeśli `p1` i `p2` są wskaźnikami typu `pointer-type*`, następnie wyrażenie `p1-p2` powoduje:</span><span class="sxs-lookup"><span data-stu-id="b32f1-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="b32f1-113">Żadne wyjątki są generowane, gdy operacja arytmetyczna przepełnienia domeny wskaźnika, a wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="b32f1-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b32f1-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b32f1-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b32f1-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b32f1-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b32f1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b32f1-116">See Also</span></span>

- [<span data-ttu-id="b32f1-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b32f1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b32f1-118">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="b32f1-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="b32f1-119">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="b32f1-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="b32f1-120">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b32f1-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="b32f1-121">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="b32f1-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="b32f1-122">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="b32f1-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="b32f1-123">Typy</span><span class="sxs-lookup"><span data-stu-id="b32f1-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="b32f1-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="b32f1-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="b32f1-125">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b32f1-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="b32f1-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b32f1-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
