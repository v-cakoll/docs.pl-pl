---
title: '&amp; Operator (odwołanie w C#)'
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510981"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="1455d-102">&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1455d-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="1455d-103">`&` Operator jest obsługiwany w dwóch formach: operatora address-of jednoargumentowy lub binarny operator logiczny.</span><span class="sxs-lookup"><span data-stu-id="1455d-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="1455d-104">Jednoargumentowy operator address-of</span><span class="sxs-lookup"><span data-stu-id="1455d-104">Unary address-of operator</span></span>

<span data-ttu-id="1455d-105">Jednoargumentowy `&` operator zwraca adres jego operandu.</span><span class="sxs-lookup"><span data-stu-id="1455d-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="1455d-106">Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie adresu zmiennej](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="1455d-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="1455d-107">Operator address-of `&` wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1455d-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="1455d-108">Operator logiczny AND bitowa liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="1455d-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="1455d-109">Dla typów całkowitoliczbowych `&` operator oblicza logiczne bitowe AND argumentów:</span><span class="sxs-lookup"><span data-stu-id="1455d-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="1455d-110">W poprzednim przykładzie użyto literały binarne [wprowadzona w C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) i [udoskonalone w C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="1455d-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="1455d-111">Ponieważ operacje na typy całkowite są ogólnie dozwolone w Typy wyliczeniowe `&` obsługuje także operator [wyliczenia](../keywords/enum.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="1455d-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="1455d-112">Operator logiczny AND logiczne</span><span class="sxs-lookup"><span data-stu-id="1455d-112">Boolean logical AND operator</span></span>

<span data-ttu-id="1455d-113">Dla [bool](../keywords/bool.md) operandów, `&` operator oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="1455d-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="1455d-114">Wynik `x & y` jest `true` Jeśli oba `x` i `y` są `true`.</span><span class="sxs-lookup"><span data-stu-id="1455d-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="1455d-115">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="1455d-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="1455d-116">`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="1455d-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="1455d-117">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="1455d-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="1455d-118">[Operatora warunkowego i](conditional-and-operator.md) `&&` również oblicza logicznym, a z argumentów, ale wartość drugiego operandu tylko wtedy, gdy pierwszy operand ma wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="1455d-118">The [conditional AND operator](conditional-and-operator.md) `&&` also computes the logical AND of its operands, but evaluates the second operand only if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="1455d-119">Dla argumentów bool dopuszczającego wartość null, zachowanie `&` operator jest zgodne z logiką przechowywanymi w trzech SQL.</span><span class="sxs-lookup"><span data-stu-id="1455d-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="1455d-120">Aby uzyskać więcej informacji, zobacz [bool? typu](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="1455d-120">For more information, see the [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1455d-121">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="1455d-121">Operator overloadability</span></span>

<span data-ttu-id="1455d-122">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) pliku binarnego `&` operatora.</span><span class="sxs-lookup"><span data-stu-id="1455d-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="1455d-123">Gdy dane binarne `&` operator jest przeciążony, [operator przypisania AND](and-assignment-operator.md) `&=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="1455d-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1455d-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1455d-124">C# language specification</span></span>

<span data-ttu-id="1455d-125">Aby uzyskać więcej informacji, zobacz [operatora address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) i [operatorów logicznych](~/_csharplang/spec/expressions.md#logical-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1455d-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1455d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1455d-126">See also</span></span>

- [<span data-ttu-id="1455d-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1455d-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1455d-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1455d-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1455d-129">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1455d-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="1455d-130">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="1455d-130">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="1455d-131">| operator</span><span class="sxs-lookup"><span data-stu-id="1455d-131">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="1455d-132">^ — operator</span><span class="sxs-lookup"><span data-stu-id="1455d-132">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="1455d-133">~ — operator</span><span class="sxs-lookup"><span data-stu-id="1455d-133">~ operator</span></span>](bitwise-complement-operator.md)
- [<span data-ttu-id="1455d-134">& & — operator</span><span class="sxs-lookup"><span data-stu-id="1455d-134">&& operator</span></span>](conditional-and-operator.md)
