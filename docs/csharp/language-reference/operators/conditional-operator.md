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
ms.openlocfilehash: 210b7cabb658c6f068d9ab34c83050ad6267e426
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704911"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8b4c6-102">?: Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8b4c6-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="8b4c6-103">Operator warunkowy `?:`, powszechnie znane jako operator warunkowy trójargumentowy ocenia wyrażenie logiczne i zwraca wynik obliczania wartości jednego z dwóch wyrażeń w zależności od tego, czy wyrażenie logiczne daje w wyniku `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-103">The conditional operator `?:`, commonly known as the ternary conditional operator, evaluates a Boolean expression, and returns the result of evaluating one of two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span> <span data-ttu-id="8b4c6-104">Począwszy od C# 7.2, [wyrażenie warunkowe ref](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-104">Beginning with C# 7.2, the [conditional ref expression](#conditional-ref-expression) returns the reference to the result of one of the two expressions.</span></span>

<span data-ttu-id="8b4c6-105">Składnia służąca do operatora warunkowego jest następująca:</span><span class="sxs-lookup"><span data-stu-id="8b4c6-105">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequence : alternative
```

<span data-ttu-id="8b4c6-106">`condition` Wyrażenia musi być `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="8b4c6-107">Jeśli `condition` daje w wyniku `true`, `consequence` wyrażenie jest obliczane, a jego wynik staje się wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-107">If `condition` evaluates to `true`, the `consequence` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="8b4c6-108">Jeśli `condition` daje w wyniku `false`, `alternative` wyrażenie jest obliczane, a jego wynik staje się wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="8b4c6-109">Tylko `consequence` lub `alternative` jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-109">Only `consequence` or `alternative` is evaluated.</span></span>

<span data-ttu-id="8b4c6-110">Typ `consequence` i `alternative` musi być w tej samej lub występują musi być niejawna konwersja z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-110">The type of `consequence` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="8b4c6-111">Operator warunkowy jest łączność do prawej strony, oznacza to, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="8b4c6-111">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="8b4c6-112">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="8b4c6-112">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

<span data-ttu-id="8b4c6-113">Poniższy przykład ilustruje użycie operatora warunkowego:</span><span class="sxs-lookup"><span data-stu-id="8b4c6-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="8b4c6-114">Wyrażenie warunkowe ref</span><span class="sxs-lookup"><span data-stu-id="8b4c6-114">Conditional ref expression</span></span>

<span data-ttu-id="8b4c6-115">Począwszy od C# 7.2, umożliwia wyrażenie warunkowe ref zwraca odwołanie do wyniku jednego z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-115">Beginning with C# 7.2, you can use the conditional ref expression to return the reference to the result of one of the two expressions.</span></span> <span data-ttu-id="8b4c6-116">Można przypisać tego odwołania do [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej, lub użyj go jako [odwoływać się do wartości zwracanej](../keywords/ref.md#reference-return-values) lub jako [ `ref` — metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="8b4c6-116">You can assign that reference to a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable, or use it as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method parameter](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="8b4c6-117">Wyrażenie warunkowe ref składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="8b4c6-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequence : ref alternative
```

<span data-ttu-id="8b4c6-118">Takich jak oryginalne operator warunkowy ref warunkowego wynikiem wyrażenia jest tylko jeden z dwóch wyrażeń: albo `consequence` lub `alternative`.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequence` or `alternative`.</span></span>

<span data-ttu-id="8b4c6-119">W przypadku wyrażenie warunkowe ref, typ `consequence` i `alternative` musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-119">In the case of the conditional ref expression, the type of `consequence` and `alternative` must be the same.</span></span>

<span data-ttu-id="8b4c6-120">W poniższym przykładzie pokazano użycie wyrażenie warunkowe ref:</span><span class="sxs-lookup"><span data-stu-id="8b4c6-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

<span data-ttu-id="8b4c6-121">Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="8b4c6-121">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="8b4c6-122">Operator warunkowy i `if..else` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8b4c6-122">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="8b4c6-123">Użycie operatora warunkowego nad [if-else](../keywords/if-else.md) instrukcji może prowadzić do bardziej zwięzły widok kodu w przypadku, gdy trzeba warunkowo obliczenia wartości.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-123">Use of the conditional operator over an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="8b4c6-124">W poniższym przykładzie pokazano zaklasyfikowania liczby całkowitej jako ujemny lub nieujemne na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="8b4c6-124">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="8b4c6-125">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="8b4c6-125">Operator overloadability</span></span>

<span data-ttu-id="8b4c6-126">Operatorów warunkowych nie można przeciążać.</span><span class="sxs-lookup"><span data-stu-id="8b4c6-126">The conditional operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b4c6-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8b4c6-127">C# language specification</span></span>

<span data-ttu-id="8b4c6-128">Aby uzyskać więcej informacji, zobacz [operator warunkowy](~/_csharplang/spec/expressions.md#conditional-operator) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8b4c6-128">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b4c6-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b4c6-129">See also</span></span>

- [<span data-ttu-id="8b4c6-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8b4c6-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8b4c6-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8b4c6-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8b4c6-132">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="8b4c6-132">C# Operators</span></span>](index.md)
- [<span data-ttu-id="8b4c6-133">if-else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8b4c6-133">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="8b4c6-134">[Operatory ?. i ?[]](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="8b4c6-134">[?. and ?[] Operators](null-conditional-operators.md)</span></span>
- [<span data-ttu-id="8b4c6-135">??, operator</span><span class="sxs-lookup"><span data-stu-id="8b4c6-135">?? Operator</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="8b4c6-136">ref keyword</span><span class="sxs-lookup"><span data-stu-id="8b4c6-136">ref keyword</span></span>](../keywords/ref.md)
