---
title: '- and-= operatory- C# Reference'
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
ms.openlocfilehash: ccf3572df99f5c3de127c9ada690a977843648af
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238848"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="6e412-102">-and-= — operatoryC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="6e412-102">- and -= operators (C# reference)</span></span>

<span data-ttu-id="6e412-103">Operatory `-` i `-=` są obsługiwane przez wbudowane typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) oraz typy [delegatów](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="6e412-103">The `-` and `-=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="6e412-104">Aby uzyskać informacje o operatorze arytmetycznej `-`, zobacz [operatory jednoargumentowe Plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator odejmowania —](arithmetic-operators.md#subtraction-operator--) sekcje w artykule [Operatory arytmetyczne](arithmetic-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="6e412-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="6e412-105">Usuwanie delegata</span><span class="sxs-lookup"><span data-stu-id="6e412-105">Delegate removal</span></span>

<span data-ttu-id="6e412-106">Dla operandów tego samego typu [delegata](../builtin-types/reference-types.md#the-delegate-type) operator `-` zwraca wystąpienie delegata, które jest obliczane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6e412-106">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="6e412-107">Jeśli oba operandy mają wartość inną niż null, a lista wywołań operandu po prawej stronie jest właściwą ciągłą podlistą listy wywołań operandu po lewej stronie, wynik operacji jest nową listą wywołań, która jest uzyskiwana przez usunięcie argumentów operacji po prawej stronie wpisy z listy wywołań operandu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="6e412-107">If both operands are non-null and the invocation list of the right-hand operand is a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is a new invocation list that is obtained by removing the right-hand operand's entries from the invocation list of the left-hand operand.</span></span> <span data-ttu-id="6e412-108">Jeśli lista argumentów operacji po prawej stronie jest zgodna z wieloma ciągłymi podlistami na liście operandów po lewej stronie, usuwana jest tylko podlista dopasowania do prawej.</span><span class="sxs-lookup"><span data-stu-id="6e412-108">If the right-hand operand's list matches multiple contiguous sublists in the left-hand operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="6e412-109">Jeśli usunięcie spowoduje powstanie pustej listy, wynik jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6e412-109">If removal results in an empty list, the result is `null`.</span></span>

  [!code-csharp-interactive[delegate removal](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

- <span data-ttu-id="6e412-110">Jeśli lista wywołań operandu po prawej stronie nie jest prawidłową ciągłą podlistą listy wywołań operandu po lewej stronie, wynik operacji jest argumentem po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="6e412-110">If the invocation list of the right-hand operand is not a proper contiguous sublist of the invocation list of the left-hand operand, the result of the operation is the left-hand operand.</span></span> <span data-ttu-id="6e412-111">Na przykład usunięcie delegata, który nie jest częścią delegata multiemisji, ma wartość Nothing i skutkuje niezmienionym delegatem multiemisji.</span><span class="sxs-lookup"><span data-stu-id="6e412-111">For example, removing a delegate that is not part of the multicast delegate does nothing and results in the unchanged multicast delegate.</span></span>

  [!code-csharp-interactive[delegate removal with no effect](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalNoChange)]

  <span data-ttu-id="6e412-112">W poprzednim przykładzie pokazano również, że podczas porównywania wystąpień delegatów usuwania delegatów.</span><span class="sxs-lookup"><span data-stu-id="6e412-112">The preceding example also demonstrates that during delegate removal delegate instances are compared.</span></span> <span data-ttu-id="6e412-113">Na przykład Delegaty wytwarzane z oceny identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe.</span><span class="sxs-lookup"><span data-stu-id="6e412-113">For example, delegates that are produced from evaluation of identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal.</span></span> <span data-ttu-id="6e412-114">Aby uzyskać więcej informacji o równość delegowania, zobacz sekcję [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6e412-114">For more information about delegate equality, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="6e412-115">Jeśli argument operacji po lewej stronie jest `null`, wynik operacji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6e412-115">If the left-hand operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="6e412-116">Jeśli argument operacji po prawej stronie jest `null`, wynik operacji jest argumentem po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="6e412-116">If the right-hand operand is `null`, the result of the operation is the left-hand operand.</span></span>

  [!code-csharp-interactive[delegate removal and null](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemovalAndNull)]

<span data-ttu-id="6e412-117">Aby połączyć delegatów, użyj [operatora`+`](addition-operator.md#delegate-combination).</span><span class="sxs-lookup"><span data-stu-id="6e412-117">To combine delegates, use the [`+` operator](addition-operator.md#delegate-combination).</span></span>

<span data-ttu-id="6e412-118">Aby uzyskać więcej informacji na temat typów delegatów, zobacz [delegats](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e412-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="6e412-119">Operator przypisania odejmowania — =</span><span class="sxs-lookup"><span data-stu-id="6e412-119">Subtraction assignment operator -=</span></span>

<span data-ttu-id="6e412-120">Wyrażenie używające operatora `-=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="6e412-120">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="6e412-121">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="6e412-121">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="6e412-122">z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="6e412-122">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6e412-123">Poniższy przykład ilustruje użycie operatora `-=`:</span><span class="sxs-lookup"><span data-stu-id="6e412-123">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/snippets/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="6e412-124">Możesz również użyć operatora `-=`, aby określić metodę programu obsługi zdarzeń do usunięcia podczas anulowania subskrypcji [zdarzenia](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="6e412-124">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="6e412-125">Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="6e412-125">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="6e412-126">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="6e412-126">Operator overloadability</span></span>

<span data-ttu-id="6e412-127">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operator `-`.</span><span class="sxs-lookup"><span data-stu-id="6e412-127">A user-defined type can [overload](operator-overloading.md) the `-` operator.</span></span> <span data-ttu-id="6e412-128">Gdy operator `-` binarny jest przeciążony, operator `-=` jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="6e412-128">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="6e412-129">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora `-=`.</span><span class="sxs-lookup"><span data-stu-id="6e412-129">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6e412-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6e412-130">C# language specification</span></span>

<span data-ttu-id="6e412-131">Aby uzyskać więcej informacji, zobacz sekcje [jednoargumentowe minus](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6e412-131">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e412-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e412-132">See also</span></span>

- [<span data-ttu-id="6e412-133">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="6e412-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6e412-134">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6e412-134">C# operators</span></span>](index.md)
- [<span data-ttu-id="6e412-135">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6e412-135">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="6e412-136">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="6e412-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6e412-137">Operatory + i + =</span><span class="sxs-lookup"><span data-stu-id="6e412-137">+ and += operators</span></span>](addition-operator.md)
