---
title: += — Operator - C# odwołania
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: 5d48f2fe53a9bb6f781f8d35f1e0983bcaa30f88
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240934"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="72d29-102">+= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="72d29-102">+= Operator (C# Reference)</span></span>

<span data-ttu-id="72d29-103">Operator przypisania dodawania.</span><span class="sxs-lookup"><span data-stu-id="72d29-103">The addition assignment operator.</span></span>

<span data-ttu-id="72d29-104">Usługi za pomocą wyrażenia `+=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="72d29-104">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="72d29-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="72d29-105">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="72d29-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="72d29-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="72d29-107">Dla typów liczbowych [operator dodawania](addition-operator.md) `+` oblicza sumę argumentów.</span><span class="sxs-lookup"><span data-stu-id="72d29-107">For numeric types, the [addition operator](addition-operator.md) `+` computes the sum of its operands.</span></span> <span data-ttu-id="72d29-108">Jeśli jeden lub obydwa operandy typu [ciąg](../keywords/string.md), łączy on ciągów reprezentujących swoich argumentów.</span><span class="sxs-lookup"><span data-stu-id="72d29-108">If one or both operands is of type [string](../keywords/string.md), it concatenates the string representations of its operands.</span></span> <span data-ttu-id="72d29-109">Dla typów delegowanych `+` operator zwraca nowe wystąpienie delegata, który jest kombinacja argumentów.</span><span class="sxs-lookup"><span data-stu-id="72d29-109">For delegate types, the `+` operator returns a new delegate instance that is combination of its operands.</span></span>

<span data-ttu-id="72d29-110">Możesz także użyć `+=` operatora, aby określić metodę programu obsługi zdarzeń podczas subskrybowania [zdarzeń](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="72d29-110">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="72d29-111">Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="72d29-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

<span data-ttu-id="72d29-112">W poniższym przykładzie pokazano użycie `+=` operator:</span><span class="sxs-lookup"><span data-stu-id="72d29-112">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="72d29-113">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="72d29-113">Operator overloadability</span></span>

<span data-ttu-id="72d29-114">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator dodawania](addition-operator.md) `+`, operator przypisania dodawania `+=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="72d29-114">If a user-defined type [overloads](../keywords/operator.md) the [addition operator](addition-operator.md) `+`, the addition assignment operator `+=` is implicitly overloaded.</span></span> <span data-ttu-id="72d29-115">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania dodawania.</span><span class="sxs-lookup"><span data-stu-id="72d29-115">A user-defined type cannot explicitly overload the addition assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="72d29-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="72d29-116">C# language specification</span></span>

<span data-ttu-id="72d29-117">Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) i [przypisanie zdarzenia](~/_csharplang/spec/expressions.md#event-assignment) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="72d29-117">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) and [Event assignment](~/_csharplang/spec/expressions.md#event-assignment) sections of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="72d29-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72d29-118">See also</span></span>

- [<span data-ttu-id="72d29-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="72d29-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="72d29-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="72d29-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="72d29-121">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="72d29-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="72d29-122">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="72d29-122">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="72d29-123">Delegaty</span><span class="sxs-lookup"><span data-stu-id="72d29-123">Delegates</span></span>](../../programming-guide/delegates/index.md)
