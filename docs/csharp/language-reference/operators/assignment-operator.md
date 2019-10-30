---
title: Operatory przypisania — C# odwołanie
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 103bc823ab6a56d53a3f2ec05b8de9295f1de400
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039078"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="2cc18-102">Operatory przypisania (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="2cc18-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="2cc18-103">Operator przypisania `=` przypisuje wartość operandu po prawej stronie do zmiennej, [Właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu [indeksatora](../../programming-guide/indexers/index.md) podaną przez jego operand po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2cc18-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="2cc18-104">Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2cc18-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="2cc18-105">Typ operandu po prawej stronie musi być taki sam jak typ operandu po lewej stronie lub niejawnie konwertowany.</span><span class="sxs-lookup"><span data-stu-id="2cc18-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="2cc18-106">Operator przypisania `=` jest prawym przyciskiem asocjacyjnym, czyli wyrażeniem formularza</span><span class="sxs-lookup"><span data-stu-id="2cc18-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="2cc18-107">jest oceniane jako</span><span class="sxs-lookup"><span data-stu-id="2cc18-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="2cc18-108">Poniższy przykład ilustruje użycie operatora przypisania ze zmienną lokalną, właściwością i elementem indeksatora jako swój argument operacji po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="2cc18-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="2cc18-109">operator przypisania ref</span><span class="sxs-lookup"><span data-stu-id="2cc18-109">ref assignment operator</span></span>

<span data-ttu-id="2cc18-110">Począwszy od C# 7,3, można użyć operatora przypisania ref`= ref`do ponownego [przypisania lokalnej zmiennej lokalnej lub](../keywords/ref.md#ref-locals) [ref tylko do odczytu](../keywords/ref.md#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="2cc18-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="2cc18-111">Poniższy przykład ilustruje użycie operatora przypisania odwołania:</span><span class="sxs-lookup"><span data-stu-id="2cc18-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="2cc18-112">W przypadku operatora przypisania odwołania, oba operandy muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="2cc18-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="2cc18-113">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="2cc18-113">Compound assignment</span></span>

<span data-ttu-id="2cc18-114">Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza</span><span class="sxs-lookup"><span data-stu-id="2cc18-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="2cc18-115">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="2cc18-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="2cc18-116">z tą różnicą, że `x` jest obliczana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="2cc18-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="2cc18-117">Przypisanie złożone jest obsługiwane przez [arytmetyczne](arithmetic-operators.md#compound-assignment)operatory [logiczne logiczne](boolean-logical-operators.md#compound-assignment) [i bitowe](bitwise-and-shift-operators.md#compound-assignment) .</span><span class="sxs-lookup"><span data-stu-id="2cc18-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="2cc18-118">Przypisanie do łączenia o wartości null</span><span class="sxs-lookup"><span data-stu-id="2cc18-118">Null-coalescing assignment</span></span>

<span data-ttu-id="2cc18-119">Począwszy od C# 8,0, można użyć operatora przypisania łączącego wartości null`??=`, aby przypisać wartość jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie jest obliczany do`null`.</span><span class="sxs-lookup"><span data-stu-id="2cc18-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="2cc18-120">Aby uzyskać więcej informacji, zobacz [? =](null-coalescing-operator.md) — artykuł.</span><span class="sxs-lookup"><span data-stu-id="2cc18-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2cc18-121">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="2cc18-121">Operator overloadability</span></span>

<span data-ttu-id="2cc18-122">Typ zdefiniowany przez użytkownika nie może [przeciążać](operator-overloading.md) operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="2cc18-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="2cc18-123">Jednak typ zdefiniowany przez użytkownika może definiować niejawną konwersję na inny typ.</span><span class="sxs-lookup"><span data-stu-id="2cc18-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="2cc18-124">W ten sposób wartość typu zdefiniowanego przez użytkownika może być przypisana do zmiennej, właściwości lub elementu indeksatora innego typu.</span><span class="sxs-lookup"><span data-stu-id="2cc18-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="2cc18-125">Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="2cc18-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="2cc18-126">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="2cc18-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="2cc18-127">Jeśli jednak typ zdefiniowany przez użytkownika przeciąża operator binarny `op`, operator `op=`, jeśli istnieje, jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="2cc18-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2cc18-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2cc18-128">C# language specification</span></span>

<span data-ttu-id="2cc18-129">Aby uzyskać więcej informacji, zobacz sekcję [Operatory przypisania](~/_csharplang/spec/expressions.md#assignment-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2cc18-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="2cc18-130">Aby uzyskać więcej informacji na temat `= ref`operatora przypisania odwołania, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="2cc18-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2cc18-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cc18-131">See also</span></span>

- [<span data-ttu-id="2cc18-132">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="2cc18-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2cc18-133">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2cc18-133">C# operators</span></span>](index.md)
- [<span data-ttu-id="2cc18-134">ref — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="2cc18-134">ref keyword</span></span>](../keywords/ref.md)
