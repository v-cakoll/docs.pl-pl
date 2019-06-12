---
title: ?? operator - C# odwołania
ms.custom: seodec18
ms.date: 06/07/2019
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: a19b5558da36ffb11dabd1b9bec419a3623a0f17
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024988"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="47304-103">??</span><span class="sxs-lookup"><span data-stu-id="47304-103">??</span></span> <span data-ttu-id="47304-104">Operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="47304-104">operator (C# reference)</span></span>

<span data-ttu-id="47304-105">Operatora łączenia wartości null `??` zwraca wartość swojego operandu po lewej stronie, jeśli nie jest `null`; w przeciwnym razie oblicza prawostronny operand i zwraca jego wynik.</span><span class="sxs-lookup"><span data-stu-id="47304-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="47304-106">`??` Operator nie szacuje swojego operandu po prawej stronie, gdy lewostronny operand jest inna niż null.</span><span class="sxs-lookup"><span data-stu-id="47304-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="47304-107">Operator łączenia wartości null jest łączność do prawej strony, oznacza to, że wyrażenie formularza</span><span class="sxs-lookup"><span data-stu-id="47304-107">The null-coalescing operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ?? b ?? c
```

<span data-ttu-id="47304-108">jest wykonywane jako</span><span class="sxs-lookup"><span data-stu-id="47304-108">is evaluated as</span></span>

```csharp
a ?? (b ?? c)
```

<span data-ttu-id="47304-109">`??` Operator może być przydatne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="47304-109">The `??` operator can be useful in the following scenarios:</span></span>

- <span data-ttu-id="47304-110">W wyrażeniach z [operatorów warunkowych działających z wartością null?. i?] ](member-access-operators.md#null-conditional-operators--and-), można używać operatora łączenia wartości null zapewnienie alternatywnych wyrażenie do oceny, w przypadku, gdy jest wynikiem wyrażenia warunkowe null operacji `null`:</span><span class="sxs-lookup"><span data-stu-id="47304-110">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="47304-111">Podczas pracy z [typy o wartości zerowalnej](../../programming-guide/nullable-types/index.md) i musisz podać wartość bazowego typu wartości, określ wartość, aby zapewnić w przypadku, gdy wartość typu dopuszczającego wartość null jest za pomocą operatora łączenia wartości null `null`:</span><span class="sxs-lookup"><span data-stu-id="47304-111">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="47304-112">Użyj <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metoda Jeśli wartość ma być używana, gdy wartość typu dopuszczającego wartość null jest `null` powinien mieć wartość domyślną typu wartości podstawowej.</span><span class="sxs-lookup"><span data-stu-id="47304-112">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="47304-113">Począwszy od C# 7.0, można użyć [ `throw` wyrażenie](../keywords/throw.md#the-throw-expression) jako prawostronny operand operatora łączenia wartości null się bardziej zwięzły widok kodu sprawdzanie argumentu:</span><span class="sxs-lookup"><span data-stu-id="47304-113">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="47304-114">Poprzedni przykład ilustruje też sposób używania [elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) do zdefiniowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="47304-114">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="47304-115">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="47304-115">Operator overloadability</span></span>

<span data-ttu-id="47304-116">Nie można przeciążać operatora łączenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="47304-116">The null-coalescing operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="47304-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="47304-117">C# language specification</span></span>

<span data-ttu-id="47304-118">Aby uzyskać więcej informacji, zobacz [null operatora łączącego](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="47304-118">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47304-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47304-119">See also</span></span>

- [<span data-ttu-id="47304-120">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="47304-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="47304-121">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="47304-121">C# operators</span></span>](index.md)
- <span data-ttu-id="47304-122">[?. i? Operatory]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="47304-122">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="47304-123">?: — operator</span><span class="sxs-lookup"><span data-stu-id="47304-123">?: operator</span></span>](conditional-operator.md)
