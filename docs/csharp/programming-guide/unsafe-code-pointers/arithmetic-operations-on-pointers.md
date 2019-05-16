---
title: Operacje arytmetyczne na wskaźnikach - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b08f9dbf8137e483bd38a4f396732191598532cf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635232"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="8f823-102">Operacje arytmetyczne na wskaźnikach (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="8f823-102">Arithmetic operations on pointers (C# Programming Guide)</span></span>
<span data-ttu-id="8f823-103">W tym temacie omówiono przy użyciu operatorów arytmetycznych `+` i `-` do manipulowania wskaźników.</span><span class="sxs-lookup"><span data-stu-id="8f823-103">This topic discusses using the arithmetic operators `+` and `-` to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f823-104">Nie można wykonać wszystkie operacje arytmetyczne na wskaźnikach typu void.</span><span class="sxs-lookup"><span data-stu-id="8f823-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="8f823-105">Dodawanie i odejmowanie wartości numerycznych do i z wskaźników</span><span class="sxs-lookup"><span data-stu-id="8f823-105">Adding and subtracting numeric values to or from pointers</span></span>  
 <span data-ttu-id="8f823-106">Wartość zostanie dodana `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długie](../../../csharp/language-reference/keywords/long.md), lub [ulong](../../../csharp/language-reference/keywords/ulong.md) do wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="8f823-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer.</span></span> <span data-ttu-id="8f823-107">Jeśli `p` jest wskaźnikiem typu `pointer-type*`, wynik `p+n` jest wskaźnikiem wynikające z dodawania `n * sizeof(pointer-type)` adres `p`.</span><span class="sxs-lookup"><span data-stu-id="8f823-107">If `p` is a pointer of the type `pointer-type*`, the result `p+n` is the pointer resulting from adding `n * sizeof(pointer-type)` to the address of `p`.</span></span> <span data-ttu-id="8f823-108">Podobnie `p-n` jest wskaźnikiem wynikające z odjęcie `n * sizeof(pointer-type)` z adresu `p`.</span><span class="sxs-lookup"><span data-stu-id="8f823-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(pointer-type)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="8f823-109">Odjęcie wskaźników</span><span class="sxs-lookup"><span data-stu-id="8f823-109">Subtracting pointers</span></span>  
 <span data-ttu-id="8f823-110">Możliwe jest również odjęcie wskaźników tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="8f823-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="8f823-111">Wynik jest zawsze typu `long`.</span><span class="sxs-lookup"><span data-stu-id="8f823-111">The result is always of the type `long`.</span></span> <span data-ttu-id="8f823-112">Na przykład jeśli `p1` i `p2` są wskaźnikami typu `pointer-type*`, następnie wyrażenie `p1-p2` powoduje:</span><span class="sxs-lookup"><span data-stu-id="8f823-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 <span data-ttu-id="8f823-113">Żadne wyjątki są generowane, gdy operacja arytmetyczna przepełnienia domeny wskaźnika, a wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="8f823-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f823-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f823-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8f823-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8f823-115">C# language specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f823-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f823-116">See also</span></span>

- [<span data-ttu-id="8f823-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8f823-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8f823-118">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="8f823-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="8f823-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8f823-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="8f823-120">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="8f823-120">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [<span data-ttu-id="8f823-121">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="8f823-121">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="8f823-122">Typy</span><span class="sxs-lookup"><span data-stu-id="8f823-122">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="8f823-123">unsafe</span><span class="sxs-lookup"><span data-stu-id="8f823-123">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="8f823-124">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8f823-124">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="8f823-125">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8f823-125">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
