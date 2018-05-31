---
title: () — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 2ded01ef3192e0f34d586cd63d93b894b5347e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275028"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="390bc-102">() — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="390bc-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="390bc-103">Oprócz określania kolejności operacji w wyrażeniach nawiasy są też używane do następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="390bc-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="390bc-104">Określanie rzutowania lub konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="390bc-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="390bc-105">Wywołanie metod lub obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="390bc-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="390bc-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="390bc-106">Remarks</span></span>  
 <span data-ttu-id="390bc-107">Rzutowanie jawnie wywołuje operatora konwersji z jednego typu do drugiego. Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="390bc-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="390bc-108">Aby zdefiniować operatora konwersji, zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md) definiowanie operatorów konwersji.</span><span class="sxs-lookup"><span data-stu-id="390bc-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="390bc-109">Operator `()` nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="390bc-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="390bc-110">Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="390bc-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="390bc-111">Wyrażenie cast może prowadzić do niejednoznaczności składni.</span><span class="sxs-lookup"><span data-stu-id="390bc-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="390bc-112">Na przykład wyrażenie `(x)–y` może być interpretowane jako wyrażenie cast (rzutowanie -y na typ x) lub jako wyrażenie addytywne połączone z wyrażeniem w nawiasie, które oblicza wartość x — y.</span><span class="sxs-lookup"><span data-stu-id="390bc-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="390bc-113">Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="390bc-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="390bc-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="390bc-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="390bc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="390bc-115">See Also</span></span>  
 [<span data-ttu-id="390bc-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="390bc-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="390bc-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="390bc-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="390bc-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="390bc-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
