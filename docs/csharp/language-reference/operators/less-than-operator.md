---
title: < — Operator - C# odwołania
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: ab21e32b7609bc0c8753b42ccf8b6091bf3ad57b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286640"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="eb4e0-102">\< Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="eb4e0-102">\< Operator (C# Reference)</span></span>

<span data-ttu-id="eb4e0-103">Operator "mniejsze niż" relacyjny `<` zwraca `true` Jeśli pierwszy argument operacji jest mniejszy niż drugi argument operacji `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-103">The "less than" relational operator `<` returns `true` if its first operand is less than its second operand, `false` otherwise.</span></span> <span data-ttu-id="eb4e0-104">Obsługa wszystkich typów liczbowych i wyliczenie `<` operatora.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-104">All numeric and enumeration types support the `<` operator.</span></span> <span data-ttu-id="eb4e0-105">Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="eb4e0-106">Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="eb4e0-107">Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="eb4e0-108">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="eb4e0-109">W poniższym przykładzie pokazano użycie `<` operator:</span><span class="sxs-lookup"><span data-stu-id="eb4e0-109">The following example demonstrates the usage of the `<` operator:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a><span data-ttu-id="eb4e0-110">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="eb4e0-110">Operator overloadability</span></span>

<span data-ttu-id="eb4e0-111">Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `<` operatora.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-111">User-defined types can [overload](../keywords/operator.md) the `<` operator.</span></span> <span data-ttu-id="eb4e0-112">Jeśli typem przeciążenia operator "mniejsze niż" `<`, należy także przeciążyć [operator "większe niż"](greater-than-operator.md) `>`.</span><span class="sxs-lookup"><span data-stu-id="eb4e0-112">If a type overloads the "less than" operator `<`, it must also overload the ["greater than" operator](greater-than-operator.md) `>`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb4e0-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eb4e0-113">C# language specification</span></span>

<span data-ttu-id="eb4e0-114">Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb4e0-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb4e0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb4e0-115">See also</span></span>

- [<span data-ttu-id="eb4e0-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eb4e0-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eb4e0-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eb4e0-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eb4e0-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="eb4e0-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="eb4e0-119"><=, operator</span><span class="sxs-lookup"><span data-stu-id="eb4e0-119"><= Operator</span></span>](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
