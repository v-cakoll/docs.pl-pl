---
title: -= Operator — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: dc3cedafc57e1c6ec9bc34ca4e2c2aa9c604848c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239588"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="6f804-102">Operator -= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6f804-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="6f804-103">Operator przypisania odejmowania.</span><span class="sxs-lookup"><span data-stu-id="6f804-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f804-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f804-104">Remarks</span></span>  
 <span data-ttu-id="6f804-105">Wyrażenie używające operatora przypisania `-=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="6f804-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="6f804-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="6f804-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="6f804-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="6f804-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6f804-108">Znaczenie [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) jest zależny od typów `x` i `y` (odejmowania w przypadku argumentów operacji numerycznych, delegowanie usuwania w przypadku argumentów operacji delegata i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="6f804-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="6f804-109">`-=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6f804-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="6f804-110">-= Operator jest również używany w języku C# można anulować subskrypcję zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6f804-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="6f804-111">Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="6f804-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f804-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f804-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6f804-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f804-113">See Also</span></span>

- [<span data-ttu-id="6f804-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6f804-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6f804-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6f804-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6f804-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6f804-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
