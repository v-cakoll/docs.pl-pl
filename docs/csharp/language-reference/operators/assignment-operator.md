---
title: = — operator - C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 6b8f67f32287b18a9e4ac8f0fa822f6ca4919e7f
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025265"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="282f0-102">= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="282f0-102">= operator (C# reference)</span></span>

<span data-ttu-id="282f0-103">Operator przypisania `=` wartość jego prawostronny operand jest przypisywany do zmiennej, [właściwość](../../programming-guide/classes-and-structs/properties.md), lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) elementu przez jej argument po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="282f0-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="282f0-104">Wynikiem wyrażenia przypisania jest wartość przypisana do lewostronny operand.</span><span class="sxs-lookup"><span data-stu-id="282f0-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="282f0-105">Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie, albo niejawnie przekonwertować do niego.</span><span class="sxs-lookup"><span data-stu-id="282f0-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="282f0-106">Operator przypisania ma łączność do prawej strony, oznacza to, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="282f0-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="282f0-107">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="282f0-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="282f0-108">Poniższy przykład ilustruje użycie operatora przypisania do przypisywania wartości do zmiennej lokalnej, właściwości i elementu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="282f0-108">The following example demonstrates the usage of the assignment operator to assign values to a local variable, a property, and an indexer element:</span></span>

[!code-csharp-interactive[assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="282f0-109">operator przypisania REF</span><span class="sxs-lookup"><span data-stu-id="282f0-109">ref assignment operator</span></span>

<span data-ttu-id="282f0-110">Począwszy od C# 7.3, można użyć operatora przypisania `= ref` do ponownego przypisania [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej.</span><span class="sxs-lookup"><span data-stu-id="282f0-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="282f0-111">Poniższy przykład ilustruje użycie operatora przypisania:</span><span class="sxs-lookup"><span data-stu-id="282f0-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

<span data-ttu-id="282f0-112">W przypadku operatora przypisania typ operandu po lewej stronie i prawy operand musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="282f0-112">In the case of the ref assignment operator, the type of the left operand and the right operand must be the same.</span></span>

<span data-ttu-id="282f0-113">Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="282f0-113">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="282f0-114">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="282f0-114">Operator overloadability</span></span>

<span data-ttu-id="282f0-115">Typ zdefiniowany przez użytkownika nie mogą przeciążać operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="282f0-115">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="282f0-116">Typ zdefiniowany przez użytkownika można jednak zdefiniować niejawną konwersję do innego typu.</span><span class="sxs-lookup"><span data-stu-id="282f0-116">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="282f0-117">Dzięki temu wartość typu zdefiniowanego przez użytkownika można przypisać do zmiennej, właściwość lub indeksator elementu innego typu.</span><span class="sxs-lookup"><span data-stu-id="282f0-117">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="282f0-118">Aby uzyskać więcej informacji, zobacz [niejawne](../keywords/implicit.md) artykułu — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="282f0-118">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="282f0-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="282f0-119">C# language specification</span></span>

<span data-ttu-id="282f0-120">Aby uzyskać więcej informacji, zobacz [przypisanie proste](~/_csharplang/spec/expressions.md#simple-assignment) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="282f0-120">For more information, see the [Simple assignment](~/_csharplang/spec/expressions.md#simple-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="282f0-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="282f0-121">See also</span></span>

- [<span data-ttu-id="282f0-122">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="282f0-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="282f0-123">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="282f0-123">C# operators</span></span>](index.md)
- [<span data-ttu-id="282f0-124">ref keyword</span><span class="sxs-lookup"><span data-stu-id="282f0-124">ref keyword</span></span>](../keywords/ref.md)
