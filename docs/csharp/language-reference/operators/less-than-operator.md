---
title: '&lt; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: eceb6214e4e625aa71e12788d5dd5e8324c75443
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270234"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="08ff0-102">&lt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="08ff0-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="08ff0-103">Wszystkie typy liczbowe oraz wyliczenie zdefiniować operator relacyjny "mniejsze niż" (`<`) zwracająca `true` Jeśli pierwszy argument operacji jest mniejsza od drugiej, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="08ff0-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08ff0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08ff0-104">Remarks</span></span>  
 <span data-ttu-id="08ff0-105">Typy definiowane przez użytkownika można przeciążać `<` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="08ff0-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="08ff0-106">Jeśli `<` jest przeciążony [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) również musi być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="08ff0-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="08ff0-107">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="08ff0-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08ff0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="08ff0-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="08ff0-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08ff0-109">See Also</span></span>  
 [<span data-ttu-id="08ff0-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="08ff0-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="08ff0-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="08ff0-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="08ff0-112">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="08ff0-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
