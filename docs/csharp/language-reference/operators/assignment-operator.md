---
title: Operatory przypisania — odwołanie do języka C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399253"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="05e70-102">Operatory przydziałów (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="05e70-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="05e70-103">Operator `=` przypisania przypisuje wartość jego prawostronnego operandu do zmiennej, [właściwości](../../programming-guide/classes-and-structs/properties.md)lub elementu [indeksatora](../../programming-guide/indexers/index.md) podanego przez jego argument po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="05e70-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="05e70-104">Wynikiem wyrażenia przypisania jest wartość przypisana do operandu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="05e70-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="05e70-105">Typ argumentu po prawej stronie musi być taki sam jak typ lewego operandu lub niejawnie kabriolet do niego.</span><span class="sxs-lookup"><span data-stu-id="05e70-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="05e70-106">Operator `=` przypisania jest zeswany, to oznacza, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="05e70-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="05e70-107">jest oceniana jako</span><span class="sxs-lookup"><span data-stu-id="05e70-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="05e70-108">W poniższym przykładzie przedstawiono użycie operatora przypisania ze zmienną lokalną, właściwością i elementem indeksatora jako jego argumentpowe po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="05e70-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="05e70-109">operator przypisania ref</span><span class="sxs-lookup"><span data-stu-id="05e70-109">ref assignment operator</span></span>

<span data-ttu-id="05e70-110">Począwszy od C# 7.3, można `= ref` użyć operatora przypisania ref do ponownego przypisania [ref lokalnej](../keywords/ref.md#ref-locals) lub [ref readonly](../keywords/ref.md#ref-readonly-locals) zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="05e70-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="05e70-111">W poniższym przykładzie przedstawiono użycie operatora przypisania ref:</span><span class="sxs-lookup"><span data-stu-id="05e70-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="05e70-112">W przypadku operatora przypisania ref oba jego operandy muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="05e70-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="05e70-113">Przypisanie złożone</span><span class="sxs-lookup"><span data-stu-id="05e70-113">Compound assignment</span></span>

<span data-ttu-id="05e70-114">Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza</span><span class="sxs-lookup"><span data-stu-id="05e70-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="05e70-115">jest równoważny</span><span class="sxs-lookup"><span data-stu-id="05e70-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="05e70-116">chyba `x` że jest oceniana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="05e70-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="05e70-117">Przypisanie złożone jest obsługiwane przez operatory [arytmetyczne,](arithmetic-operators.md#compound-assignment) [logiczne logiczne logiczne](boolean-logical-operators.md#compound-assignment)i [bitowe logiczne i przesuwne.](bitwise-and-shift-operators.md#compound-assignment)</span><span class="sxs-lookup"><span data-stu-id="05e70-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="05e70-118">Przypisanie łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="05e70-118">Null-coalescing assignment</span></span>

<span data-ttu-id="05e70-119">Począwszy od języka C# 8.0, można użyć operatora `??=` przypisania zerowego łączenia przypisać przypisać przypisać wartość jego operand po prawej stronie do jego `null`operand po lewej stronie tylko wtedy, gdy po lewej stronie operand ocenia .</span><span class="sxs-lookup"><span data-stu-id="05e70-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="05e70-120">Aby uzyskać więcej informacji, zobacz [?? i ?? = artykuł operatorów.](null-coalescing-operator.md)</span><span class="sxs-lookup"><span data-stu-id="05e70-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="05e70-121">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="05e70-121">Operator overloadability</span></span>

<span data-ttu-id="05e70-122">Typ zdefiniowany przez użytkownika nie może [przeciążać](operator-overloading.md) operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="05e70-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="05e70-123">Jednak typ zdefiniowany przez użytkownika można zdefiniować niejawną konwersję na inny typ.</span><span class="sxs-lookup"><span data-stu-id="05e70-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="05e70-124">W ten sposób wartość typu zdefiniowanego przez użytkownika można przypisać do zmiennej, właściwości lub elementu indeksatora innego typu.</span><span class="sxs-lookup"><span data-stu-id="05e70-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="05e70-125">Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="05e70-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="05e70-126">Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.</span><span class="sxs-lookup"><span data-stu-id="05e70-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="05e70-127">Jednak jeśli typ zdefiniowany przez użytkownika `op`przeciąża operatora binarnego, `op=` operator, jeśli istnieje, jest również niejawnie przeciążony.</span><span class="sxs-lookup"><span data-stu-id="05e70-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="05e70-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05e70-128">C# language specification</span></span>

<span data-ttu-id="05e70-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="05e70-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="05e70-130">Aby uzyskać więcej informacji `= ref`na temat operatora przypisania ref, zobacz [propozycję funkcji .](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)</span><span class="sxs-lookup"><span data-stu-id="05e70-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05e70-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05e70-131">See also</span></span>

- [<span data-ttu-id="05e70-132">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="05e70-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="05e70-133">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="05e70-133">C# operators</span></span>](index.md)
- [<span data-ttu-id="05e70-134">ref — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="05e70-134">ref keyword</span></span>](../keywords/ref.md)
