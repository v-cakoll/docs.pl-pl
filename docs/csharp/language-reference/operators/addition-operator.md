---
title: + i += operatory — odwołanie do języka C#
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
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399302"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="1da42-102">+ i += operatory (odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="1da42-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="1da42-103">`+` Operatory `+=` i są obsługiwane przez wbudowane [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe,](../builtin-types/floating-point-numeric-types.md) typ [ciągu](../builtin-types/reference-types.md#the-string-type) i typy [delegatów.](../builtin-types/reference-types.md#the-delegate-type)</span><span class="sxs-lookup"><span data-stu-id="1da42-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="1da42-104">Aby uzyskać informacje na `+` temat operatora arytmetycznego, zobacz [operatory nieparzyste plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) [oraz Operator dodawania +](arithmetic-operators.md#addition-operator-) w artykule [Operatory arytmetyczne.](arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="1da42-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="1da42-105">Ciągów</span><span class="sxs-lookup"><span data-stu-id="1da42-105">String concatenation</span></span>

<span data-ttu-id="1da42-106">Gdy jeden lub oba operandy są `+` [typu ciągu,](../builtin-types/reference-types.md#the-string-type)operator łączy reprezentacje ciągu jego operands:</span><span class="sxs-lookup"><span data-stu-id="1da42-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="1da42-107">Począwszy od C# 6, [interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodniejszy sposób formatowania ciągów:</span><span class="sxs-lookup"><span data-stu-id="1da42-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="1da42-108">Kombinacja pełnomocników</span><span class="sxs-lookup"><span data-stu-id="1da42-108">Delegate combination</span></span>

<span data-ttu-id="1da42-109">W przypadku operandów tego samego `+` typu [delegata](../builtin-types/reference-types.md#the-delegate-type) operator zwraca nowe wystąpienie delegata, które po wywołaniu wywołuje operand po lewej stronie, a następnie wywołuje operand po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="1da42-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="1da42-110">Jeśli którykolwiek z argumentów `null` `+` jest , operator zwraca wartość innego operand (który również może być `null`).</span><span class="sxs-lookup"><span data-stu-id="1da42-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="1da42-111">W poniższym przykładzie pokazano, jak `+` delegatów można łączyć z operatorem:</span><span class="sxs-lookup"><span data-stu-id="1da42-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="1da42-112">Aby wykonać usunięcie delegata, należy użyć [ `-` operatora](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="1da42-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="1da42-113">Aby uzyskać więcej informacji na temat typów pełnomocników, zobacz [Delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="1da42-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="1da42-114">Operator przypisania dodatku +=</span><span class="sxs-lookup"><span data-stu-id="1da42-114">Addition assignment operator +=</span></span>

<span data-ttu-id="1da42-115">Wyrażenie używające `+=` operatora, takie jak</span><span class="sxs-lookup"><span data-stu-id="1da42-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="1da42-116">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="1da42-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="1da42-117">chyba `x` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1da42-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1da42-118">W poniższym przykładzie przedstawiono `+=` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="1da42-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="1da42-119">Operator służy `+=` również do określania metody obsługi zdarzeń podczas subskrybowania [zdarzenia](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="1da42-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="1da42-120">Aby uzyskać więcej informacji, zobacz [Jak: subskrybować i anulować subskrypcję wydarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="1da42-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1da42-121">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="1da42-121">Operator overloadability</span></span>

<span data-ttu-id="1da42-122">Typ zdefiniowany przez użytkownika `+` może [przeciążać](operator-overloading.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="1da42-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="1da42-123">Gdy operator `+` binarny jest `+=` przeciążony, operator jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="1da42-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="1da42-124">Typ zdefiniowany przez użytkownika nie `+=` może jawnie przeciążać operatora.</span><span class="sxs-lookup"><span data-stu-id="1da42-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1da42-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1da42-125">C# language specification</span></span>

<span data-ttu-id="1da42-126">Aby uzyskać więcej informacji, zobacz [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [Dodawanie operator](~/_csharplang/spec/expressions.md#addition-operator) sekcje [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="1da42-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1da42-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1da42-127">See also</span></span>

- [<span data-ttu-id="1da42-128">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1da42-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1da42-129">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1da42-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="1da42-130">Jak połączyć wiele ciągów</span><span class="sxs-lookup"><span data-stu-id="1da42-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="1da42-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1da42-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="1da42-132">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="1da42-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="1da42-133">- i -= operatory</span><span class="sxs-lookup"><span data-stu-id="1da42-133">- and -= operators</span></span>](subtraction-operator.md)
