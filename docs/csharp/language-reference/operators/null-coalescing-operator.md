---
title: ?? I?? = operatory - odwołanie c#
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847316"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="b3c7b-103">??</span><span class="sxs-lookup"><span data-stu-id="b3c7b-103">??</span></span> <span data-ttu-id="b3c7b-104">I?? = operatory (odwołanie do Języka C#)</span><span class="sxs-lookup"><span data-stu-id="b3c7b-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="b3c7b-105">Operator `??` null-łączenie zwraca wartość jego operand po lewej stronie, jeśli `null`nie jest ; w przeciwnym razie ocenia argument po prawej stronie i zwraca jego wynik.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="b3c7b-106">Operator `??` nie ocenia jego prawostronny operand, jeśli po lewej stronie operand ocenia non-null.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="b3c7b-107">Dostępne w języku C# 8.0 i nowszych `??=` operator przypisania null-łączenie przypisuje wartość jego operand po prawej stronie do jego operand po lewej stronie tylko wtedy, gdy po lewej stronie operand ocenia . `null`</span><span class="sxs-lookup"><span data-stu-id="b3c7b-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="b3c7b-108">Operator `??=` nie ocenia jego prawostronny operand, jeśli po lewej stronie operand ocenia non-null.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="b3c7b-109">Operand po lewej stronie `??=` operatora musi być zmienną, [właściwością](../../programming-guide/classes-and-structs/properties.md)lub elementem [indeksatora.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="b3c7b-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="b3c7b-110">W języku C# 7.3 i wcześniejszych typ operandu po lewej stronie `??` operatora musi być [typem odwołania](../keywords/reference-types.md) lub [typem wartości nullable](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b3c7b-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="b3c7b-111">Począwszy od Języka C# 8.0, to wymaganie jest zastępowane następującymi: typ operand po lewej stronie `??` i `??=` operatorów nie może być typem wartości niedopuszczająca wartości.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="b3c7b-112">W szczególności, począwszy od Języka C# 8.0, można użyć null-łączenie operatorów z nieograniczonymi parametrami typu:</span><span class="sxs-lookup"><span data-stu-id="b3c7b-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="b3c7b-113">Operatory null-łączenia są zasocjałe.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="b3c7b-114">Oznacza to, że wyrażenia formy</span><span class="sxs-lookup"><span data-stu-id="b3c7b-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="b3c7b-115">są oceniane jako</span><span class="sxs-lookup"><span data-stu-id="b3c7b-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="b3c7b-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b3c7b-116">Examples</span></span>

<span data-ttu-id="b3c7b-117">`??` Operatory `??=` i mogą być przydatne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="b3c7b-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="b3c7b-118">W wyrażeniach z [operatorami warunkowymi zerowymi ?. i ?[]](member-access-operators.md#null-conditional-operators--and-)można użyć `??` operatora, aby zapewnić wyrażenie alternatywne `null`do oceny w przypadku, gdy wynik wyrażenia z operacjami warunkowymi zerowymi jest:</span><span class="sxs-lookup"><span data-stu-id="b3c7b-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="b3c7b-119">Podczas pracy z [typami wartości nullable](../builtin-types/nullable-value-types.md) i trzeba podać wartość podstawowego typu wartości, należy użyć `??` operatora, aby `null`określić wartość, aby podać w przypadku wartości typu nullable jest:</span><span class="sxs-lookup"><span data-stu-id="b3c7b-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="b3c7b-120">Użyj <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metody, jeśli wartość, która ma być `null` używana, gdy wartość typu nulljest powinna być wartością domyślną podstawowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="b3c7b-121">Począwszy od języka C# 7.0, można użyć [ `throw` wyrażenia](../keywords/throw.md#the-throw-expression) jako `??` operand po prawej stronie operatora, aby kod sprawdzania argumentów bardziej zwięzły:</span><span class="sxs-lookup"><span data-stu-id="b3c7b-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="b3c7b-122">W poprzednim przykładzie pokazano również, jak używać [elementów członkowskich zabudowanych wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) do definiowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="b3c7b-123">Począwszy od języka C# 8.0, można użyć `??=` operatora, aby zastąpić kod formularza</span><span class="sxs-lookup"><span data-stu-id="b3c7b-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="b3c7b-124">z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="b3c7b-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="b3c7b-125">Przeciążenie operatora</span><span class="sxs-lookup"><span data-stu-id="b3c7b-125">Operator overloadability</span></span>

<span data-ttu-id="b3c7b-126">Operatory `??` `??=` i nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="b3c7b-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b3c7b-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b3c7b-127">C# language specification</span></span>

<span data-ttu-id="b3c7b-128">Aby uzyskać więcej `??` informacji na temat operatora, zobacz [null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="b3c7b-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="b3c7b-129">Aby uzyskać więcej `??=` informacji na temat operatora, zobacz [notę propozycji funkcji](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="b3c7b-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3c7b-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3c7b-130">See also</span></span>

- [<span data-ttu-id="b3c7b-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b3c7b-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b3c7b-132">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="b3c7b-132">C# operators</span></span>](index.md)
- <span data-ttu-id="b3c7b-133">[?. I? [] operatorzy](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="b3c7b-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="b3c7b-134">?: operator</span><span class="sxs-lookup"><span data-stu-id="b3c7b-134">?: operator</span></span>](conditional-operator.md)
