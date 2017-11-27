---
title: "Porównanie wskaźników (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0b45b9152272244b9a0c9d0fa3787973f8f8182a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="e273a-102">Porównanie wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e273a-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="e273a-103">Można użyć następujących operatorów do porównania wskaźniki dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="e273a-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="e273a-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="e273a-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="e273a-105">Operatory porównania porównać adresy dwóch argumentów operacji, ponieważ, jeśli są one liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="e273a-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e273a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e273a-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="e273a-107">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="e273a-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="e273a-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e273a-108">See Also</span></span>  
 [<span data-ttu-id="e273a-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e273a-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e273a-110">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="e273a-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="e273a-111">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="e273a-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="e273a-112">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="e273a-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="e273a-113">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="e273a-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="e273a-114">Typy</span><span class="sxs-lookup"><span data-stu-id="e273a-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="e273a-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="e273a-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="e273a-116">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e273a-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="e273a-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="e273a-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
