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
ms.openlocfilehash: 5262aa70bb5ec2f03dda9425194b89ec1e809d76
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038965"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="875de-103">??</span><span class="sxs-lookup"><span data-stu-id="875de-103">??</span></span> <span data-ttu-id="875de-104">i? = — OperatoryC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="875de-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="875de-105">Operator łączenia wartości null `??` zwraca wartość operandu po lewej stronie, jeśli nie `null`; w przeciwnym razie oblicza argument operacji po prawej stronie i zwraca jego wynik.</span><span class="sxs-lookup"><span data-stu-id="875de-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="875de-106">Operator `??` nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.</span><span class="sxs-lookup"><span data-stu-id="875de-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="875de-107">Dostępne w C# 8,0 i późniejszych, operator przypisania łączącej wartości null`??=`przypisuje wartość jego operandu po lewej stronie tylko wtedy, gdy operand po lewej stronie jest obliczany do`null`.</span><span class="sxs-lookup"><span data-stu-id="875de-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="875de-108">Operator `??=` nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.</span><span class="sxs-lookup"><span data-stu-id="875de-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="875de-109">Argument operacji po lewej stronie operatora `??=` musi być zmienną, [właściwością](../../programming-guide/classes-and-structs/properties.md)lub elementem [indeksatora](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="875de-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="875de-110">W C# 7,3 i starszych typach operandu po lewej stronie operatora`??`musi być typem referencyjnym lub [typem wartości null](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="875de-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a reference type or a [nullable value type](../../programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="875de-111">Począwszy od C# 8,0, ten wymóg jest zastępowany następującymi: typem operandu po lewej stronie operatorów`??`i`??=`nie może być typ wartości niedopuszczający wartości null.</span><span class="sxs-lookup"><span data-stu-id="875de-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="875de-112">W szczególności, począwszy od C# 8,0, można użyć operatorów łączenia wartości null z nieokreślonymi parametrami typu:</span><span class="sxs-lookup"><span data-stu-id="875de-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="875de-113">Operatory łączenia wartości null są z prawej strony skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="875de-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="875de-114">To jest wyrażenie w postaci</span><span class="sxs-lookup"><span data-stu-id="875de-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="875de-115">są oceniane jako</span><span class="sxs-lookup"><span data-stu-id="875de-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="875de-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="875de-116">Examples</span></span>

<span data-ttu-id="875de-117">Operatory `??` i `??=` mogą być przydatne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="875de-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="875de-118">W wyrażeniach zawierających [Operatory warunkowe o wartości null?. i? []](member-access-operators.md#null-conditional-operators--and-)można użyć operatora `??`, aby podać alternatywne wyrażenie do obliczenia w przypadku, gdy wynik wyrażenia z operacjami warunkowymi o wartości null jest `null`:</span><span class="sxs-lookup"><span data-stu-id="875de-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="875de-119">Podczas pracy z [typami wartości null](../../programming-guide/nullable-types/index.md) i musi podać wartość bazowego typu wartości, użyj operatora `??`, aby określić wartość, która ma zostać podana w przypadku, gdy wartość typu null jest `null`:</span><span class="sxs-lookup"><span data-stu-id="875de-119">When you work with [nullable value types](../../programming-guide/nullable-types/index.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="875de-120">Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, jeśli wartość, która ma zostać użyta, gdy wartość typu null jest `null` powinna być wartością domyślną bazowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="875de-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="875de-121">Począwszy od C# 7,0, można użyć [wyrażenia`throw`](../keywords/throw.md#the-throw-expression) jako wiersza operacji po prawej stronie operatora`??`, aby kod sprawdzania argumentów był bardziej zwięzły:</span><span class="sxs-lookup"><span data-stu-id="875de-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="875de-122">W powyższym przykładzie pokazano również, jak używać [składowych wyrażeń](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) w celu zdefiniowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="875de-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="875de-123">Począwszy od C# 8,0, można użyć operatora`??=`, aby zamienić kod formularza</span><span class="sxs-lookup"><span data-stu-id="875de-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="875de-124">przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="875de-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="875de-125">Przeciążanie operatora</span><span class="sxs-lookup"><span data-stu-id="875de-125">Operator overloadability</span></span>

<span data-ttu-id="875de-126">Operatory `??` i `??=` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="875de-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="875de-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="875de-127">C# language specification</span></span>

<span data-ttu-id="875de-128">Aby uzyskać więcej informacji na temat operatora `??`, zobacz sekcję [operator łączenia wartości null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="875de-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="875de-129">Aby uzyskać więcej informacji na temat operatora `??=`, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="875de-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="875de-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="875de-130">See also</span></span>

- [<span data-ttu-id="875de-131">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="875de-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="875de-132">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="875de-132">C# operators</span></span>](index.md)
- <span data-ttu-id="875de-133">[?. lub? operator []](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="875de-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="875de-134">?: — operator</span><span class="sxs-lookup"><span data-stu-id="875de-134">?: operator</span></span>](conditional-operator.md)
