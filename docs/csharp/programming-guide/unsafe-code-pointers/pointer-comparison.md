---
title: Porównanie wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 72d9017064959c801bd2702ff585ee16b1592da6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236794"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="8dbb0-102">Porównanie wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8dbb0-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="8dbb0-103">Można zastosować następujących operatorów porównywanie wskaźników dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="8dbb0-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="8dbb0-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="8dbb0-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="8dbb0-105">Operatory porównania Porównaj adresy dwóch argumentów operacji, jak gdyby były liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="8dbb0-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dbb0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="8dbb0-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="8dbb0-107">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8dbb0-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="8dbb0-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dbb0-108">See Also</span></span>

- [<span data-ttu-id="8dbb0-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8dbb0-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8dbb0-110">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="8dbb0-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="8dbb0-111">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8dbb0-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="8dbb0-112">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="8dbb0-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="8dbb0-113">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="8dbb0-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="8dbb0-114">Typy</span><span class="sxs-lookup"><span data-stu-id="8dbb0-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="8dbb0-115">unsafe</span><span class="sxs-lookup"><span data-stu-id="8dbb0-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="8dbb0-116">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8dbb0-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="8dbb0-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8dbb0-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
