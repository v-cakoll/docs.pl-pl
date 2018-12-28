---
title: '&lt;= — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 30f42de68667756a8233fef4241bfd74ed4eff2a
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656092"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="5f79c-102">&lt;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5f79c-102">&lt;= Operator (C# Reference)</span></span>

<span data-ttu-id="5f79c-103">"Mniejsze niż lub równe" operator relacyjny `<=` zwraca `true` Jeśli pierwszy argument operacji jest mniejszy niż drugi argument operacji `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="5f79c-103">The "less than or equal" relational operator `<=` returns `true` if its first operand is less than or equal to its second operand, `false` otherwise.</span></span> <span data-ttu-id="5f79c-104">Obsługa wszystkich typów liczbowych i wyliczenie `<=` operatora.</span><span class="sxs-lookup"><span data-stu-id="5f79c-104">All numeric and enumeration types support the `<=` operator.</span></span> <span data-ttu-id="5f79c-105">Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.</span><span class="sxs-lookup"><span data-stu-id="5f79c-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="5f79c-106">Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="5f79c-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="5f79c-107">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość.</span><span class="sxs-lookup"><span data-stu-id="5f79c-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="5f79c-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="5f79c-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="5f79c-109">W poniższym przykładzie pokazano użycie `<=` operator:</span><span class="sxs-lookup"><span data-stu-id="5f79c-109">The following example demonstrates the usage of the `<=` operator:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="5f79c-110">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="5f79c-110">Operator overloadability</span></span>

<span data-ttu-id="5f79c-111">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `<=` operatora.</span><span class="sxs-lookup"><span data-stu-id="5f79c-111">User-defined types can [overload](../keywords/operator.md) the `<=` operator.</span></span> <span data-ttu-id="5f79c-112">Jeśli typem przeciążenia operator "mniejsze niż lub równe" `<=`, należy także przeciążyć [operator "większe lub równe"](greater-than-equal-operator.md) `>=`.</span><span class="sxs-lookup"><span data-stu-id="5f79c-112">If a type overloads the "less than or equal" operator `<=`, it must also overload the ["greater than or equal" operator](greater-than-equal-operator.md) `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5f79c-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5f79c-113">C# language specification</span></span>

<span data-ttu-id="5f79c-114">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f79c-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f79c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f79c-115">See also</span></span>

- [<span data-ttu-id="5f79c-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5f79c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5f79c-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5f79c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5f79c-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5f79c-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="5f79c-119"><, operator</span><span class="sxs-lookup"><span data-stu-id="5f79c-119">< Operator</span></span>](less-than-operator.md)
- [<span data-ttu-id="5f79c-120">==, operator</span><span class="sxs-lookup"><span data-stu-id="5f79c-120">== Operator</span></span>](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
