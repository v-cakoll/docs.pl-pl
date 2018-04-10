---
title: '&gt;Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc7c173ecc97bd3ca3b76a92ccbabc0f40062ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="bcb07-102">&gt;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bcb07-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="bcb07-103">Wszystkie typy liczbowe oraz wyliczenie zdefiniować operator relacyjny "większe niż" (`>`), która zwracałaby `true` Jeśli pierwszy argument operacji jest większa od drugiej, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="bcb07-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcb07-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bcb07-104">Remarks</span></span>  
 <span data-ttu-id="bcb07-105">Typy definiowane przez użytkownika można przeciążać `>` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="bcb07-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="bcb07-106">Jeśli `>` jest przeciążony [ < ](../../../csharp/language-reference/operators/less-than-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="bcb07-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="bcb07-107">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="bcb07-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcb07-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="bcb07-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bcb07-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcb07-109">See Also</span></span>  
 [<span data-ttu-id="bcb07-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="bcb07-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bcb07-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bcb07-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bcb07-112">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="bcb07-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="bcb07-113">jawne</span><span class="sxs-lookup"><span data-stu-id="bcb07-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
