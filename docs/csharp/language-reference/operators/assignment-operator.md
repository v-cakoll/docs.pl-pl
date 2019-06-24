---
title: = — operator - C# odwołania
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306566"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="eec96-102">= — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="eec96-102">= operator (C# reference)</span></span>

<span data-ttu-id="eec96-103">Operator przypisania `=` wartość jego prawostronny operand jest przypisywany do zmiennej, [właściwość](../../programming-guide/classes-and-structs/properties.md), lub [indeksatora](../../../csharp/programming-guide/indexers/index.md) elementu przez jej argument po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="eec96-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="eec96-104">Wynikiem wyrażenia przypisania jest wartość przypisana do lewostronny operand.</span><span class="sxs-lookup"><span data-stu-id="eec96-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="eec96-105">Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie, albo niejawnie przekonwertować do niego.</span><span class="sxs-lookup"><span data-stu-id="eec96-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="eec96-106">Operator przypisania ma łączność do prawej strony, oznacza to, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="eec96-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="eec96-107">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="eec96-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="eec96-108">Poniższy przykład ilustruje użycie operatora przypisania, za pomocą zmiennej lokalnej, właściwości i elementu indeksatora jako jej argument po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="eec96-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="eec96-109">operator przypisania REF</span><span class="sxs-lookup"><span data-stu-id="eec96-109">ref assignment operator</span></span>

<span data-ttu-id="eec96-110">Począwszy od C# 7.3, można użyć operatora przypisania `= ref` do ponownego przypisania [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej.</span><span class="sxs-lookup"><span data-stu-id="eec96-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="eec96-111">Poniższy przykład ilustruje użycie operatora przypisania:</span><span class="sxs-lookup"><span data-stu-id="eec96-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="eec96-112">W przypadku operatora przypisania typ obu argumentów musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="eec96-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="eec96-113">Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="eec96-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="eec96-114">Przydział złożony</span><span class="sxs-lookup"><span data-stu-id="eec96-114">Compound assignment</span></span>

<span data-ttu-id="eec96-115">Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="eec96-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="eec96-116">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="eec96-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="eec96-117">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="eec96-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="eec96-118">Przypisania złożonego jest obsługiwana przez [arytmetyczne](arithmetic-operators.md#compound-assignment), [Boolean logiczna](boolean-logical-operators.md#compound-assignment), i [bitowe logicznej- and -shift](bitwise-and-shift-operators.md#compound-assignment) operatorów.</span><span class="sxs-lookup"><span data-stu-id="eec96-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="eec96-119">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="eec96-119">Operator overloadability</span></span>

<span data-ttu-id="eec96-120">Typ zdefiniowany przez użytkownika nie mogą przeciążać operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="eec96-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="eec96-121">Typ zdefiniowany przez użytkownika można jednak zdefiniować niejawną konwersję do innego typu.</span><span class="sxs-lookup"><span data-stu-id="eec96-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="eec96-122">Dzięki temu wartość typu zdefiniowanego przez użytkownika można przypisać do zmiennej, właściwość lub indeksator elementu innego typu.</span><span class="sxs-lookup"><span data-stu-id="eec96-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="eec96-123">Aby uzyskać więcej informacji, zobacz [niejawne](../keywords/implicit.md) artykułu — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="eec96-123">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eec96-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eec96-124">C# language specification</span></span>

<span data-ttu-id="eec96-125">Aby uzyskać więcej informacji, zobacz [operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="eec96-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eec96-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eec96-126">See also</span></span>

- [<span data-ttu-id="eec96-127">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="eec96-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="eec96-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="eec96-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="eec96-129">ref keyword</span><span class="sxs-lookup"><span data-stu-id="eec96-129">ref keyword</span></span>](../keywords/ref.md)
