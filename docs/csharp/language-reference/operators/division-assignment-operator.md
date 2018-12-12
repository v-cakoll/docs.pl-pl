---
title: / = — Operator - C# odwołania
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286523"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="74c2b-102">Operator /= (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="74c2b-102">/= Operator (C# Reference)</span></span>

<span data-ttu-id="74c2b-103">Operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="74c2b-103">The division assignment operator.</span></span>

<span data-ttu-id="74c2b-104">Usługi za pomocą wyrażenia `/=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="74c2b-104">An expression using the `/=` operator, such as</span></span>

```csharp
x /= y
```

<span data-ttu-id="74c2b-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="74c2b-105">is equivalent to</span></span>

```csharp
x = x / y
```

<span data-ttu-id="74c2b-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="74c2b-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="74c2b-107">[Operator dzielenia](division-operator.md) `/` dzieli pierwszy argument operacji za drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="74c2b-107">The [division operator](division-operator.md) `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="74c2b-108">Jest ona obsługiwana przez wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="74c2b-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="74c2b-109">W poniższym przykładzie pokazano użycie `/=` operator:</span><span class="sxs-lookup"><span data-stu-id="74c2b-109">The following example demonstrates the usage of the `/=` operator:</span></span>

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="74c2b-110">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="74c2b-110">Operator overloadability</span></span>

<span data-ttu-id="74c2b-111">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator dzielenia](division-operator.md) `/`, operator przypisania dzielenia `/=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="74c2b-111">If a user-defined type [overloads](../keywords/operator.md) the [division operator](division-operator.md) `/`, the division assignment operator `/=` is implicitly overloaded.</span></span> <span data-ttu-id="74c2b-112">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania dzielenia.</span><span class="sxs-lookup"><span data-stu-id="74c2b-112">A user-defined type cannot explicitly overload the division assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="74c2b-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="74c2b-113">C# language specification</span></span>

<span data-ttu-id="74c2b-114">Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="74c2b-114">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74c2b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74c2b-115">See also</span></span>

- [<span data-ttu-id="74c2b-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="74c2b-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="74c2b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="74c2b-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="74c2b-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="74c2b-118">C# Operators</span></span>](index.md)
