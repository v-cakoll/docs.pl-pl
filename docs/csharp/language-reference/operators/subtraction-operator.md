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
ms.openlocfilehash: 9f43a863de69122e251204668af2ea989fcc993c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300090"
---
# <a name="--and---operators-c-reference"></a><span data-ttu-id="3418d-102">— i Operatorzy-= (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="3418d-102">- and -= operators (C# Reference)</span></span>

<span data-ttu-id="3418d-103">`-` Operator jest obsługiwany przez wbudowane typy liczbowe i [delegować](../keywords/delegate.md) typów.</span><span class="sxs-lookup"><span data-stu-id="3418d-103">The `-` operator is supported by the built-in numeric types and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="3418d-104">Aby uzyskać informacje o operacji arytmetycznych `-` operatora, zobacz [jednoargumentowe plus lub minus operatory](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator odejmowania -](arithmetic-operators.md#subtraction-operator--) części [operatorów arytmetycznych](arithmetic-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="3418d-104">For information about the arithmetic `-` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Subtraction operator -](arithmetic-operators.md#subtraction-operator--) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="delegate-removal"></a><span data-ttu-id="3418d-105">Usuwanie delegata</span><span class="sxs-lookup"><span data-stu-id="3418d-105">Delegate removal</span></span>

<span data-ttu-id="3418d-106">Dla argumentów operacji tego samego [delegować](../keywords/delegate.md) typu `-` operator zwraca wystąpienie delegata, który jest obliczany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3418d-106">For operands of the same [delegate](../keywords/delegate.md) type, the `-` operator returns a delegate instance that is calculated as follows:</span></span>

- <span data-ttu-id="3418d-107">Jeśli oba operandy są inne niż null, a lista wywołania drugi argument operacji jest odpowiednie podlisty ciągłych listy wywołania pierwszego operandu, wynik operacji jest nową listę wywołania uzyskany przez usuwanie wpisów drugiego operandu od Lista wywołania pierwszy operand.</span><span class="sxs-lookup"><span data-stu-id="3418d-107">If both operands are non-null and the invocation list of the second operand is a proper contiguous sublist of the invocation list of the first operand, the result of the operation is a new invocation list that is obtained by removing the second operand's entries from the invocation list of the first operand.</span></span> <span data-ttu-id="3418d-108">Jeśli drugi argument operacji listy pasuje wiele sąsiadujących podlisty na liście pierwszy operand, tylko podlisty pasującego najdalej z prawej strony jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="3418d-108">If the second operand's list matches multiple contiguous sublists in the first operand's list, only the right-most matching sublist is removed.</span></span> <span data-ttu-id="3418d-109">Jeśli wyniki usuwania w pustej listy, wynik jest `null`.</span><span class="sxs-lookup"><span data-stu-id="3418d-109">If removal results in an empty list, the result is `null`.</span></span>
- <span data-ttu-id="3418d-110">Jeśli wywołanie listę drugiego operandu nie jest właściwe podlisty ciągłych listy wywołania pierwszego operandu, wynik operacji jest pierwszy operand.</span><span class="sxs-lookup"><span data-stu-id="3418d-110">If the invocation list of the second operand is not a proper contiguous sublist of the invocation list of the first operand, the result of the operation is the first operand.</span></span>
- <span data-ttu-id="3418d-111">Jeśli pierwszy argument jest `null`, wynik operacji jest `null`.</span><span class="sxs-lookup"><span data-stu-id="3418d-111">If the first operand is `null`, the result of the operation is `null`.</span></span> <span data-ttu-id="3418d-112">Jeśli drugi argument operacji jest `null`, wynik operacji jest pierwszy operand.</span><span class="sxs-lookup"><span data-stu-id="3418d-112">If the second operand is `null`, the result of the operation is the first operand.</span></span>

<span data-ttu-id="3418d-113">W poniższym przykładzie pokazano sposób, w jaki `-` operacja wykonuje usuwanie delegata:</span><span class="sxs-lookup"><span data-stu-id="3418d-113">The following example shows how the `-` operation performs delegate removal:</span></span>

[!code-csharp-interactive[delegate removal](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#DelegateRemoval)]

## <a name="subtraction-assignment-operator--"></a><span data-ttu-id="3418d-114">Operator przypisania odejmowania-=</span><span class="sxs-lookup"><span data-stu-id="3418d-114">Subtraction assignment operator -=</span></span>

<span data-ttu-id="3418d-115">Usługi za pomocą wyrażenia `-=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="3418d-115">An expression using the `-=` operator, such as</span></span>

```csharp
x -= y
```

<span data-ttu-id="3418d-116">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="3418d-116">is equivalent to</span></span>

```csharp
x = x - y
```

<span data-ttu-id="3418d-117">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3418d-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="3418d-118">W poniższym przykładzie pokazano użycie `-=` operator:</span><span class="sxs-lookup"><span data-stu-id="3418d-118">The following example demonstrates the usage of the `-=` operator:</span></span>

[!code-csharp-interactive[-= examples](~/samples/csharp/language-reference/operators/SubtractionOperator.cs#SubtractAndAssign)]

<span data-ttu-id="3418d-119">Możesz także użyć `-=` operatora, aby określić metodę programu obsługi zdarzeń, aby usunąć po anulowaniu subskrypcji z [zdarzeń](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="3418d-119">You also use the `-=` operator to specify an event handler method to remove when you unsubscribe from an [event](../keywords/event.md).</span></span> <span data-ttu-id="3418d-120">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="3418d-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3418d-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="3418d-121">Operator overloadability</span></span>

<span data-ttu-id="3418d-122">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `-` operatora.</span><span class="sxs-lookup"><span data-stu-id="3418d-122">A user-defined type can [overload](../keywords/operator.md) the `-` operator.</span></span> <span data-ttu-id="3418d-123">Gdy dane binarne `-` operator jest przeciążony, `-=` operator jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="3418d-123">When a binary `-` operator is overloaded, the `-=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="3418d-124">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="3418d-124">A user-defined type cannot explicitly overload the `-=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3418d-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3418d-125">C# language specification</span></span>

<span data-ttu-id="3418d-126">Aby uzyskać więcej informacji, zobacz [jednoargumentowy minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) i [operator odejmowania](~/_csharplang/spec/expressions.md#subtraction-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3418d-126">For more information, see the [Unary minus operator](~/_csharplang/spec/expressions.md#unary-minus-operator) and [Subtraction operator](~/_csharplang/spec/expressions.md#subtraction-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3418d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3418d-127">See also</span></span>

- [<span data-ttu-id="3418d-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3418d-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3418d-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3418d-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3418d-130">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3418d-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="3418d-131">Delegaty</span><span class="sxs-lookup"><span data-stu-id="3418d-131">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="3418d-132">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3418d-132">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="3418d-133">Checked i unchecked</span><span class="sxs-lookup"><span data-stu-id="3418d-133">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="3418d-134">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="3418d-134">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="3418d-135">+ i operatory +=</span><span class="sxs-lookup"><span data-stu-id="3418d-135">+ and += operators</span></span>](addition-operator.md)
