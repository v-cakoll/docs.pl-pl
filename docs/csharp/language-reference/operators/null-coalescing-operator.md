---
title: ?? i? = Operatory- C# odwołanie
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924678"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="ce976-103">??</span><span class="sxs-lookup"><span data-stu-id="ce976-103">??</span></span> <span data-ttu-id="ce976-104">i? = — OperatoryC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ce976-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="ce976-105">Operator `??` łączenia wartości null zwraca wartość operandu po lewej stronie, jeśli nie jest `null`; w przeciwnym razie oblicza argument operacji po prawej stronie i zwraca wynik.</span><span class="sxs-lookup"><span data-stu-id="ce976-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="ce976-106">`??` Operator nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.</span><span class="sxs-lookup"><span data-stu-id="ce976-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="ce976-107">Dostępne w C# 8,0 i nowszych operator `??=` przypisania łączenia wartości null przypisuje wartość jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie jest obliczany do. `null`</span><span class="sxs-lookup"><span data-stu-id="ce976-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="ce976-108">`??=` Operator nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.</span><span class="sxs-lookup"><span data-stu-id="ce976-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="ce976-109">Argument operacji `??=` po lewej stronie operatora musi być zmienną, [właściwością](../../programming-guide/classes-and-structs/properties.md)lub elementem [indeksatora](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="ce976-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span> <span data-ttu-id="ce976-110">Aby uzyskać więcej informacji na temat przypisania łączenia z wartością null, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="ce976-110">For more information about null-coalescing assignment, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

<span data-ttu-id="ce976-111">W C# 7,3 i starszych typach operandu `??` po lewej stronie operatora musi być typem referencyjnym lub [typem wartości null](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce976-111">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a reference type or a [nullable value type](../../programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="ce976-112">Począwszy od C# 8,0, ten wymóg jest zastępowany następującym: typ operandu `??` i operatorów operatora and `??=` nie może być typem wartości niedopuszczających wartości null.</span><span class="sxs-lookup"><span data-stu-id="ce976-112">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="ce976-113">W szczególności można użyć operatorów łączenia wartości null z nieokreślonymi parametrami typu w C# 8,0 i późniejszych:</span><span class="sxs-lookup"><span data-stu-id="ce976-113">In particular, you can use the null-coalescing operators with unconstrained type parameters in C# 8.0 and later:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="ce976-114">Operatory łączenia wartości null są z prawej strony skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="ce976-114">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="ce976-115">To jest wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="ce976-115">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="ce976-116">są oceniane jako</span><span class="sxs-lookup"><span data-stu-id="ce976-116">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="ce976-117">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ce976-117">Examples</span></span>

<span data-ttu-id="ce976-118">Operatory `??` i`??=` mogą być przydatne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="ce976-118">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="ce976-119">W wyrażeniach z [operatorów warunkowych działających z wartością null?. i ?[]](member-access-operators.md#null-conditional-operators--and-), można używać operatora łączenia wartości null zapewnienie alternatywnych wyrażenie do oceny, w przypadku, gdy jest wynikiem wyrażenia warunkowe null operacji `null`:</span><span class="sxs-lookup"><span data-stu-id="ce976-119">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="ce976-120">Podczas pracy z [typami wartości null](../../programming-guide/nullable-types/index.md) i musi podać wartość bazowego typu wartości, użyj operatora łączenia wartości null, aby określić wartość, która ma zostać podana w przypadku, gdy wartość typu Nullable to `null`:</span><span class="sxs-lookup"><span data-stu-id="ce976-120">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the null-coalescing operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="ce976-121">Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , jeśli wartość, która ma zostać użyta, gdy wartość typu `null` dopuszczająca wartości null ma być wartością domyślną dla bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="ce976-121">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="ce976-122">Począwszy od C# 7,0, można użyć [ `throw` wyrażenia](../keywords/throw.md#the-throw-expression) jako argumentu operacji po prawej stronie operatora łączenia wartości null, aby kod sprawdzania argumentów był bardziej zwięzły:</span><span class="sxs-lookup"><span data-stu-id="ce976-122">Starting with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the null-coalescing operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="ce976-123">W powyższym przykładzie pokazano również, jak używać [składowych wyrażeń](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) w celu zdefiniowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="ce976-123">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="ce976-124">Począwszy od C# 8,0, można użyć operatora, `??=` aby zamienić kod formularza</span><span class="sxs-lookup"><span data-stu-id="ce976-124">Starting with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="ce976-125">przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ce976-125">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="ce976-126">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="ce976-126">Operator overloadability</span></span>

<span data-ttu-id="ce976-127">Operatory `??` i`??=` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="ce976-127">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ce976-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce976-128">C# language specification</span></span>

<span data-ttu-id="ce976-129">Aby uzyskać więcej informacji na `??` temat operatora, zobacz sekcję [operator łączenia null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ce976-129">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce976-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce976-130">See also</span></span>

- [<span data-ttu-id="ce976-131">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="ce976-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ce976-132">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ce976-132">C# operators</span></span>](index.md)
- <span data-ttu-id="ce976-133">[?. i ?[] Operatory](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="ce976-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="ce976-134">?: — operator</span><span class="sxs-lookup"><span data-stu-id="ce976-134">?: operator</span></span>](conditional-operator.md)
