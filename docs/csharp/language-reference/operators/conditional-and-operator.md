---
title: '&amp;&amp; Operator (odwołanie w C#)'
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: d0e6d9a5aedc7dc87393e3dea070bf442b3268dc
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43529238"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="5a969-102">&amp;&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5a969-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="5a969-103">Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza operator logiczny oraz z jego [bool](../keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="5a969-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="5a969-104">Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="5a969-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="5a969-105">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="5a969-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5a969-106">Jeśli pierwszy operand ma wartość `false`, drugi operand nie jest oceniany i wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="5a969-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="5a969-107">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="5a969-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="5a969-108">[Logicznego operatora AND](and-operator.md) `&` oblicza również operator logiczny oraz z jego `bool` operandów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="5a969-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5a969-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="5a969-109">Operator overloadability</span></span>

<span data-ttu-id="5a969-110">Typ zdefiniowany przez użytkownika nie można przeciążyć operator logiczny AND warunkowe.</span><span class="sxs-lookup"><span data-stu-id="5a969-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="5a969-111">Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operator logiczny oraz](and-operator.md), [true](../keywords/true-operator.md), i [false](../keywords/false-operator.md) operatorów w określony sposób, `&&` operacja może zostać obliczone dla Operandy typu.</span><span class="sxs-lookup"><span data-stu-id="5a969-111">However, if a user-defined type overloads the [logical AND](and-operator.md), [true](../keywords/true-operator.md), and [false](../keywords/false-operator.md) operators in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="5a969-112">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a969-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5a969-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a969-113">C# language specification</span></span>

<span data-ttu-id="5a969-114">Aby uzyskać więcej informacji, zobacz [warunkowego operatorów logicznych](~/_csharplang/spec/expressions.md#conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a969-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a969-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a969-115">See also</span></span>

- [<span data-ttu-id="5a969-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a969-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5a969-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5a969-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5a969-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5a969-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="5a969-119">|| operator</span><span class="sxs-lookup"><span data-stu-id="5a969-119">|| operator</span></span>](conditional-or-operator.md)
- [<span data-ttu-id="5a969-120">\! operator</span><span class="sxs-lookup"><span data-stu-id="5a969-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="5a969-121">& — operator</span><span class="sxs-lookup"><span data-stu-id="5a969-121">& operator</span></span>](and-operator.md)
