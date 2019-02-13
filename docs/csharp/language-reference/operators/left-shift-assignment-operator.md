---
title: << = — operator - C# odwołania
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219454"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4d133-102">\<\<= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="4d133-102">\<\<= operator (C# Reference)</span></span>

<span data-ttu-id="4d133-103">Operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="4d133-103">The left-shift assignment operator.</span></span>

<span data-ttu-id="4d133-104">Usługi za pomocą wyrażenia `<<=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="4d133-104">An expression using the `<<=` operator, such as</span></span>

```csharp
x <<= y
```

<span data-ttu-id="4d133-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="4d133-105">is equivalent to</span></span>

```csharp
x = x << y
```

<span data-ttu-id="4d133-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4d133-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="4d133-107">[ `<<` Operator](left-shift-operator.md) pierwszy argument operacji lewo o liczbę bitów definicją drugim argumentem operacji przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="4d133-107">The [`<<` operator](left-shift-operator.md) shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="4d133-108">W poniższym przykładzie pokazano użycie `<<=` operator:</span><span class="sxs-lookup"><span data-stu-id="4d133-108">The following example demonstrates the usage of the `<<=` operator:</span></span>

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="4d133-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="4d133-109">Operator overloadability</span></span>

<span data-ttu-id="4d133-110">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [ `<<` operator](left-shift-operator.md), operator przypisania przesunięcia w lewo `<<=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="4d133-110">If a user-defined type [overloads](../keywords/operator.md) the [`<<` operator](left-shift-operator.md), the left-shift assignment operator `<<=` is implicitly overloaded.</span></span> <span data-ttu-id="4d133-111">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="4d133-111">A user-defined type cannot explicitly overload the left-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4d133-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4d133-112">C# language specification</span></span>

<span data-ttu-id="4d133-113">Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d133-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d133-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d133-114">See also</span></span>

- [<span data-ttu-id="4d133-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4d133-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4d133-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4d133-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4d133-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="4d133-117">C# Operators</span></span>](index.md)
