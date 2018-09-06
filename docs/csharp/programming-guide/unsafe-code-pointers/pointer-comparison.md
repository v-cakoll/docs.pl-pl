---
title: Porównanie wskaźników (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: fa980c944159c477c333762ffad569332fba9402
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747635"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="70baf-102">Porównanie wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="70baf-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="70baf-103">Można zastosować następujących operatorów porównywanie wskaźników dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="70baf-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="70baf-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="70baf-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="70baf-105">Operatory porównania Porównaj adresy dwóch argumentów operacji, jak gdyby były liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="70baf-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70baf-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="70baf-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="70baf-107">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="70baf-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="70baf-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70baf-108">See Also</span></span>

- [<span data-ttu-id="70baf-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="70baf-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="70baf-110">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="70baf-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="70baf-111">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="70baf-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="70baf-112">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="70baf-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="70baf-113">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="70baf-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="70baf-114">Typy</span><span class="sxs-lookup"><span data-stu-id="70baf-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="70baf-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="70baf-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="70baf-116">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="70baf-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="70baf-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="70baf-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
