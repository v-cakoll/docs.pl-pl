---
title: '- operatory-= — i C# odwołania'
ms.custom: seodec18
ms.date: 05/27/2019
f1_keywords:
- -_CSharpKeyword
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction operator [C#]
- delegate removal [C#]
- '- operator [C#]'
- subtraction assignment operator [C#]
- event unsubscription [C#]
- -= operator [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 7c9863134cb2a12072954bb283c7828abece3adb
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347911"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="0fabe-102">— i Operatorzy-= (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="0fabe-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="0fabe-103">`-` Operator jest obsługiwany przez wbudowane typy liczbowe i [delegować](../keywords/delegate.md) typów.</span><span class="sxs-lookup"><span data-stu-id="0fabe-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="0fabe-104">Aby uzyskać informacje o operacji arytmetycznych `-` operatora, zobacz [jednoargumentowe plus lub minus operatory](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator odejmowania -](arithmetic-operators.md#subtraction-operator--) części [operatorów arytmetycznych](arithmetic-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="0fabe-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="0fabe-105">Usuwanie delegata</span><span class="sxs-lookup"><span data-stu-id="0fabe-105">Delegate removal</span></span>

<span data-ttu-id="0fabe-106">Dla argumentów operacji tego samego [delegować](../keywords/delegate.md) typu `-` operator zwraca wystąpienie delegata, który jest obliczany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0fabe-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="0fabe-107">Jeśli oba operandy są inne niż null, a lista wywołania prawostronny operand jest właściwe ciągłych podlistę wywołania listę lewostronny operand, wynik operacji jest nową listę wywołania uzyskany przez usunięcie prawostronny operand wpisy na liście wywołania operandu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="0fabe-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="0fabe-108">Jeśli listy prawostronny operand pasuje wiele sąsiadujących podlisty liście argument po lewej stronie, tylko podlisty pasującego najdalej z prawej strony są usuwane.</span><span class="sxs-lookup"><span data-stu-id="0fabe-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="0fabe-109">Jeśli wyniki usuwania w pustej listy, wynik jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0fabe-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="0fabe-110">Jeśli wywołanie listę prawostronny operand nie jest właściwe ciągłych podlistę wywołania listę lewostronny operand, wynik operacji jest lewostronny operand.</span><span class="sxs-lookup"><span data-stu-id="0fabe-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="0fabe-111">Na przykład usuwanie delegata, który nie jest częścią delegatów multiemisji nie robi nic i powoduje niezmienione delegatów multiemisji.</span><span class="sxs-lookup"><span data-stu-id="0fabe-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="0fabe-112">Poprzedni przykład ilustruje też, że podczas delegata usuwania wystąpień delegata są porównywane.</span><span class="sxs-lookup"><span data-stu-id="0fabe-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="0fabe-113">Na przykład, delegatów, które są tworzone z wersji ewaluacyjnej identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="0fabe-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="0fabe-114">Aby uzyskać więcej informacji na temat równości delegata zobacz [delegować Operatory równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fabe-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

- <span data-ttu-id="0fabe-115">Jeśli argument po lewej stronie jest `null`, wynik operacji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0fabe-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="0fabe-116">Jeśli argument po prawej stronie jest `null`, wynik operacji jest lewostronny operand.</span><span class="sxs-lookup"><span data-stu-id="0fabe-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="0fabe-117">Aby połączyć delegatów, należy użyć [ `+` operator](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="0fabe-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="0fabe-118">Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fabe-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="0fabe-119">Operator przypisania odejmowania-=</span><span class="sxs-lookup"><span data-stu-id="0fabe-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="0fabe-120">Usługi za pomocą wyrażenia `-=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="0fabe-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="0fabe-121">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="0fabe-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="0fabe-122">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="0fabe-122">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="0fabe-123">W poniższym przykładzie pokazano użycie `-=` operator:</span><span class="sxs-lookup"><span data-stu-id="0fabe-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="0fabe-124">Możesz także użyć `-=` operatora, aby określić metodę programu obsługi zdarzeń, aby usunąć po anulowaniu subskrypcji z [zdarzeń](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="0fabe-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="0fabe-125">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="0fabe-125">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0fabe-126">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="0fabe-126">Operator overloadability</span></span>

<span data-ttu-id="0fabe-127">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `-` operatora.</span><span class="sxs-lookup"><span data-stu-id="0fabe-127">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="0fabe-128">Gdy dane binarne `-` operator jest przeciążony, `-=` operator jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="0fabe-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="0fabe-129">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="0fabe-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0fabe-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0fabe-130">C# language specification</span></span>

<span data-ttu-id="0fabe-131">Aby uzyskać więcej informacji, zobacz [jednoargumentowy minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0fabe-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0fabe-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fabe-132">See also</span></span>

- [<span data-ttu-id="0fabe-133">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="0fabe-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0fabe-134">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0fabe-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="0fabe-135">Delegaty</span><span class="sxs-lookup"><span data-stu-id="0fabe-135">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="0fabe-136">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0fabe-136">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="0fabe-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="0fabe-137">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0fabe-138">+ i operatory +=</span><span class="sxs-lookup"><span data-stu-id="0fabe-138">+ and += operators</span></span>](addition-operator.md)
