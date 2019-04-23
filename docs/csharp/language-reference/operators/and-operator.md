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
ms.openlocfilehash: 7aac0af93efb3d72496df13a64afb7840993b22c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980645"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="ec9a1-102">&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ec9a1-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="ec9a1-103">`&` Operator jest obsługiwany w dwóch formach: operatora address-of jednoargumentowy lub binarny operator logiczny.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="ec9a1-104">Jednoargumentowy operator address-of</span><span class="sxs-lookup"><span data-stu-id="ec9a1-104">Unary address-of operator</span></span>

<span data-ttu-id="ec9a1-105">Jednoargumentowy `&` operator zwraca adres jego operandu.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="ec9a1-106">Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie adresu zmiennej](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="ec9a1-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="ec9a1-107">Operator address-of `&` wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="ec9a1-108">Operator logiczny AND bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="ec9a1-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="ec9a1-109">Dla typów całkowitoliczbowych `&` operator oblicza logiczne bitowe AND argumentów:</span><span class="sxs-lookup"><span data-stu-id="ec9a1-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="ec9a1-110">W poprzednim przykładzie użyto literały binarne [wprowadzona w C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) i [udoskonalone w C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="ec9a1-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="ec9a1-111">Ponieważ operacje na typy całkowite są ogólnie dozwolone w Typy wyliczeniowe `&` obsługuje także operator [wyliczenia](../keywords/enum.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="ec9a1-112">Operator logiczny AND logiczne</span><span class="sxs-lookup"><span data-stu-id="ec9a1-112">Boolean logical AND operator</span></span>

<span data-ttu-id="ec9a1-113">Dla [bool](../keywords/bool.md) operandów, `&` operator oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="ec9a1-114">Wynik `x & y` jest `true` Jeśli oba `x` i `y` są `true`.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="ec9a1-115">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="ec9a1-116">`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="ec9a1-117">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="ec9a1-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="ec9a1-118">[Operatora warunkowego i](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` również oblicza logicznego i jego operandu, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-118">The [conditional AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="ec9a1-119">Dla argumentów bool dopuszczającego wartość null, zachowanie `&` operator jest zgodne z logiką przechowywanymi w trzech SQL.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="ec9a1-120">Aby uzyskać więcej informacji, zobacz [Nullable logiczna operatorów logicznych](boolean-logical-operators.md#nullable-boolean-logical-operators) części [logiczna operatorów logicznych](boolean-logical-operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-120">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ec9a1-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="ec9a1-121">Operator overloadability</span></span>

<span data-ttu-id="ec9a1-122">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) pliku binarnego `&` operatora.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="ec9a1-123">Gdy dane binarne `&` operator jest przeciążony, [operator przypisania AND](and-assignment-operator.md) `&=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="ec9a1-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ec9a1-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ec9a1-124">C# language specification</span></span>

<span data-ttu-id="ec9a1-125">Aby uzyskać więcej informacji, zobacz [operatora address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) i [operatorów logicznych](~/_csharplang/spec/expressions.md#logical-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec9a1-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec9a1-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec9a1-126">See also</span></span>

- [<span data-ttu-id="ec9a1-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ec9a1-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ec9a1-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ec9a1-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ec9a1-129">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ec9a1-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ec9a1-130">Operatory logiczne logiczne</span><span class="sxs-lookup"><span data-stu-id="ec9a1-130">Boolean logical operators</span></span>](boolean-logical-operators.md)
- [<span data-ttu-id="ec9a1-131">Bitowe i operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="ec9a1-131">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
- [<span data-ttu-id="ec9a1-132">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="ec9a1-132">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)