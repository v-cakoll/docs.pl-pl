---
title: Porównanie wskaźników (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: fa980c944159c477c333762ffad569332fba9402
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555513"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="edb46-102">Porównanie wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="edb46-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="edb46-103">Można zastosować następujących operatorów porównywanie wskaźników dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="edb46-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="edb46-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="edb46-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="edb46-105">Operatory porównania Porównaj adresy dwóch argumentów operacji, jak gdyby były liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="edb46-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edb46-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="edb46-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="edb46-107">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="edb46-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="edb46-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edb46-108">See Also</span></span>

- [<span data-ttu-id="edb46-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="edb46-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="edb46-110">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="edb46-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="edb46-111">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="edb46-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="edb46-112">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="edb46-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="edb46-113">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="edb46-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="edb46-114">Typy</span><span class="sxs-lookup"><span data-stu-id="edb46-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="edb46-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="edb46-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="edb46-116">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="edb46-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="edb46-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="edb46-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
