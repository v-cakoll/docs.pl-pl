---
title: + Operator (odwołanie w C#)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: ae2774d96bc50afa271fffdea445e640e68c3647
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192307"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a1447-102">+ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a1447-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="a1447-103">`+` Operator jest obsługiwany w dwóch formach: jednoargumentowe plus operatora lub operator binarny dodawania.</span><span class="sxs-lookup"><span data-stu-id="a1447-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

<span data-ttu-id="a1447-104">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) jednoargumentowy i danych binarnych `+` operatorów.</span><span class="sxs-lookup"><span data-stu-id="a1447-104">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="a1447-105">Gdy dane binarne `+` operator jest przeciążony, [operator przypisania dodawania](addition-assignment-operator.md) `+=` jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="a1447-105">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="a1447-106">Jednoargumentowy operator plus</span><span class="sxs-lookup"><span data-stu-id="a1447-106">Unary plus operator</span></span>

<span data-ttu-id="a1447-107">Jednoargumentowy `+` operator zwraca wartość swojego operandu.</span><span class="sxs-lookup"><span data-stu-id="a1447-107">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="a1447-108">Jest ona obsługiwana przez wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="a1447-108">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="a1447-109">Dodawanie numeryczne</span><span class="sxs-lookup"><span data-stu-id="a1447-109">Numeric addition</span></span>

<span data-ttu-id="a1447-110">Dla typów liczbowych `+` operator oblicza sumę argumentów:</span><span class="sxs-lookup"><span data-stu-id="a1447-110">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="a1447-111">{1&gt;Łączenie ciągów&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a1447-111">String concatenation</span></span>

<span data-ttu-id="a1447-112">Kiedy jeden lub obydwa operandy są typu [ciąg](../keywords/string.md), `+` operator łączy ciągów reprezentujących argumentów:</span><span class="sxs-lookup"><span data-stu-id="a1447-112">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="a1447-113">Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodny sposób na ciągi formatu:</span><span class="sxs-lookup"><span data-stu-id="a1447-113">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="a1447-114">Delegatów</span><span class="sxs-lookup"><span data-stu-id="a1447-114">Delegate combination</span></span>

<span data-ttu-id="a1447-115">Aby uzyskać [delegować](../keywords/delegate.md) typów `+` operator zwraca nowe wystąpienie delegata, gdy wywoływany, wywołuje pierwszy operand, a następnie wywołuje drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="a1447-115">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="a1447-116">Jeśli którykolwiek z argumentów jest `null`, `+` operator zwraca wartość innego operandu (które mogą być również `null`).</span><span class="sxs-lookup"><span data-stu-id="a1447-116">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="a1447-117">W poniższym przykładzie pokazano, jak delegaty można łączyć z `+` operator:</span><span class="sxs-lookup"><span data-stu-id="a1447-117">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="a1447-118">Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1447-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a1447-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a1447-119">C# language specification</span></span>

<span data-ttu-id="a1447-120">Aby uzyskać więcej informacji, zobacz [jednoargumentowe plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1447-120">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1447-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1447-121">See also</span></span>

- [<span data-ttu-id="a1447-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a1447-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1447-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1447-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a1447-124">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a1447-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="a1447-125">Interpolacja ciągów</span><span class="sxs-lookup"><span data-stu-id="a1447-125">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="a1447-126">Instrukcje: łączenie wielu ciągów</span><span class="sxs-lookup"><span data-stu-id="a1447-126">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="a1447-127">Delegaty</span><span class="sxs-lookup"><span data-stu-id="a1447-127">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="a1447-128">Checked i unchecked</span><span class="sxs-lookup"><span data-stu-id="a1447-128">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
