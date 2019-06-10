---
title: + operatory += — i C# odwołania
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 2c99065dacbf391e94c97092336f5dda3adda5b0
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815985"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="4eb21-102">+ i operatory += (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="4eb21-102">+ and += operators (C# Reference)</span></span>

<span data-ttu-id="4eb21-103">`+` Operator jest obsługiwany przez wbudowane typy liczbowe [ciąg](../keywords/string.md) typu, i [delegować](../keywords/delegate.md) typów.</span><span class="sxs-lookup"><span data-stu-id="4eb21-103">The `+` operator is supported by the built-in numeric types, [string](../keywords/string.md) type, and [delegate](../keywords/delegate.md) types.</span></span>

<span data-ttu-id="4eb21-104">Aby uzyskać informacje o operacji arytmetycznych `+` operatora, zobacz [jednoargumentowe plus lub minus operatory](arithmetic-operators.md#unary-plus-and-minus-operators) i [operator dodawania +](arithmetic-operators.md#addition-operator-) sekcje [operatorów arytmetycznych](arithmetic-operators.md)artykułu.</span><span class="sxs-lookup"><span data-stu-id="4eb21-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="4eb21-105">{1&gt;Łączenie ciągów&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4eb21-105">String concatenation</span></span>

<span data-ttu-id="4eb21-106">Kiedy jeden lub obydwa operandy są typu [ciąg](../keywords/string.md), `+` operator łączy ciągów reprezentujących argumentów:</span><span class="sxs-lookup"><span data-stu-id="4eb21-106">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="4eb21-107">Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodny sposób na ciągi formatu:</span><span class="sxs-lookup"><span data-stu-id="4eb21-107">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="4eb21-108">Delegatów</span><span class="sxs-lookup"><span data-stu-id="4eb21-108">Delegate combination</span></span>

<span data-ttu-id="4eb21-109">Dla argumentów operacji tego samego [delegować](../keywords/delegate.md) typu `+` operator zwraca nowe wystąpienie delegata, gdy wywoływany, wywołuje pierwszy operand, a następnie wywołuje drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="4eb21-109">For operands of the same [delegate](../keywords/delegate.md) type, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="4eb21-110">Jeśli którykolwiek z argumentów jest `null`, `+` operator zwraca wartość innego operandu (które mogą być również `null`).</span><span class="sxs-lookup"><span data-stu-id="4eb21-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="4eb21-111">W poniższym przykładzie pokazano, jak delegaty można łączyć z `+` operator:</span><span class="sxs-lookup"><span data-stu-id="4eb21-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="4eb21-112">Aby wykonać usuwanie delegata, użyj [ `-` operator](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="4eb21-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="4eb21-113">Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="4eb21-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="4eb21-114">+= — Operator przypisania dodawania</span><span class="sxs-lookup"><span data-stu-id="4eb21-114">Addition assignment operator +=</span></span>

<span data-ttu-id="4eb21-115">Usługi za pomocą wyrażenia `+=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="4eb21-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="4eb21-116">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="4eb21-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="4eb21-117">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4eb21-117">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="4eb21-118">W poniższym przykładzie pokazano użycie `+=` operator:</span><span class="sxs-lookup"><span data-stu-id="4eb21-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="4eb21-119">Możesz także użyć `+=` operatora, aby określić metodę programu obsługi zdarzeń podczas subskrybowania [zdarzeń](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="4eb21-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="4eb21-120">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="4eb21-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4eb21-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="4eb21-121">Operator overloadability</span></span>

<span data-ttu-id="4eb21-122">Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="4eb21-122">A user-defined type can [overload](../keywords/operator.md) the `+` operator.</span></span> <span data-ttu-id="4eb21-123">Gdy dane binarne `+` operator jest przeciążony, `+=` operator jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="4eb21-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="4eb21-124">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć `+=` operatora.</span><span class="sxs-lookup"><span data-stu-id="4eb21-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4eb21-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4eb21-125">C# language specification</span></span>

<span data-ttu-id="4eb21-126">Aby uzyskać więcej informacji, zobacz [jednoargumentowe plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4eb21-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4eb21-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4eb21-127">See also</span></span>

- [<span data-ttu-id="4eb21-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4eb21-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4eb21-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4eb21-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4eb21-130">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="4eb21-130">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4eb21-131">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="4eb21-131">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="4eb21-132">Porady: łączenie wielu ciągów</span><span class="sxs-lookup"><span data-stu-id="4eb21-132">How to: concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="4eb21-133">Delegaty</span><span class="sxs-lookup"><span data-stu-id="4eb21-133">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="4eb21-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4eb21-134">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="4eb21-135">Checked i unchecked</span><span class="sxs-lookup"><span data-stu-id="4eb21-135">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
- [<span data-ttu-id="4eb21-136">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="4eb21-136">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="4eb21-137">— i Operatorzy-=</span><span class="sxs-lookup"><span data-stu-id="4eb21-137">- and -= operators</span></span>](subtraction-operator.md)
