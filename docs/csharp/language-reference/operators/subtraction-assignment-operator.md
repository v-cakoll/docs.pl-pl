---
title: Operator -= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 7cade0811536d836480f80a56cf8c4d09e089a0b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254397"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="8ec35-102">Operator -= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8ec35-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="8ec35-103">Operator przypisania odejmowania.</span><span class="sxs-lookup"><span data-stu-id="8ec35-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ec35-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ec35-104">Remarks</span></span>  
 <span data-ttu-id="8ec35-105">Wyrażenie używające operatora przypisania `-=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="8ec35-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="8ec35-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="8ec35-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="8ec35-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="8ec35-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="8ec35-108">Znaczenie [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) jest zależny od typów `x` i `y` (odejmowania w przypadku argumentów operacji numerycznych, delegowanie usuwania w przypadku argumentów operacji delegata i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="8ec35-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="8ec35-109">`-=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8ec35-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="8ec35-110">-= Operator jest również używany w języku C# można anulować subskrypcję zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8ec35-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="8ec35-111">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="8ec35-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ec35-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ec35-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8ec35-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ec35-113">See Also</span></span>

- [<span data-ttu-id="8ec35-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8ec35-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8ec35-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8ec35-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8ec35-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8ec35-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
