---
title: '&amp;&amp; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 82442f50275f21e0a0748951dc50628a8d7e11bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243599"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="86777-102">&amp;&amp; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="86777-102">&amp;&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="86777-103">Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza operator logiczny oraz z jego [bool](../keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="86777-103">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="86777-104">Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`.</span><span class="sxs-lookup"><span data-stu-id="86777-104">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="86777-105">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="86777-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="86777-106">Jeśli pierwszy operand ma wartość `false`, drugi operand nie jest oceniany i wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="86777-106">If the first operand evaluates to `false`, the second operand is not evaluated and the result of operation is `false`.</span></span> <span data-ttu-id="86777-107">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="86777-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

<span data-ttu-id="86777-108">[Logicznego operatora AND](and-operator.md) `&` oblicza również operator logiczny oraz z jego `bool` operandów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="86777-108">The [logical AND operator](and-operator.md) `&` also computes the logical AND of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="86777-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="86777-109">Operator overloadability</span></span>

<span data-ttu-id="86777-110">Typ zdefiniowany przez użytkownika nie można przeciążyć operator logiczny AND warunkowe.</span><span class="sxs-lookup"><span data-stu-id="86777-110">A user-defined type cannot overload the conditional logical AND operator.</span></span> <span data-ttu-id="86777-111">Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operator logiczny oraz](and-operator.md) i [operatory true i false](../keywords/true-false-operators.md) w określony sposób, `&&` operacji mogą być obliczane w przypadku argumentów operacji typu.</span><span class="sxs-lookup"><span data-stu-id="86777-111">However, if a user-defined type overloads the [logical AND](and-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `&&` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="86777-112">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="86777-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="86777-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86777-113">C# language specification</span></span>

<span data-ttu-id="86777-114">Aby uzyskać więcej informacji, zobacz [warunkowego operatorów logicznych](~/_csharplang/spec/expressions.md#conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="86777-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86777-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86777-115">See also</span></span>

- [<span data-ttu-id="86777-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="86777-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="86777-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86777-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="86777-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="86777-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="86777-119">|| operator</span><span class="sxs-lookup"><span data-stu-id="86777-119">|| operator</span></span>](conditional-or-operator.md)
- [<span data-ttu-id="86777-120">\! operator</span><span class="sxs-lookup"><span data-stu-id="86777-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="86777-121">& — operator</span><span class="sxs-lookup"><span data-stu-id="86777-121">& operator</span></span>](and-operator.md)
