---
title: '* = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689609"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79f7b-102">\*= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="79f7b-102">\*= Operator (C# Reference)</span></span>

<span data-ttu-id="79f7b-103">Operator przypisania mnożenia.</span><span class="sxs-lookup"><span data-stu-id="79f7b-103">The multiplication assignment operator.</span></span>

<span data-ttu-id="79f7b-104">Usługi za pomocą wyrażenia `*=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="79f7b-104">An expression using the `*=` operator, such as</span></span>

```csharp
x *= y
```

<span data-ttu-id="79f7b-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="79f7b-105">is equivalent to</span></span>

```csharp
x = x * y
```

<span data-ttu-id="79f7b-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="79f7b-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="79f7b-107">Dla typów liczbowych [ \* operator](multiplication-operator.md) Oblicza iloczyn argumentów.</span><span class="sxs-lookup"><span data-stu-id="79f7b-107">For numeric types, the [\* operator](multiplication-operator.md) computes the product of its operands.</span></span>

<span data-ttu-id="79f7b-108">W poniższym przykładzie pokazano użycie `*=` operator:</span><span class="sxs-lookup"><span data-stu-id="79f7b-108">The following example demonstrates the usage of the `*=` operator:</span></span>

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a><span data-ttu-id="79f7b-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="79f7b-109">Operator overloadability</span></span>

<span data-ttu-id="79f7b-110">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator mnożenia](multiplication-operator.md) `*`, operator przypisania mnożenia `*=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="79f7b-110">If a user-defined type [overloads](../keywords/operator.md) the [multiplication operator](multiplication-operator.md) `*`, the multiplication assignment operator `*=` is implicitly overloaded.</span></span> <span data-ttu-id="79f7b-111">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania mnożenia.</span><span class="sxs-lookup"><span data-stu-id="79f7b-111">A user-defined type cannot explicitly overload the multiplication assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="79f7b-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="79f7b-112">C# language specification</span></span>

<span data-ttu-id="79f7b-113">Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="79f7b-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79f7b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79f7b-114">See also</span></span>

- [<span data-ttu-id="79f7b-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="79f7b-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79f7b-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="79f7b-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79f7b-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="79f7b-117">C# Operators</span></span>](index.md)
