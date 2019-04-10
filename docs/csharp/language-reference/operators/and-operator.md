---
title: '&amp; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310047"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="684fe-102">&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="684fe-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="684fe-103">`&` Operator jest obsługiwany w dwóch formach: operatora address-of jednoargumentowy lub binarny operator logiczny.</span><span class="sxs-lookup"><span data-stu-id="684fe-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="684fe-104">Jednoargumentowy operator address-of</span><span class="sxs-lookup"><span data-stu-id="684fe-104">Unary address-of operator</span></span>

<span data-ttu-id="684fe-105">Jednoargumentowy `&` operator zwraca adres jego operandu.</span><span class="sxs-lookup"><span data-stu-id="684fe-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="684fe-106">Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie adresu zmiennej](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="684fe-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="684fe-107">Operator address-of `&` wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="684fe-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="684fe-108">Operator logiczny AND bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="684fe-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="684fe-109">Dla typów całkowitoliczbowych `&` operator oblicza logiczne bitowe AND argumentów:</span><span class="sxs-lookup"><span data-stu-id="684fe-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="684fe-110">W poprzednim przykładzie użyto literały binarne [wprowadzona w C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) i [udoskonalone w C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="684fe-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="684fe-111">Ponieważ operacje na typy całkowite są ogólnie dozwolone w Typy wyliczeniowe `&` obsługuje także operator [wyliczenia](../keywords/enum.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="684fe-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="684fe-112">Operator logiczny AND logiczne</span><span class="sxs-lookup"><span data-stu-id="684fe-112">Boolean logical AND operator</span></span>

<span data-ttu-id="684fe-113">Dla [bool](../keywords/bool.md) operandów, `&` operator oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="684fe-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="684fe-114">Wynik `x & y` jest `true` Jeśli oba `x` i `y` są `true`.</span><span class="sxs-lookup"><span data-stu-id="684fe-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="684fe-115">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="684fe-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="684fe-116">`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="684fe-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="684fe-117">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="684fe-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="684fe-118">[Operatora warunkowego i](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` również oblicza logicznego i jego operandu, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="684fe-118">The [conditional AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="684fe-119">Dla argumentów bool dopuszczającego wartość null, zachowanie `&` operator jest zgodne z logiką przechowywanymi w trzech SQL.</span><span class="sxs-lookup"><span data-stu-id="684fe-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="684fe-120">Aby uzyskać więcej informacji, zobacz [Nullable logiczna operatorów logicznych](boolean-logical-operators.md#nullable-boolean-logical-operators) części [logiczna operatorów logicznych](boolean-logical-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="684fe-120">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="684fe-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="684fe-121">Operator overloadability</span></span>

<span data-ttu-id="684fe-122">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) pliku binarnego `&` operatora.</span><span class="sxs-lookup"><span data-stu-id="684fe-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="684fe-123">Gdy dane binarne `&` operator jest przeciążony, [operator przypisania AND](and-assignment-operator.md) `&=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="684fe-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="684fe-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="684fe-124">C# language specification</span></span>

<span data-ttu-id="684fe-125">Aby uzyskać więcej informacji, zobacz [operatora address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) i [operatorów logicznych](~/_csharplang/spec/expressions.md#logical-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="684fe-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="684fe-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="684fe-126">See also</span></span>

- [<span data-ttu-id="684fe-127">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="684fe-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="684fe-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="684fe-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="684fe-129">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="684fe-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="684fe-130">Operatory logiczne (Boolean)</span><span class="sxs-lookup"><span data-stu-id="684fe-130">Boolean logical operators</span></span>](boolean-logical-operators.md)
- [<span data-ttu-id="684fe-131">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="684fe-131">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="684fe-132">| — Operator</span><span class="sxs-lookup"><span data-stu-id="684fe-132">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="684fe-133">Operator ^</span><span class="sxs-lookup"><span data-stu-id="684fe-133">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="684fe-134">~ - Operator</span><span class="sxs-lookup"><span data-stu-id="684fe-134">~ operator</span></span>](bitwise-complement-operator.md)
