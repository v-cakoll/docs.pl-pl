---
title: '>>= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220916"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6353c-102">>> = — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="6353c-102">>>= operator (C# Reference)</span></span>

<span data-ttu-id="6353c-103">Operator przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="6353c-103">The right-shift assignment operator.</span></span>

<span data-ttu-id="6353c-104">Usługi za pomocą wyrażenia `>>=` operatora, takich jak</span><span class="sxs-lookup"><span data-stu-id="6353c-104">An expression using the `>>=` operator, such as</span></span>

```csharp
x >>= y
```

<span data-ttu-id="6353c-105">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="6353c-105">is equivalent to</span></span>

```csharp
x = x >> y
```

<span data-ttu-id="6353c-106">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="6353c-106">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="6353c-107">[ `>>` Operator](right-shift-operator.md) bezpośrednio przenosi swojego pierwszego operandu przez liczbę bitów definicją drugim argumentem.</span><span class="sxs-lookup"><span data-stu-id="6353c-107">The [`>>` operator](right-shift-operator.md) shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="6353c-108">W poniższym przykładzie pokazano użycie `>>=` operator:</span><span class="sxs-lookup"><span data-stu-id="6353c-108">The following example demonstrates the usage of the `>>=` operator:</span></span>

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a><span data-ttu-id="6353c-109">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="6353c-109">Operator overloadability</span></span>

<span data-ttu-id="6353c-110">Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [ `>>` operator](right-shift-operator.md), operator przypisania przesunięcia w prawo `>>=` niejawnie jest przeciążony.</span><span class="sxs-lookup"><span data-stu-id="6353c-110">If a user-defined type [overloads](../keywords/operator.md) the [`>>` operator](right-shift-operator.md), the right-shift assignment operator `>>=` is implicitly overloaded.</span></span> <span data-ttu-id="6353c-111">Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="6353c-111">A user-defined type cannot explicitly overload the right-shift assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6353c-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6353c-112">C# language specification</span></span>

<span data-ttu-id="6353c-113">Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6353c-113">For more information, see the [Compound assignment](~/_csharplang/spec/expressions.md#compound-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6353c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6353c-114">See also</span></span>

- [<span data-ttu-id="6353c-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6353c-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6353c-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6353c-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6353c-117">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="6353c-117">C# operators</span></span>](index.md)