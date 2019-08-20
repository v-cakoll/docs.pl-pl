---
title: = odwołanie do C# operatora
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: f30b48fc6bd1e896658a7234a58409ea9a0f5e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601945"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3d64c-102">= — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="3d64c-102">= operator (C# reference)</span></span>

<span data-ttu-id="3d64c-103">Operator `=` przypisania przypisuje wartość jego operandu po prawej stronie do zmiennej, [Właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu indeksatora podanym [](../../programming-guide/indexers/index.md) przez operand z lewej strony.</span><span class="sxs-lookup"><span data-stu-id="3d64c-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="3d64c-104">Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3d64c-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="3d64c-105">Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie lub niejawnie konwertowany.</span><span class="sxs-lookup"><span data-stu-id="3d64c-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="3d64c-106">Operator przypisania jest prawym przyciskiem asocjacyjnym, czyli wyrażeniem formularza</span><span class="sxs-lookup"><span data-stu-id="3d64c-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="3d64c-107">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="3d64c-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="3d64c-108">Poniższy przykład ilustruje użycie operatora przypisania ze zmienną lokalną, właściwością i elementem indeksatora jako swój argument operacji po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="3d64c-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="3d64c-109">operator przypisania ref</span><span class="sxs-lookup"><span data-stu-id="3d64c-109">ref assignment operator</span></span>

<span data-ttu-id="3d64c-110">Począwszy od C# 7,3, można użyć operatora `= ref` przypisania odwołania, aby ponownie przypisać [lokalną](../keywords/ref.md#ref-locals) zmienną lokalną lub [ref tylko do odczytu](../keywords/ref.md#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="3d64c-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="3d64c-111">Poniższy przykład ilustruje użycie operatora przypisania odwołania:</span><span class="sxs-lookup"><span data-stu-id="3d64c-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="3d64c-112">W przypadku operatora przypisania ref typ obu argumentów operacji musi być taki sam.</span><span class="sxs-lookup"><span data-stu-id="3d64c-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="3d64c-113">Aby uzyskać więcej informacji, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="3d64c-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="3d64c-114">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="3d64c-114">Compound assignment</span></span>

<span data-ttu-id="3d64c-115">Dla operatora `op`binarnego wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="3d64c-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="3d64c-116">odpowiada wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="3d64c-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="3d64c-117">z tą różnicą, że `x` jest obliczany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3d64c-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="3d64c-118">Przypisanie złożone jest obsługiwane przez [arytmetyczne](arithmetic-operators.md#compound-assignment)operatory logiczne logiczne [i bitowe](bitwise-and-shift-operators.md#compound-assignment) . [](boolean-logical-operators.md#compound-assignment)</span><span class="sxs-lookup"><span data-stu-id="3d64c-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3d64c-119">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="3d64c-119">Operator overloadability</span></span>

<span data-ttu-id="3d64c-120">Typ zdefiniowany przez użytkownika nie może przeciążać operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="3d64c-120">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="3d64c-121">Jednak typ zdefiniowany przez użytkownika może definiować niejawną konwersję na inny typ.</span><span class="sxs-lookup"><span data-stu-id="3d64c-121">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="3d64c-122">W ten sposób wartość typu zdefiniowanego przez użytkownika może być przypisana do zmiennej, właściwości lub elementu indeksatora innego typu.</span><span class="sxs-lookup"><span data-stu-id="3d64c-122">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="3d64c-123">Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3d64c-123">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d64c-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3d64c-124">C# language specification</span></span>

<span data-ttu-id="3d64c-125">Aby uzyskać więcej informacji, zobacz sekcję [Operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d64c-125">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d64c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d64c-126">See also</span></span>

- [<span data-ttu-id="3d64c-127">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="3d64c-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3d64c-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3d64c-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="3d64c-129">ref keyword</span><span class="sxs-lookup"><span data-stu-id="3d64c-129">ref keyword</span></span>](../keywords/ref.md)
