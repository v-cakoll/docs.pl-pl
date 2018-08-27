---
title: += — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bd0997ec5b7d79a41e01f9c2b17533293e412c1e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933790"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="db9c1-102">+= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="db9c1-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="db9c1-103">Operator przypisania dodawania.</span><span class="sxs-lookup"><span data-stu-id="db9c1-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db9c1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db9c1-104">Remarks</span></span>  
 <span data-ttu-id="db9c1-105">Wyrażenie używające operatora przypisania `+=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="db9c1-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```csharp  
x += y  
```  
  
 <span data-ttu-id="db9c1-106">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="db9c1-106">is equivalent to</span></span>  
  
```csharp  
x = x + y  
```  
  
 <span data-ttu-id="db9c1-107">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="db9c1-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="db9c1-108">Znaczenie [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) zależy od typów `x` i `y` (Dodawanie liczbową argumentów operacji, łączenia dla argumentów ciągu i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="db9c1-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="db9c1-109">`+=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="db9c1-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="db9c1-110">`+=` Operator jest również używany do określają metodę, która będzie wywoływana w odpowiedzi na zdarzenie; metody te są wywoływane programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="db9c1-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="db9c1-111">Korzystanie z `+=` operatora w tym kontekście jest określany jako *subskrybowanie zdarzenia*.</span><span class="sxs-lookup"><span data-stu-id="db9c1-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="db9c1-112">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) i [delegatów](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="db9c1-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db9c1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="db9c1-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="db9c1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db9c1-114">See Also</span></span>

- [<span data-ttu-id="db9c1-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db9c1-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="db9c1-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="db9c1-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="db9c1-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="db9c1-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
