---
title: + Operatory i + = — C# odwołanie
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
ms.openlocfilehash: c8452ab1f90bb2873a591b483b5432311a9f9b79
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239629"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="33f73-102">Operatory + i + = (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="33f73-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="33f73-103">Operatory `+` i `+=` są obsługiwane przez wbudowane typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) , typ [ciągu](../builtin-types/reference-types.md#the-string-type) i typy [delegatów](../builtin-types/reference-types.md#the-delegate-type) .</span><span class="sxs-lookup"><span data-stu-id="33f73-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="33f73-104">Aby uzyskać informacje o operatorze arytmetycznej `+`, zobacz [operatory jednoargumentowe Plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) oraz [operator dodawania +](arithmetic-operators.md#addition-operator-) sekcje w artykule [Operatory arytmetyczne](arithmetic-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="33f73-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="33f73-105">{1&gt;Łączenie ciągów&lt;1}</span><span class="sxs-lookup"><span data-stu-id="33f73-105">String concatenation</span></span>

<span data-ttu-id="33f73-106">Gdy jeden lub oba operandy są typu [String](../builtin-types/reference-types.md#the-string-type), operator `+` łączy reprezentacje ciągów argumentów operacji:</span><span class="sxs-lookup"><span data-stu-id="33f73-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="33f73-107">Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodniejszy sposób formatowania ciągów:</span><span class="sxs-lookup"><span data-stu-id="33f73-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="33f73-108">Połączenie delegata</span><span class="sxs-lookup"><span data-stu-id="33f73-108">Delegate combination</span></span>

<span data-ttu-id="33f73-109">W przypadku operandów tego samego typu [delegata](../builtin-types/reference-types.md#the-delegate-type) operator `+` zwraca nowe wystąpienie delegata, które po wywołaniu wywołuje argument operacji po lewej stronie, a następnie wywołuje operand z prawej strony.</span><span class="sxs-lookup"><span data-stu-id="33f73-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="33f73-110">Jeśli którykolwiek z operandów jest `null`, operator `+` zwróci wartość innego operandu (co również może być `null`).</span><span class="sxs-lookup"><span data-stu-id="33f73-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="33f73-111">Poniższy przykład pokazuje, jak można łączyć delegatów z operatorem `+`:</span><span class="sxs-lookup"><span data-stu-id="33f73-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="33f73-112">Aby przeprowadzić usuwanie delegata, użyj [operatora`-`](subtraction-operator.md#delegate-removal).</span><span class="sxs-lookup"><span data-stu-id="33f73-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="33f73-113">Aby uzyskać więcej informacji na temat typów delegatów, zobacz [delegats](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="33f73-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="33f73-114">Operator przypisania dodawania + =</span><span class="sxs-lookup"><span data-stu-id="33f73-114">Addition assignment operator +=</span></span>

<span data-ttu-id="33f73-115">Wyrażenie używające operatora `+=`, takie jak</span><span class="sxs-lookup"><span data-stu-id="33f73-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="33f73-116">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="33f73-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="33f73-117">z tą różnicą, że `x` są oceniane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="33f73-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="33f73-118">Poniższy przykład ilustruje użycie operatora `+=`:</span><span class="sxs-lookup"><span data-stu-id="33f73-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="33f73-119">Możesz również użyć operatora `+=`, aby określić metodę procedury obsługi zdarzeń podczas subskrybowania [zdarzenia](../keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="33f73-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="33f73-120">Aby uzyskać więcej informacji, zobacz [How to: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="33f73-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="33f73-121">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="33f73-121">Operator overloadability</span></span>

<span data-ttu-id="33f73-122">Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operator `+`.</span><span class="sxs-lookup"><span data-stu-id="33f73-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="33f73-123">Gdy operator `+` binarny jest przeciążony, operator `+=` jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="33f73-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="33f73-124">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora `+=`.</span><span class="sxs-lookup"><span data-stu-id="33f73-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="33f73-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="33f73-125">C# language specification</span></span>

<span data-ttu-id="33f73-126">Aby uzyskać więcej informacji, zobacz sekcje [jednoargumentowe Plus](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="33f73-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33f73-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33f73-127">See also</span></span>

- [<span data-ttu-id="33f73-128">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="33f73-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="33f73-129">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="33f73-129">C# operators</span></span>](index.md)
- [<span data-ttu-id="33f73-130">Jak połączyć wiele ciągów</span><span class="sxs-lookup"><span data-stu-id="33f73-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="33f73-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="33f73-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="33f73-132">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="33f73-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="33f73-133">Operatory-and-=</span><span class="sxs-lookup"><span data-stu-id="33f73-133">- and -= operators</span></span>](subtraction-operator.md)
