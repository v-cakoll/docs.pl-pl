---
title: += — Operator (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: de83f48fc644d8b232d9ef9e1698272f20a27d65
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5fca3-102">+= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5fca3-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="5fca3-103">Operator przypisania dodawania.</span><span class="sxs-lookup"><span data-stu-id="5fca3-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fca3-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fca3-104">Remarks</span></span>  
 <span data-ttu-id="5fca3-105">Za pomocą wyrażenia `+=` operator przypisania, takich jak</span><span class="sxs-lookup"><span data-stu-id="5fca3-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="5fca3-106">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="5fca3-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="5fca3-107">z tą różnicą, że `x` jest tylko jeden raz obliczone.</span><span class="sxs-lookup"><span data-stu-id="5fca3-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="5fca3-108">Znaczenie [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) zależy od typów `x` i `y` (oprócz dla argumentów operacji liczbowych, łączenia dla argumentów ciągu i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="5fca3-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="5fca3-109">`+=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5fca3-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="5fca3-110">`+=` Operator służy również do określają metodę, która będzie wywoływana w odpowiedzi na zdarzenia; metody te są wywoływane programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5fca3-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="5fca3-111">Korzystanie z `+=` operatora w tym kontekście jest określany jako *subskrybowanie zdarzeń*.</span><span class="sxs-lookup"><span data-stu-id="5fca3-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="5fca3-112">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) i [delegatów](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="5fca3-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fca3-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fca3-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5fca3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fca3-114">See Also</span></span>  
 [<span data-ttu-id="5fca3-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="5fca3-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5fca3-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5fca3-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5fca3-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5fca3-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
