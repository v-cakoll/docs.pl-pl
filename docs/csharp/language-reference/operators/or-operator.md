---
title: '| — Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 374adc30e6937a68d67bfae152f2546c854b829b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cfd4a-102">| — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cfd4a-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="cfd4a-103">Binarny `|` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="cfd4a-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="cfd4a-104">W przypadku typów całkowitych `|` oblicza wartości bitowe lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="cfd4a-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="cfd4a-105">Dla `bool` argumentów operacji, `|` logiczne lub z argumentów; oblicza wynik jest `false` tylko wtedy, gdy są obie argumentów `false`.</span><span class="sxs-lookup"><span data-stu-id="cfd4a-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfd4a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfd4a-106">Remarks</span></span>  
 <span data-ttu-id="cfd4a-107">Typy definiowane przez użytkownika można przeciążać `|` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="cfd4a-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfd4a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfd4a-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cfd4a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfd4a-109">See Also</span></span>  
 [<span data-ttu-id="cfd4a-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="cfd4a-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cfd4a-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cfd4a-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cfd4a-112">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="cfd4a-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
