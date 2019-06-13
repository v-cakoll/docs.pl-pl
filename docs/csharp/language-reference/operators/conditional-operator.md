---
title: '?: operator - C# odwołania'
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
ms.openlocfilehash: 2717505a0a09b9ac1c6ad43153c52771c13f7b5c
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025196"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1a4f3-102">?: — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="1a4f3-102">?: operator (C# reference)</span></span>

<span data-ttu-id="1a4f3-103">Operator warunkowy `?:`, powszechnie znane jako operator warunkowy trójargumentowy ocenia wyrażenie logiczne i zwraca wynik obliczania wartości jednego z dwóch wyrażeń w zależności od tego, czy wyrażenie logiczne daje w wyniku `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="1a4f3-104">Począwszy od C# 7.2, [wyrażenie warunkowe ref](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="1a4f3-105">Składnia służąca do operatora warunkowego jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1a4f3-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="1a4f3-106">`condition` Wyrażenia musi być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="1a4f3-107">Jeśli `condition` daje w wyniku `true`, `consequent` wyrażenie jest obliczane, a jego wynik staje się wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="1a4f3-108">Jeśli `condition` daje w wyniku `false`, `alternative` wyrażenie jest obliczane, a jego wynik staje się wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="1a4f3-109">Tylko `consequent` lub `alternative` jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="1a4f3-110">Typ `consequent` i `alternative` musi być w tej samej lub występują musi być niejawna konwersja z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="1a4f3-111">Operator warunkowy jest łączność do prawej strony, oznacza to, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="1a4f3-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="1a4f3-112">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="1a4f3-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="1a4f3-113">Następujące urządzenia mnemoników służy do zapamiętania, jak operator warunkowy jest oceniane:</span><span class="sxs-lookup"><span data-stu-id="1a4f3-113">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="1a4f3-114">Poniższy przykład ilustruje użycie operatora warunkowego:</span><span class="sxs-lookup"><span data-stu-id="1a4f3-114">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="1a4f3-115">Wyrażenie warunkowe ref</span><span class="sxs-lookup"><span data-stu-id="1a4f3-115">Conditional ref expression</span></span>

<span data-ttu-id="1a4f3-116">Począwszy od C# 7.2, umożliwia wyrażenie warunkowe ref zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-116">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="1a4f3-117">Można przypisać tego odwołania do [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej, lub użyj go jako [odwoływać się do wartości zwracanej](../keywords/ref.md#reference-return-values) lub jako [ `ref` — metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="1a4f3-117">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="1a4f3-118">Wyrażenie warunkowe ref składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1a4f3-118">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="1a4f3-119">Takich jak oryginalne operator warunkowy ref warunkowego wynikiem wyrażenia jest tylko jeden z dwóch wyrażeń: albo `consequent` lub `alternative`.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-119">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="1a4f3-120">W przypadku wyrażenie warunkowe ref, typ `consequent` i `alternative` musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-120">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="1a4f3-121">W poniższym przykładzie pokazano użycie wyrażenie warunkowe ref:</span><span class="sxs-lookup"><span data-stu-id="1a4f3-121">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

<span data-ttu-id="1a4f3-122">Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="1a4f3-122">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="1a4f3-123">Operator warunkowy i `if..else` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a4f3-123">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="1a4f3-124">Użycie operatora warunkowego nad [if-else](../keywords/if-else.md) instrukcji może prowadzić do bardziej zwięzły widok kodu w przypadku, gdy trzeba warunkowo obliczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-124">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="1a4f3-125">W poniższym przykładzie pokazano zaklasyfikowania liczby całkowitej jako ujemny lub nieujemne na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="1a4f3-125">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="1a4f3-126">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="1a4f3-126">Operator overloadability</span></span>

<span data-ttu-id="1a4f3-127">Operatorów warunkowych nie można przeciążać.</span><span class="sxs-lookup"><span data-stu-id="1a4f3-127">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1a4f3-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1a4f3-128">C# language specification</span></span>

<span data-ttu-id="1a4f3-129">Aby uzyskać więcej informacji, zobacz [operator warunkowy](~/_csharplang/spec/expressions.md#conditional-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1a4f3-129">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a4f3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a4f3-130">See also</span></span>

- [<span data-ttu-id="1a4f3-131">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="1a4f3-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1a4f3-132">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1a4f3-132">C# operators</span></span>](index.md)
- [<span data-ttu-id="1a4f3-133">if-else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a4f3-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="1a4f3-134">[?. i?\[\] Operatory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="1a4f3-134">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="1a4f3-135">?? operator</span><span class="sxs-lookup"><span data-stu-id="1a4f3-135">?? operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="1a4f3-136">ref keyword</span><span class="sxs-lookup"><span data-stu-id="1a4f3-136">ref keyword</span></span>](../keywords/ref.md)
