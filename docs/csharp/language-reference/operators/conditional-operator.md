---
title: '?: — odwołanie C# do operatora'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 923591634599a6bbac74d43b105f4e46b492fa1a
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796465"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b5362-102">?: — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="b5362-102">?: operator (C# reference)</span></span>

<span data-ttu-id="b5362-103">Operator `?:`warunkowy, często znany jako operator warunkowy Trzyelementowy, ocenia wyrażenie logiczne i zwraca wynik oceny jednego z dwóch wyrażeń, w zależności od tego, czy wyrażenie logiczne daje `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="b5362-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="b5362-104">Począwszy od C# 7,2, [wyrażenie warunkowe](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b5362-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="b5362-105">Składnia operatora warunkowego jest następująca:</span><span class="sxs-lookup"><span data-stu-id="b5362-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="b5362-106">Wyrażenie musi być szacowane do `true` lub `false`. `condition`</span><span class="sxs-lookup"><span data-stu-id="b5362-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="b5362-107">Jeśli `condition` jest wynikiem obliczenia `true`, `consequent` wyrażenie jest oceniane, a jego wynik zmieni się na wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="b5362-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="b5362-108">Jeśli `condition` jest wynikiem obliczenia `false`, `alternative` wyrażenie jest oceniane, a jego wynik zmieni się na wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="b5362-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="b5362-109">Tylko `consequent` lub`alternative` jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="b5362-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="b5362-110">Typ `consequent` i`alternative` musi być taki sam lub musi być niejawną konwersją z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="b5362-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="b5362-111">Operator warunkowy jest prawym przyciskiem asocjacyjnym, czyli wyrażeniem formularza</span><span class="sxs-lookup"><span data-stu-id="b5362-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="b5362-112">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="b5362-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="b5362-113">Poniższego urządzenia można użyć do zapamiętania, jak jest oceniany operator warunkowy:</span><span class="sxs-lookup"><span data-stu-id="b5362-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="b5362-114">Poniższy przykład ilustruje użycie operatora warunkowego:</span><span class="sxs-lookup"><span data-stu-id="b5362-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="b5362-115">Wyrażenie warunkowe ref</span><span class="sxs-lookup"><span data-stu-id="b5362-115">Conditional ref expression</span></span>

<span data-ttu-id="b5362-116">Począwszy od C# 7,2, można użyć wyrażenia ref warunkowego do zwrócenia odwołania do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b5362-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="b5362-117">Można przypisać to odwołanie do zmiennej lokalnej [ref](../keywords/ref.md#ref-locals) lub [ref tylko do odczytu](../keywords/ref.md#ref-readonly-locals) , lub użyć jej jako [](../keywords/ref.md#reference-return-values) [ `ref` ](../keywords/ref.md#passing-an-argument-by-reference)wartości zwracanej przez odwołanie lub jako parametru metody.</span><span class="sxs-lookup"><span data-stu-id="b5362-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="b5362-118">Składnia wyrażenia ref warunkowego jest następująca:</span><span class="sxs-lookup"><span data-stu-id="b5362-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="b5362-119">Podobnie jak w przypadku oryginalnego operatora warunkowego wyrażenie ref oblicza tylko jedno z dwóch wyrażeń: `consequent` albo lub. `alternative`</span><span class="sxs-lookup"><span data-stu-id="b5362-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="b5362-120">W przypadku warunkowego wyrażenia ref typ `consequent` i `alternative` musi być taki sam.</span><span class="sxs-lookup"><span data-stu-id="b5362-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="b5362-121">Poniższy przykład demonstruje użycie warunkowego wyrażenia ref:</span><span class="sxs-lookup"><span data-stu-id="b5362-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

<span data-ttu-id="b5362-122">Aby uzyskać więcej informacji, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="b5362-122">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="b5362-123">Operator warunkowy i `if..else` instrukcja</span><span class="sxs-lookup"><span data-stu-id="b5362-123">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="b5362-124">Użycie operatora warunkowego nad instrukcją [if-else](../keywords/if-else.md) może spowodować zwiększenie zwięzłego kodu w przypadkach, gdy konieczne jest warunkowe obliczenie wartości.</span><span class="sxs-lookup"><span data-stu-id="b5362-124">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="b5362-125">Poniższy przykład ilustruje dwa sposoby klasyfikowania liczby całkowitej jako ujemnej lub nieujemnej:</span><span class="sxs-lookup"><span data-stu-id="b5362-125">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="b5362-126">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="b5362-126">Operator overloadability</span></span>

<span data-ttu-id="b5362-127">Operatorów warunkowych nie można przeciążać.</span><span class="sxs-lookup"><span data-stu-id="b5362-127">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b5362-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b5362-128">C# language specification</span></span>

<span data-ttu-id="b5362-129">Aby uzyskać więcej informacji, zobacz sekcję [warunkowego operatora](~/_csharplang/spec/expressions.md#conditional-operator) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b5362-129">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5362-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5362-130">See also</span></span>

- [<span data-ttu-id="b5362-131">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="b5362-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b5362-132">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b5362-132">C# operators</span></span>](index.md)
- [<span data-ttu-id="b5362-133">if-else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b5362-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="b5362-134">[?. i?\[\] Operatory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="b5362-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="b5362-135">?? zakład</span><span class="sxs-lookup"><span data-stu-id="b5362-135">?? operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="b5362-136">ref keyword</span><span class="sxs-lookup"><span data-stu-id="b5362-136">ref keyword</span></span>](../keywords/ref.md)
