---
title: Porównanie wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 25bc1c7b701c36d2daf1918986eb6a8e56980990
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635134"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="7140b-102">Porównanie wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7140b-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="7140b-103">Można zastosować następujących operatorów porównywanie wskaźników dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="7140b-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="7140b-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="7140b-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="7140b-105">Operatory porównania Porównaj adresy dwóch argumentów operacji, jak gdyby były liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="7140b-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7140b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7140b-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a><span data-ttu-id="7140b-107">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7140b-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="7140b-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7140b-108">See also</span></span>

- [<span data-ttu-id="7140b-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7140b-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7140b-110">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="7140b-110">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="7140b-111">Manipulowanie wskaźnikami</span><span class="sxs-lookup"><span data-stu-id="7140b-111">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [<span data-ttu-id="7140b-112">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="7140b-112">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="7140b-113">Typy</span><span class="sxs-lookup"><span data-stu-id="7140b-113">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="7140b-114">unsafe</span><span class="sxs-lookup"><span data-stu-id="7140b-114">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="7140b-115">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7140b-115">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="7140b-116">stackalloc</span><span class="sxs-lookup"><span data-stu-id="7140b-116">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
