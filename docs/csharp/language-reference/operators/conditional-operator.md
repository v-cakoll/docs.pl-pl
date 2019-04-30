---
title: '?: Operator - C# odwołania'
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
ms.openlocfilehash: 53a867e46b02793df5ad5bd9ca5ef676d0653a2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660063"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="30f55-102">?: Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="30f55-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="30f55-103">Operator warunkowy `?:`, powszechnie znane jako operator warunkowy trójargumentowy ocenia wyrażenie logiczne i zwraca wynik obliczania wartości jednego z dwóch wyrażeń w zależności od tego, czy wyrażenie logiczne daje w wyniku `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="30f55-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="30f55-104">Począwszy od C# 7.2, [wyrażenie warunkowe ref](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="30f55-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="30f55-105">Składnia służąca do operatora warunkowego jest następująca:</span><span class="sxs-lookup"><span data-stu-id="30f55-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="30f55-106">`condition` Wyrażenia musi być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="30f55-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="30f55-107">Jeśli `condition` daje w wyniku `true`, `consequent` wyrażenie jest obliczane, a jego wynik staje się wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="30f55-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="30f55-108">Jeśli `condition` daje w wyniku `false`, `alternative` wyrażenie jest obliczane, a jego wynik staje się wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="30f55-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="30f55-109">Tylko `consequent` lub `alternative` jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="30f55-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="30f55-110">Typ `consequent` i `alternative` musi być w tej samej lub występują musi być niejawna konwersja z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="30f55-110">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="30f55-111">Operator warunkowy jest łączność do prawej strony, oznacza to, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="30f55-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="30f55-112">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="30f55-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

<span data-ttu-id="30f55-113">Przydatną urządzenia mnemoników, służących do zapamiętania, jak ocenia Ten operator jest zadając:</span><span class="sxs-lookup"><span data-stu-id="30f55-113">A handy mnemonic device you can use to remember how this operator evaluates is by asking:</span></span>

```
is this condition true ? yes : no
```

<span data-ttu-id="30f55-114">za pomocą?</span><span class="sxs-lookup"><span data-stu-id="30f55-114">with the ?</span></span> <span data-ttu-id="30f55-115">część operator działający jako znak zapytania do poprzedniej instrukcji i następstwie działający jako logicznych odpowiedzi na to pytanie.</span><span class="sxs-lookup"><span data-stu-id="30f55-115">part of the operator acting as a question mark for the previous statement, and the consequent acting as the logical response to this question.</span></span>

<span data-ttu-id="30f55-116">Poniższy przykład ilustruje użycie operatora warunkowego:</span><span class="sxs-lookup"><span data-stu-id="30f55-116">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="30f55-117">Wyrażenie warunkowe ref</span><span class="sxs-lookup"><span data-stu-id="30f55-117">Conditional ref expression</span></span>

<span data-ttu-id="30f55-118">Począwszy od C# 7.2, umożliwia wyrażenie warunkowe ref zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="30f55-118">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="30f55-119">Można przypisać tego odwołania do [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej, lub użyj go jako [odwoływać się do wartości zwracanej](../keywords/ref.md#reference-return-values) lub jako [ `ref` — metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="30f55-119">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="30f55-120">Wyrażenie warunkowe ref składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="30f55-120">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="30f55-121">Takich jak oryginalne operator warunkowy ref warunkowego wynikiem wyrażenia jest tylko jeden z dwóch wyrażeń: albo `consequent` lub `alternative`.</span><span class="sxs-lookup"><span data-stu-id="30f55-121">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="30f55-122">W przypadku wyrażenie warunkowe ref, typ `consequent` i `alternative` musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="30f55-122">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="30f55-123">W poniższym przykładzie pokazano użycie wyrażenie warunkowe ref:</span><span class="sxs-lookup"><span data-stu-id="30f55-123">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="30f55-124">Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="30f55-124">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="30f55-125">Operator warunkowy i `if..else` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="30f55-125">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="30f55-126">Użycie operatora warunkowego nad [if-else](../keywords/if-else.md) instrukcji może prowadzić do bardziej zwięzły widok kodu w przypadku, gdy trzeba warunkowo obliczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="30f55-126">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="30f55-127">W poniższym przykładzie pokazano zaklasyfikowania liczby całkowitej jako ujemny lub nieujemne na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="30f55-127">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="30f55-128">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="30f55-128">Operator overloadability</span></span>

<span data-ttu-id="30f55-129">Operatorów warunkowych nie można przeciążać.</span><span class="sxs-lookup"><span data-stu-id="30f55-129">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="30f55-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="30f55-130">C# language specification</span></span>

<span data-ttu-id="30f55-131">Aby uzyskać więcej informacji, zobacz [operator warunkowy](~/_csharplang/spec/expressions.md#conditional-operator) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="30f55-131">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30f55-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30f55-132">See also</span></span>

- [<span data-ttu-id="30f55-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="30f55-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="30f55-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30f55-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="30f55-135">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="30f55-135">C# Operators</span></span>](index.md)
- [<span data-ttu-id="30f55-136">if-else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="30f55-136">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="30f55-137">[Operatory ?. i ?[]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="30f55-137">[?. and ?[] Operators](null-conditional-operators.md)</span></span>
- [<span data-ttu-id="30f55-138">??, operator</span><span class="sxs-lookup"><span data-stu-id="30f55-138">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="30f55-139">ref keyword</span><span class="sxs-lookup"><span data-stu-id="30f55-139">ref keyword</span></span>](../keywords/ref.md)
