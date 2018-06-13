---
title: '| — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 7b62af53f0d8b7cba29f4496887717f1726eabf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265690"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="008ec-102">| — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="008ec-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="008ec-103">Binarny `|` operatory są wstępnie zdefiniowane dla typów całkowitych i `bool`.</span><span class="sxs-lookup"><span data-stu-id="008ec-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="008ec-104">W przypadku typów całkowitych `|` oblicza wartości bitowe lub argumentów.</span><span class="sxs-lookup"><span data-stu-id="008ec-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="008ec-105">Dla `bool` argumentów operacji, `|` logiczne lub z argumentów; oblicza wynik jest `false` tylko wtedy, gdy są obie argumentów `false`.</span><span class="sxs-lookup"><span data-stu-id="008ec-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="008ec-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="008ec-106">Remarks</span></span>  
 <span data-ttu-id="008ec-107">Typy definiowane przez użytkownika można przeciążać `|` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="008ec-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="008ec-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="008ec-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="008ec-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="008ec-109">See Also</span></span>  
 [<span data-ttu-id="008ec-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="008ec-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="008ec-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="008ec-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="008ec-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="008ec-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
