---
title: "() — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d62e6c93dcc69c892d4ca96ace3806cb1c8d989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bda2f-102">() — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bda2f-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="bda2f-103">Oprócz używane, aby określić kolejność operacji w wyrażeniu, nawiasy są używane do wykonywania następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="bda2f-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="bda2f-104">Określ rzutowania lub konwersje typów.</span><span class="sxs-lookup"><span data-stu-id="bda2f-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="bda2f-105">Wywołanie metod lub obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="bda2f-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="bda2f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bda2f-106">Remarks</span></span>  
 <span data-ttu-id="bda2f-107">Rzutowanie jawnie wywołuje operatora konwersji z jednego typu Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="bda2f-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="bda2f-108">Aby zdefiniować operator konwersji, zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="bda2f-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="bda2f-109">`()` Operator nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="bda2f-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="bda2f-110">Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="bda2f-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="bda2f-111">Wyrażenie cast może prowadzić do składni niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="bda2f-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="bda2f-112">Na przykład, wyrażenie `(x)–y` może być albo interpretowane jako wyrażenie cast (rzutowania y — typ x) lub jako dodatek wyrażenie w połączeniu z wyrażenia ujętego w nawiasy, który oblicza wartość x — y.</span><span class="sxs-lookup"><span data-stu-id="bda2f-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="bda2f-113">Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="bda2f-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bda2f-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bda2f-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bda2f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bda2f-115">See Also</span></span>  
 [<span data-ttu-id="bda2f-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="bda2f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bda2f-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bda2f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bda2f-118">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="bda2f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
