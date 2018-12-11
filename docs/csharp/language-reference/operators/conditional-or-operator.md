---
title: '|| Operator - C# odwołania'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: f4bb7ada12fbcebcb90fb7cd22d6e6bccad5fb57
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244573"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="54b57-102">Operator || (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="54b57-102">|| Operator (C# Reference)</span></span>

<span data-ttu-id="54b57-103">Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza logiczne OR z jego [bool](../keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="54b57-103">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its [bool](../keywords/bool.md) operands.</span></span> <span data-ttu-id="54b57-104">Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="54b57-104">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="54b57-105">W przeciwnym razie wynikiem jest `false`.</span><span class="sxs-lookup"><span data-stu-id="54b57-105">Otherwise, the result is `false`.</span></span> <span data-ttu-id="54b57-106">Jeśli pierwszy operand ma wartość `true`, drugi operand nie jest oceniany i wynik operacji jest `true`.</span><span class="sxs-lookup"><span data-stu-id="54b57-106">If the first operand evaluates to `true`, the second operand is not evaluated and the result of operation is `true`.</span></span> <span data-ttu-id="54b57-107">Poniższy przykład przedstawia tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="54b57-107">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

<span data-ttu-id="54b57-108">[Operator logiczny OR](or-operator.md) `|` oblicza również logiczne OR z jego `bool` operandów, ale zawsze ocenia oba operandy.</span><span class="sxs-lookup"><span data-stu-id="54b57-108">The [logical OR operator](or-operator.md) `|` also computes the logical OR of its `bool` operands, but always evaluates both operands.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="54b57-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="54b57-109">Operator overloadability</span></span>

<span data-ttu-id="54b57-110">Typ zdefiniowany przez użytkownika nie można przeciążyć operator logiczny OR warunkowe.</span><span class="sxs-lookup"><span data-stu-id="54b57-110">A user-defined type cannot overload the conditional logical OR operator.</span></span> <span data-ttu-id="54b57-111">Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [logiczne OR](or-operator.md) i [operatory true i false](../keywords/true-false-operators.md) w określony sposób, `||` operacji mogą być obliczane w przypadku argumentów operacji typu.</span><span class="sxs-lookup"><span data-stu-id="54b57-111">However, if a user-defined type overloads the [logical OR](or-operator.md) and [true and false operators](../keywords/true-false-operators.md) in a certain way, the `||` operation can be evaluated for the operands of that type.</span></span> <span data-ttu-id="54b57-112">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="54b57-112">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="54b57-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="54b57-113">C# language specification</span></span>

<span data-ttu-id="54b57-114">Aby uzyskać więcej informacji, zobacz [warunkowego operatorów logicznych](~/_csharplang/spec/expressions.md#conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="54b57-114">For more information, see the [Conditional logical operators](~/_csharplang/spec/expressions.md#conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54b57-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54b57-115">See also</span></span>

- [<span data-ttu-id="54b57-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="54b57-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54b57-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="54b57-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54b57-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="54b57-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="54b57-119">& & — operator</span><span class="sxs-lookup"><span data-stu-id="54b57-119">&& operator</span></span>](conditional-and-operator.md)
- [<span data-ttu-id="54b57-120">\! operator</span><span class="sxs-lookup"><span data-stu-id="54b57-120">! operator</span></span>](logical-negation-operator.md)
- [<span data-ttu-id="54b57-121">| operator</span><span class="sxs-lookup"><span data-stu-id="54b57-121">| operator</span></span>](or-operator.md)
