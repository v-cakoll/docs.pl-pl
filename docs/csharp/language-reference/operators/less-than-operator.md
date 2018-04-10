---
title: '&lt;Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="f9028-102">&lt;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f9028-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="f9028-103">Wszystkie typy liczbowe oraz wyliczenie zdefiniować operator relacyjny "mniejsze niż" (`<`) zwracająca `true` Jeśli pierwszy argument operacji jest mniejsza od drugiej, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="f9028-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9028-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9028-104">Remarks</span></span>  
 <span data-ttu-id="f9028-105">Typy definiowane przez użytkownika można przeciążać `<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f9028-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="f9028-106">Jeśli `<` jest przeciążony [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="f9028-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="f9028-107">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="f9028-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9028-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9028-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f9028-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9028-109">See Also</span></span>  
 [<span data-ttu-id="f9028-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f9028-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f9028-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f9028-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f9028-112">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="f9028-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
