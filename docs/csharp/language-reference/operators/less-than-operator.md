---
title: '&lt; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: bb0f590bb547c4e632bd14c773f095435c8986f0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655949"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="07d53-102">&lt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="07d53-102">&lt; Operator (C# Reference)</span></span>

<span data-ttu-id="07d53-103">Operator "mniejsze niż" relacyjny `<` zwraca `true` Jeśli pierwszy argument operacji jest mniejszy niż drugi argument operacji `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="07d53-103">The "less than" relational operator `<` returns `true` if its first operand is less than its second operand, `false` otherwise.</span></span> <span data-ttu-id="07d53-104">Obsługa wszystkich typów liczbowych i wyliczenie `<` operatora.</span><span class="sxs-lookup"><span data-stu-id="07d53-104">All numeric and enumeration types support the `<` operator.</span></span> <span data-ttu-id="07d53-105">Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.</span><span class="sxs-lookup"><span data-stu-id="07d53-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="07d53-106">Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="07d53-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="07d53-107">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość.</span><span class="sxs-lookup"><span data-stu-id="07d53-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="07d53-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="07d53-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="07d53-109">W poniższym przykładzie pokazano użycie `<` operator:</span><span class="sxs-lookup"><span data-stu-id="07d53-109">The following example demonstrates the usage of the `<` operator:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a><span data-ttu-id="07d53-110">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="07d53-110">Operator overloadability</span></span>

<span data-ttu-id="07d53-111">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `<` operatora.</span><span class="sxs-lookup"><span data-stu-id="07d53-111">User-defined types can [overload](../keywords/operator.md) the `<` operator.</span></span> <span data-ttu-id="07d53-112">Jeśli typem przeciążenia operator "mniejsze niż" `<`, należy także przeciążyć [operator "większe niż"](greater-than-operator.md) `>`.</span><span class="sxs-lookup"><span data-stu-id="07d53-112">If a type overloads the "less than" operator `<`, it must also overload the ["greater than" operator](greater-than-operator.md) `>`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="07d53-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="07d53-113">C# language specification</span></span>

<span data-ttu-id="07d53-114">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="07d53-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07d53-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07d53-115">See also</span></span>

- [<span data-ttu-id="07d53-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="07d53-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07d53-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="07d53-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07d53-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="07d53-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="07d53-119"><=, operator</span><span class="sxs-lookup"><span data-stu-id="07d53-119"><= Operator</span></span>](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
