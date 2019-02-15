---
title: '! Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/14/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 464bd658c9bf430191d84d3d5ad8d57173ab87c5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303715"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a813f-103">!</span><span class="sxs-lookup"><span data-stu-id="a813f-103">!</span></span> <span data-ttu-id="a813f-104">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a813f-104">operator (C# Reference)</span></span>

<span data-ttu-id="a813f-105">Operator logiczny negacji `!` jest Jednoargumentowy operator, który oblicza negacji logicznej jego [bool](../keywords/bool.md) operand.</span><span class="sxs-lookup"><span data-stu-id="a813f-105">The logical negation operator `!` is a unary operator that computes logical negation of its [bool](../keywords/bool.md) operand.</span></span> <span data-ttu-id="a813f-106">Oznacza to, tworzy `true`, jeśli argument jest `false`, i `false`, jeśli argument jest `true`:</span><span class="sxs-lookup"><span data-stu-id="a813f-106">That is, it produces `true`, if the operand is `false`, and `false`, if the operand is `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalNegationExamples.cs#Example)]

## <a name="operator-overloadability"></a><span data-ttu-id="a813f-107">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="a813f-107">Operator overloadability</span></span>

<span data-ttu-id="a813f-108">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `!` operatora.</span><span class="sxs-lookup"><span data-stu-id="a813f-108">User-defined types can [overload](../keywords/operator.md) the `!` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a813f-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a813f-109">C# language specification</span></span>

<span data-ttu-id="a813f-110">Aby uzyskać więcej informacji, zobacz [operator logiczny negacji](~/_csharplang/spec/expressions.md#logical-negation-operator) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="a813f-110">For more information, see the [Logical negation operator](~/_csharplang/spec/expressions.md#logical-negation-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a813f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a813f-111">See also</span></span>

- [<span data-ttu-id="a813f-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a813f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a813f-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a813f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a813f-114">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a813f-114">C# Operators</span></span>](index.md)