---
title: '?: operator — odwołanie do języka C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399519"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e0ee4-102">?: operator (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="e0ee4-102">?: operator (C# reference)</span></span>

<span data-ttu-id="e0ee4-103">Operator `?:`warunkowy `true` `false`, znany również jako operator warunkowy wzięcia wt.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="e0ee4-104">Składnia operatora warunkowego jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e0ee4-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="e0ee4-105">Wyrażenie `condition` musi oceniać do `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="e0ee4-106">Jeśli `condition` zostanie `true`obliczona `consequent` wartość , wyrażenie zostanie obliczone, a jego wynik stanie się wynikiem operacji.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="e0ee4-107">Jeśli `condition` zostanie `false`obliczona `alternative` wartość , wyrażenie zostanie obliczone, a jego wynik stanie się wynikiem operacji.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="e0ee4-108">Tylko `consequent` `alternative` lub jest oceniana.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="e0ee4-109">Typ `consequent` i `alternative` musi być taka sama lub musi istnieć niejawna konwersja z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="e0ee4-110">Operator warunkowy ma charakter asocjatywny, to oznacza, że jest wyrazem formy</span><span class="sxs-lookup"><span data-stu-id="e0ee4-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="e0ee4-111">jest oceniana jako</span><span class="sxs-lookup"><span data-stu-id="e0ee4-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="e0ee4-112">Za pomocą następującego urządzenia mnemonic można zapamiętać sposób oceny operatora warunkowego:</span><span class="sxs-lookup"><span data-stu-id="e0ee4-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="e0ee4-113">W poniższym przykładzie przedstawiono użycie operatora warunkowego:</span><span class="sxs-lookup"><span data-stu-id="e0ee4-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="e0ee4-114">Warunkowe wyrażenie ref</span><span class="sxs-lookup"><span data-stu-id="e0ee4-114">Conditional ref expression</span></span>

<span data-ttu-id="e0ee4-115">Począwszy od C# 7.2 ref [lokalnej](../keywords/ref.md#ref-locals) lub [ref odczytu tylko](../keywords/ref.md#ref-readonly-locals) zmienna lokalna może być przypisana warunkowo z warunkowego wyrażenia ref.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="e0ee4-116">Można również użyć wyrażenia warunkowego ref jako [wartości zwracanej odwołania](../keywords/ref.md#reference-return-values) lub jako [ `ref` argumentu metody](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="e0ee4-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="e0ee4-117">Składnia wyrażenia warunkowego ref jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e0ee4-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="e0ee4-118">Podobnie jak oryginalny operator warunkowy, warunkowe wyrażenie ref oblicza `consequent` tylko `alternative`jedno z dwóch wyrażeń: albo .</span><span class="sxs-lookup"><span data-stu-id="e0ee4-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="e0ee4-119">W przypadku wyrażenia warunkowego ref typ `consequent` `alternative` i musi być taki sam.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="e0ee4-120">W poniższym przykładzie przedstawiono użycie wyrażenia warunkowego ref:</span><span class="sxs-lookup"><span data-stu-id="e0ee4-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="e0ee4-121">Operator warunkowy i oświadczenie `if..else`</span><span class="sxs-lookup"><span data-stu-id="e0ee4-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="e0ee4-122">Użycie operatora warunkowego zamiast [instrukcji if-else](../keywords/if-else.md) może spowodować bardziej zwięzły kod w przypadkach, gdy trzeba warunkowo obliczyć wartość.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="e0ee4-123">W poniższym przykładzie przedstawiono dwa sposoby klasyfikacji liczby całkowitej jako ujemnej lub nienegatywnej:</span><span class="sxs-lookup"><span data-stu-id="e0ee4-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="e0ee4-124">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="e0ee4-124">Operator overloadability</span></span>

<span data-ttu-id="e0ee4-125">Typ zdefiniowany przez użytkownika nie może przeciążać operatora warunkowego.</span><span class="sxs-lookup"><span data-stu-id="e0ee4-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e0ee4-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0ee4-126">C# language specification</span></span>

<span data-ttu-id="e0ee4-127">Aby uzyskać więcej informacji, zobacz [sekcję Operator warunkowy](~/_csharplang/spec/expressions.md#conditional-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="e0ee4-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e0ee4-128">Aby uzyskać więcej informacji na temat wyrażenia warunkowego ref, zobacz [notę propozycji funkcji](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="e0ee4-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0ee4-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0ee4-129">See also</span></span>

- [<span data-ttu-id="e0ee4-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e0ee4-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e0ee4-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="e0ee4-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="e0ee4-132">instrukcja if-else</span><span class="sxs-lookup"><span data-stu-id="e0ee4-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="e0ee4-133">[?. I? [] operatorzy](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="e0ee4-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="e0ee4-134">?? I?? = operatorzy</span><span class="sxs-lookup"><span data-stu-id="e0ee4-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="e0ee4-135">ref — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="e0ee4-135">ref keyword</span></span>](../keywords/ref.md)
