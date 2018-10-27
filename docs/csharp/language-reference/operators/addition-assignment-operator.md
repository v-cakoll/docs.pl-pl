---
title: += — Operator (odwołanie w C#)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192034"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="80b33-102">+= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="80b33-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="80b33-103">Operator przypisania dodawania.</span><span class="sxs-lookup"><span data-stu-id="80b33-103">The addition assignment operator.</span></span>

<span data-ttu-id="80b33-104">Usługi za pomocą wyrażenia `+=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="80b33-104">An expression using the `+=` operator, such as</span></span>  

```csharp
x += y
```  

<span data-ttu-id="80b33-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="80b33-105">is equivalent to</span></span>  

```csharp
x = x + y
```  

<span data-ttu-id="80b33-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="80b33-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="80b33-107">Dla typów liczbowych [operator dodawania](addition-operator.md) `+` oblicza sumę argumentów.</span><span class="sxs-lookup"><span data-stu-id="80b33-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="80b33-108">Jeśli jeden lub obydwa operandy typu [ciąg](../keywords/string.md), łączy on ciągów reprezentujących swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="80b33-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="80b33-109">Dla typów delegowanych `+` operator zwraca nowe wystąpienie delegata, który jest kombinacja argumentów.</span><span class="sxs-lookup"><span data-stu-id="80b33-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="80b33-110">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator dodawania](addition-operator.md) `+`, operator przypisania dodawania `+=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="80b33-110">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span>

<span data-ttu-id="80b33-111">Możesz także użyć `+=` operatora, aby określić metodę programu obsługi zdarzeń podczas subskrybowania [zdarzeń](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="80b33-111">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="80b33-112">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="80b33-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="80b33-113">W poniższym przykładzie pokazano użycie `+=` operator:</span><span class="sxs-lookup"><span data-stu-id="80b33-113">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a><span data-ttu-id="80b33-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80b33-114">See also</span></span>

- [<span data-ttu-id="80b33-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="80b33-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="80b33-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="80b33-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="80b33-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="80b33-117">C# Operators</span></span>](index.md)
- [<span data-ttu-id="80b33-118">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="80b33-118">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="80b33-119">Delegaty</span><span class="sxs-lookup"><span data-stu-id="80b33-119">Delegates</span></span>](../../programming-guide/delegates/index.md)
