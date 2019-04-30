---
title: '&amp;= — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660154"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="c7289-102">&amp;= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c7289-102">&amp;= Operator (C# Reference)</span></span>

<span data-ttu-id="c7289-103">Operator przypisania AND.</span><span class="sxs-lookup"><span data-stu-id="c7289-103">The AND assignment operator.</span></span>

<span data-ttu-id="c7289-104">Usługi za pomocą wyrażenia `&=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="c7289-104">An expression using the `&=` operator, such as</span></span>

```csharp
x &= y
```

<span data-ttu-id="c7289-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="c7289-105">is equivalent to</span></span>

```csharp
x = x & y
```

<span data-ttu-id="c7289-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="c7289-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="c7289-107">Dla liczby całkowitej, wykonują się dużo [ `&` operator](and-operator.md) oblicza iloczynu bitowego AND logiczne z argumentów; w przypadku [bool](../keywords/bool.md) operandów, oblicza logicznego i jego operandu.</span><span class="sxs-lookup"><span data-stu-id="c7289-107">For integer operands, the [`&` operator](and-operator.md) computes the bitwise logical AND of its operands; for [bool](../keywords/bool.md) operands, it computes the logical AND of its operands.</span></span>

<span data-ttu-id="c7289-108">W poniższym przykładzie pokazano użycie `&=` operator:</span><span class="sxs-lookup"><span data-stu-id="c7289-108">The following example demonstrates the usage of the `&=` operator:</span></span>

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a><span data-ttu-id="c7289-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="c7289-109">Operator overloadability</span></span>

<span data-ttu-id="c7289-110">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [ `&` operator](and-operator.md), operator przypisania AND `&=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="c7289-110">If a user-defined type [overloads](../keywords/operator.md) the [`&` operator](and-operator.md), the AND assignment operator `&=` is implicitly overloaded.</span></span> <span data-ttu-id="c7289-111">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania AND.</span><span class="sxs-lookup"><span data-stu-id="c7289-111">A user-defined type cannot explicitly overload the AND assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7289-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c7289-112">C# language specification</span></span>

<span data-ttu-id="c7289-113">Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7289-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7289-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7289-114">See also</span></span>

- [<span data-ttu-id="c7289-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c7289-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7289-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c7289-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7289-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c7289-117">C# Operators</span></span>](index.md)
