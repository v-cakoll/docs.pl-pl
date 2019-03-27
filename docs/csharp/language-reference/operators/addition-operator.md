---
title: + Operator - C# odwołania
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504473"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a8429-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a8429-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="a8429-103">`+` Operator jest obsługiwany w dwóch formach: jednoargumentowe plus operatora lub operator binarny dodawania.</span><span class="sxs-lookup"><span data-stu-id="a8429-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="a8429-104">Jednoargumentowy operator plus</span><span class="sxs-lookup"><span data-stu-id="a8429-104">Unary plus operator</span></span>

<span data-ttu-id="a8429-105">Jednoargumentowy `+` operator zwraca wartość swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="a8429-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="a8429-106">Jest ona obsługiwana przez wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="a8429-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="a8429-107">Dodawanie numeryczne</span><span class="sxs-lookup"><span data-stu-id="a8429-107">Numeric addition</span></span>

<span data-ttu-id="a8429-108">Dla typów liczbowych `+` operator oblicza sumę argumentów:</span><span class="sxs-lookup"><span data-stu-id="a8429-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

<span data-ttu-id="a8429-109">Aby uzyskać więcej informacji na temat operatory arytmetyczne zobaczyć [operatorów arytmetycznych](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a8429-109">For more information about arithmetic operators, see [Arithmetic operators](arithmetic-operators.md).</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="a8429-110">{1&gt;Łączenie ciągów&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a8429-110">String concatenation</span></span>

<span data-ttu-id="a8429-111">Kiedy jeden lub obydwa operandy są typu [ciąg](../keywords/string.md), `+` operator łączy ciągów reprezentujących argumentów:</span><span class="sxs-lookup"><span data-stu-id="a8429-111">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="a8429-112">Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodny sposób na ciągi formatu:</span><span class="sxs-lookup"><span data-stu-id="a8429-112">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="a8429-113">Delegatów</span><span class="sxs-lookup"><span data-stu-id="a8429-113">Delegate combination</span></span>

<span data-ttu-id="a8429-114">Aby uzyskać [delegować](../keywords/delegate.md) typów `+` operator zwraca nowe wystąpienie delegata, gdy wywoływany, wywołuje pierwszy operand, a następnie wywołuje drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="a8429-114">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="a8429-115">Jeśli którykolwiek z argumentów jest `null`, `+` operator zwraca wartość innego operandu (które mogą być również `null`).</span><span class="sxs-lookup"><span data-stu-id="a8429-115">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="a8429-116">W poniższym przykładzie pokazano, jak delegaty można łączyć z `+` operator:</span><span class="sxs-lookup"><span data-stu-id="a8429-116">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="a8429-117">Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8429-117">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a8429-118">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="a8429-118">Operator overloadability</span></span>

<span data-ttu-id="a8429-119">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) jednoargumentowy i danych binarnych `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="a8429-119">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="a8429-120">Gdy dane binarne `+` operator jest przeciążony, [operator przypisania dodawania](addition-assignment-operator.md) `+=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="a8429-120">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a8429-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a8429-121">C# language specification</span></span>

<span data-ttu-id="a8429-122">Aby uzyskać więcej informacji, zobacz [jednoargumentowe plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8429-122">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8429-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8429-123">See also</span></span>

- [<span data-ttu-id="a8429-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a8429-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a8429-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a8429-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a8429-126">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a8429-126">C# Operators</span></span>](index.md)
- [<span data-ttu-id="a8429-127">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="a8429-127">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="a8429-128">Instrukcje: Łączenie wielu ciągów</span><span class="sxs-lookup"><span data-stu-id="a8429-128">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="a8429-129">Delegaty</span><span class="sxs-lookup"><span data-stu-id="a8429-129">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="a8429-130">Checked i unchecked</span><span class="sxs-lookup"><span data-stu-id="a8429-130">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
