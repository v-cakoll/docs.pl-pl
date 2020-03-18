---
title: '- i -= operatory - odwołanie c#'
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
ms.openlocfilehash: 2017aade92e8d7ad2af7101a107122fa8d7b9e27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847654"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="5ef45-102">- i -= operatory (odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="5ef45-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="5ef45-103">`-` Operatory `-=` i są obsługiwane przez wbudowane [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) i typy [delegatów.](../builtin-types/reference-types.md#the-delegate-type)</span><span class="sxs-lookup"><span data-stu-id="5ef45-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="5ef45-104">Aby uzyskać informacje na `-` temat operatora arytmetycznego, zobacz [Operatory nieparzyste plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) oraz [Operator odejmowania —](arithmetic-operators.md#subtraction-operator--) sekcje operatora [arytmetycznego.](arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="5ef45-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="5ef45-105">Delegowanie usuwania</span><span class="sxs-lookup"><span data-stu-id="5ef45-105">Delegate removal</span></span>

<span data-ttu-id="5ef45-106">W przypadku argumentów tego samego typu `-` [delegata](../builtin-types/reference-types.md#the-delegate-type) operator zwraca wystąpienie delegata, które jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5ef45-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="5ef45-107">Jeśli oba argumenty są niezer- null, a lista wywoławczo-wywołania argumentu po prawej stronie jest właściwą ciągłą podlistą listy wywołania operandu po lewej stronie, wynikiem operacji jest nowa lista wywołań, która jest uzyskiwana przez usunięcie argumentu po prawej stronie. z listy wywoławczej argumentu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="5ef45-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="5ef45-108">Jeśli lista operandu po prawej stronie jest zgodna z wieloma sąsiadującymi podlistami na liście operandu po lewej stronie, usuwana jest tylko najbardziej pasująca lista podrzędna po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="5ef45-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="5ef45-109">Jeśli usunięcie spowoduje usunięcie pustej `null`listy, wynikiem jest .</span><span class="sxs-lookup"><span data-stu-id="5ef45-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](snippets/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="5ef45-110">Jeśli lista wywołań operandu po prawej stronie nie jest właściwą ciągłą podlistą listy wywołania operandu po lewej stronie, wynikiem operacji jest argument po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="5ef45-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="5ef45-111">Na przykład usunięcie delegata, który nie jest częścią delegata multiemisji nie robi nic i powoduje niezmienionego delegata multiemisji.</span><span class="sxs-lookup"><span data-stu-id="5ef45-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](snippets/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="5ef45-112">W poprzednim przykładzie również pokazuje, że podczas usuwania delegata delegata wystąpienia są porównywane.</span><span class="sxs-lookup"><span data-stu-id="5ef45-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="5ef45-113">Na przykład delegatów, które są produkowane z oceny identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe.</span><span class="sxs-lookup"><span data-stu-id="5ef45-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="5ef45-114">Aby uzyskać więcej informacji na temat równości delegatów, zobacz [delegowanie operatorów równości specyfikacji](~/_csharplang/spec/expressions.md#delegate-equality-operators) [języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="5ef45-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="5ef45-115">Jeśli argument po lewej `null`stronie jest , wynik `null`operacji jest .</span><span class="sxs-lookup"><span data-stu-id="5ef45-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="5ef45-116">Jeśli argument po prawej `null`stronie jest , wynikiem operacji jest po lewej stronie operand.</span><span class="sxs-lookup"><span data-stu-id="5ef45-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](snippets/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="5ef45-117">Aby połączyć delegatów, należy użyć [ `+` operatora](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="5ef45-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="5ef45-118">Aby uzyskać więcej informacji na temat typów pełnomocników, zobacz [Delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ef45-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="5ef45-119">Operator przypisania odejmowania -=</span><span class="sxs-lookup"><span data-stu-id="5ef45-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="5ef45-120">Wyrażenie używające `-=` operatora, takie jak</span><span class="sxs-lookup"><span data-stu-id="5ef45-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="5ef45-121">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="5ef45-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="5ef45-122">chyba `x` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5ef45-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="5ef45-123">W poniższym przykładzie przedstawiono `-=` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="5ef45-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](snippets/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="5ef45-124">Operator służy `-=` również do określania metody obsługi zdarzeń, aby usunąć po anulowaniu subskrypcji [ze zdarzenia](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="5ef45-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="5ef45-125">Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i zniej subskrybować je.](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="5ef45-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5ef45-126">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="5ef45-126">Operator overloadability</span></span>

<span data-ttu-id="5ef45-127">Typ zdefiniowany przez użytkownika `-` może [przeciążać](operator-overloading.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="5ef45-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="5ef45-128">Gdy operator `-` binarny jest `-=` przeciążony, operator jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="5ef45-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="5ef45-129">Typ zdefiniowany przez użytkownika nie `-=` może jawnie przeciążać operatora.</span><span class="sxs-lookup"><span data-stu-id="5ef45-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5ef45-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5ef45-130">C# language specification</span></span>

<span data-ttu-id="5ef45-131">Aby uzyskać więcej informacji, zobacz [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="5ef45-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef45-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ef45-132">See also</span></span>

- [<span data-ttu-id="5ef45-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5ef45-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5ef45-134">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5ef45-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="5ef45-135">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5ef45-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="5ef45-136">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="5ef45-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="5ef45-137">+ i += operatory</span><span class="sxs-lookup"><span data-stu-id="5ef45-137">+ and += operators</span></span>](addition-operator.md)
