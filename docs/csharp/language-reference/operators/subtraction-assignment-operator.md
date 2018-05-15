---
title: Operator -= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 33aba2e944c8d0589949e7bdc77aadd4f213da28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="--operator-c-reference"></a><span data-ttu-id="f6135-102">Operator -= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f6135-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="f6135-103">Operator przypisania odejmowania.</span><span class="sxs-lookup"><span data-stu-id="f6135-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6135-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6135-104">Remarks</span></span>  
 <span data-ttu-id="f6135-105">Za pomocą wyrażenia `-=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="f6135-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```  
x -= y  
```  
  
 <span data-ttu-id="f6135-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="f6135-106">is equivalent to</span></span>  
  
```  
x = x - y  
```  
  
 <span data-ttu-id="f6135-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="f6135-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f6135-108">Znaczenie [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) jest zależna od typów `x` i `y` (odejmowania w przypadku argumentów operacji liczbowych, delegować usunięcia operandy delegata i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="f6135-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="f6135-109">`-=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f6135-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="f6135-110">-= Operator umożliwia również w języku C# anulowanie subskrypcji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f6135-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="f6135-111">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="f6135-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6135-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6135-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f6135-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6135-113">See Also</span></span>  
 [<span data-ttu-id="f6135-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f6135-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f6135-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6135-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6135-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f6135-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
