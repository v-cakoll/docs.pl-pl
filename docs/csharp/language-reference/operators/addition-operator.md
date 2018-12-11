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
ms.openlocfilehash: 92e20dad8ae6358f71137e955bb80e3641a66a54
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237756"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4a139-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4a139-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="4a139-103">`+` Operator jest obsługiwany w dwóch formach: jednoargumentowe plus operatora lub operator binarny dodawania.</span><span class="sxs-lookup"><span data-stu-id="4a139-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="4a139-104">Jednoargumentowy operator plus</span><span class="sxs-lookup"><span data-stu-id="4a139-104">Unary plus operator</span></span>

<span data-ttu-id="4a139-105">Jednoargumentowy `+` operator zwraca wartość swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="4a139-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="4a139-106">Jest ona obsługiwana przez wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="4a139-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="4a139-107">Dodawanie numeryczne</span><span class="sxs-lookup"><span data-stu-id="4a139-107">Numeric addition</span></span>

<span data-ttu-id="4a139-108">Dla typów liczbowych `+` operator oblicza sumę argumentów:</span><span class="sxs-lookup"><span data-stu-id="4a139-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="4a139-109">{1&gt;Łączenie ciągów&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4a139-109">String concatenation</span></span>

<span data-ttu-id="4a139-110">Kiedy jeden lub obydwa operandy są typu [ciąg](../keywords/string.md), `+` operator łączy ciągów reprezentujących argumentów:</span><span class="sxs-lookup"><span data-stu-id="4a139-110">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="4a139-111">Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodny sposób na ciągi formatu:</span><span class="sxs-lookup"><span data-stu-id="4a139-111">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="4a139-112">Delegatów</span><span class="sxs-lookup"><span data-stu-id="4a139-112">Delegate combination</span></span>

<span data-ttu-id="4a139-113">Aby uzyskać [delegować](../keywords/delegate.md) typów `+` operator zwraca nowe wystąpienie delegata, gdy wywoływany, wywołuje pierwszy operand, a następnie wywołuje drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="4a139-113">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="4a139-114">Jeśli którykolwiek z argumentów jest `null`, `+` operator zwraca wartość innego operandu (które mogą być również `null`).</span><span class="sxs-lookup"><span data-stu-id="4a139-114">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="4a139-115">W poniższym przykładzie pokazano, jak delegaty można łączyć z `+` operator:</span><span class="sxs-lookup"><span data-stu-id="4a139-115">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="4a139-116">Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a139-116">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4a139-117">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="4a139-117">Operator overloadability</span></span>

<span data-ttu-id="4a139-118">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) jednoargumentowy i danych binarnych `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="4a139-118">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="4a139-119">Gdy dane binarne `+` operator jest przeciążony, [operator przypisania dodawania](addition-assignment-operator.md) `+=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="4a139-119">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4a139-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4a139-120">C# language specification</span></span>

<span data-ttu-id="4a139-121">Aby uzyskać więcej informacji, zobacz [jednoargumentowe plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a139-121">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a139-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a139-122">See also</span></span>

- [<span data-ttu-id="4a139-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4a139-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4a139-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4a139-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4a139-125">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="4a139-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4a139-126">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="4a139-126">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="4a139-127">Instrukcje: Łączenie wielu ciągów</span><span class="sxs-lookup"><span data-stu-id="4a139-127">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="4a139-128">Delegaty</span><span class="sxs-lookup"><span data-stu-id="4a139-128">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="4a139-129">Checked i unchecked</span><span class="sxs-lookup"><span data-stu-id="4a139-129">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
