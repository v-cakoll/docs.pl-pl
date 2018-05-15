---
title: Operator %= (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 2b6a537ce189ab5a1c0c8c36995b6e9e98734e14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="34712-102">Operator %= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="34712-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="34712-103">Operator przypisania reszty.</span><span class="sxs-lookup"><span data-stu-id="34712-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34712-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34712-104">Remarks</span></span>  
 <span data-ttu-id="34712-105">Za pomocą wyrażenia `%=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="34712-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="34712-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="34712-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="34712-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="34712-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="34712-108">[% Operator](../../../csharp/language-reference/operators/remainder-operator.md) jest wstępnie zdefiniowane na typy liczbowe do obliczenia resztę po dzielenia.</span><span class="sxs-lookup"><span data-stu-id="34712-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="34712-109">`%=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="34712-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34712-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="34712-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="34712-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34712-111">See Also</span></span>  
 [<span data-ttu-id="34712-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="34712-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="34712-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="34712-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="34712-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="34712-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
