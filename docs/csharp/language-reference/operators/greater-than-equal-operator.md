---
title: "&gt;= — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f020c2bd8756899908681ab72cac7aa2a203c6a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="b0c60-102">&gt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b0c60-102">&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="b0c60-103">Wszystkie typy liczbowe oraz wyliczenie zdefiniuj "większe lub równe" operator relacyjny, `>=` zwracającą `true` Jeśli pierwszy argument operacji jest większe lub równe drugiemu, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="b0c60-103">All numeric and enumeration types define a "greater than or equal" relational operator, `>=` that returns `true` if the first operand is greater than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0c60-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0c60-104">Remarks</span></span>  
 <span data-ttu-id="b0c60-105">Typy definiowane przez użytkownika można przeciążać `>=` operatora.</span><span class="sxs-lookup"><span data-stu-id="b0c60-105">User-defined types can overload the `>=` operator.</span></span> <span data-ttu-id="b0c60-106">Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="b0c60-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="b0c60-107">Jeśli `>=` jest przeciążony [ <= ](../../../csharp/language-reference/operators/less-than-equal-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="b0c60-107">If `>=` is overloaded, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="b0c60-108">Operacje na typy całkowite zazwyczaj są dozwolone w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b0c60-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c60-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0c60-109">Example</span></span>  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b0c60-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0c60-110">See Also</span></span>  
 [<span data-ttu-id="b0c60-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="b0c60-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b0c60-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b0c60-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b0c60-113">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="b0c60-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
