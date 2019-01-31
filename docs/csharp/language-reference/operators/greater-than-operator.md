---
title: '> Operator - C# odwołania'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 3b036c491d9663bf4ab0971d84a0a8d58d902ee6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287212"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ed4d2-102">Operator > (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ed4d2-102">> Operator (C# Reference)</span></span>

<span data-ttu-id="ed4d2-103">"Większe niż" operator relacyjny `>` zwraca `true` Jeśli pierwszy argument operacji jest większy niż drugi argument operacji `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-103">The "greater than" relational operator `>` returns `true` if its first operand is greater than its second operand, `false` otherwise.</span></span> <span data-ttu-id="ed4d2-104">Obsługa wszystkich typów liczbowych i wyliczenie `>` operatora.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-104">All numeric and enumeration types support the `>` operator.</span></span> <span data-ttu-id="ed4d2-105">Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="ed4d2-106">Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="ed4d2-107">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="ed4d2-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="ed4d2-109">W poniższym przykładzie pokazano użycie `>` operator:</span><span class="sxs-lookup"><span data-stu-id="ed4d2-109">The following example demonstrates the usage of the `>` operator:</span></span>

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="operator-overloadability"></a><span data-ttu-id="ed4d2-110">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="ed4d2-110">Operator overloadability</span></span>

<span data-ttu-id="ed4d2-111">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `>` operatora.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-111">User-defined types can [overload](../keywords/operator.md) the `>` operator.</span></span> <span data-ttu-id="ed4d2-112">Jeśli typem przeciążenia operatora "większe niż" `>`, należy także przeciążyć [operator "mniejsze niż"](less-than-operator.md) `<`.</span><span class="sxs-lookup"><span data-stu-id="ed4d2-112">If a type overloads the "greater than" operator `>`, it must also overload the ["less than" operator](less-than-operator.md) `<`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ed4d2-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ed4d2-113">C# language specification</span></span>

<span data-ttu-id="ed4d2-114">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ed4d2-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed4d2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed4d2-115">See also</span></span>

- [<span data-ttu-id="ed4d2-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ed4d2-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ed4d2-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ed4d2-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ed4d2-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ed4d2-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="ed4d2-119">>=, operator</span><span class="sxs-lookup"><span data-stu-id="ed4d2-119">>= Operator</span></span>](greater-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
