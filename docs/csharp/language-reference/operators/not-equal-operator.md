---
title: '! = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610180"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0fb3d-102">!= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0fb3d-102">!= Operator (C# Reference)</span></span>

<span data-ttu-id="0fb3d-103">Operator nierówności `!=` zwraca `true` argumentów nie są równe, `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-103">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="0fb3d-104">Dla argumentów operacji [wbudowanych typów](../keywords/built-in-types-table.md), wyrażenie `x != y` daje ten sam wynik jako wyrażenie `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-104">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="0fb3d-105">Aby uzyskać więcej informacji, zobacz [== — Operator](equality-comparison-operator.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-105">For more information, see the [== Operator](equality-comparison-operator.md) article.</span></span>

<span data-ttu-id="0fb3d-106">W poniższym przykładzie pokazano użycie `!=` operator:</span><span class="sxs-lookup"><span data-stu-id="0fb3d-106">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="0fb3d-107">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="0fb3d-107">Operator overloadability</span></span>

<span data-ttu-id="0fb3d-108">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `!=` operatora.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-108">User-defined types can [overload](../keywords/operator.md) the `!=` operator.</span></span> <span data-ttu-id="0fb3d-109">Jeśli typem przeciążenia operator nierówności `!=`, należy także przeciążyć [operatora równości](equality-comparison-operator.md) `==`.</span><span class="sxs-lookup"><span data-stu-id="0fb3d-109">If a type overloads the inequality operator `!=`, it must also overload the [equality operator](equality-comparison-operator.md) `==`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0fb3d-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0fb3d-110">C# language specification</span></span>

<span data-ttu-id="0fb3d-111">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fb3d-111">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0fb3d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fb3d-112">See also</span></span>

- [<span data-ttu-id="0fb3d-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0fb3d-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0fb3d-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0fb3d-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0fb3d-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0fb3d-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="0fb3d-116">Porównywanie równości</span><span class="sxs-lookup"><span data-stu-id="0fb3d-116">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
