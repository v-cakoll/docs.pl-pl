---
title: FALSE — operator (odwołanie w C#)
ms.date: 12/03/2018
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: 4428d88acb08246623e2deb71a9daf7fb1cca692
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152308"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="ba6d9-102">FALSE — operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ba6d9-102">false operator (C# Reference)</span></span>

<span data-ttu-id="ba6d9-103">Zwraca [bool](bool.md) wartość `true` do wskazania, że argument jest zdecydowanie false.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-103">Returns the [bool](bool.md) value `true` to indicate that an operand is definitely false.</span></span> <span data-ttu-id="ba6d9-104">Jeśli typ definiuje `false` operatora on również muszą definiować [true — operator](true-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ba6d9-104">If a type defines the `false` operator, it must also define the [true operator](true-operator.md).</span></span> <span data-ttu-id="ba6d9-105">`true` i `false` operatorów nie ma gwarancji uzupełniają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-105">The `true` and `false` operators are not guaranteed to complement each other.</span></span>

> [!TIP]
> <span data-ttu-id="ba6d9-106">Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu logicznego.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-106">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued logical type.</span></span> <span data-ttu-id="ba6d9-107">Aby uzyskać więcej informacji, zobacz [bool? typu](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-107">For more information, see [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="ba6d9-108">Jeśli typ za pomocą zdefiniowanego `false` operator [przeciążenia](operator.md) [logicznego operatora AND](../operators/and-operator.md) `&` w określony sposób, [warunkowego operator logiczny AND](../operators/conditional-and-operator.md) `&&`, czyli short-circuiting, mogą być obliczane w przypadku argumentów operacji tego typu.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-108">If a type with the defined `false` operator [overloads](operator.md) the [logical AND operator](../operators/and-operator.md) `&` in a certain way, the [conditional logical AND operator](../operators/conditional-and-operator.md) `&&`, which is short-circuiting, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="ba6d9-109">Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba6d9-109">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

<span data-ttu-id="ba6d9-110">Poniższy przykład przedstawia typ, który określa zarówno `true` i `false` operatorów.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-110">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="ba6d9-111">Ponadto przeciąża logicznego operatora AND `&` w taki sposób, że operator `&&` mogą być obliczane dla argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-111">Moreover, it overloads the logical AND operator `&` in such a way that the operator `&&` also can be evaluated for the operands of that type.</span></span>

[!code-csharp-interactive[true and false operators example](~/samples/snippets/csharp/keywords/TrueFalseOperatorsExample.cs)]

<span data-ttu-id="ba6d9-112">Zwróć uwagę, zachowanie short-circuiting `&&` operatora.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-112">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="ba6d9-113">Gdy `GetFuelLaunchStatus` metoda zwraca `LaunchStatus.Red`, drugi operand `&&` operator nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-113">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the second operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="ba6d9-114">To dlatego, że `LaunchStatus.Red` ma zdecydowanie wartość false.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-114">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="ba6d9-115">Następnie wynik logicznego i nie zależy od wartości drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-115">Then the result of the logical AND doesn't depend on the value of the second operand.</span></span> <span data-ttu-id="ba6d9-116">Dane wyjściowe z przykładu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="ba6d9-116">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

<span data-ttu-id="ba6d9-117">Ponadto należy zauważyć, że wyrażenie warunkowe w [operator warunkowy `?:` ](../operators/conditional-operator.md) jest `LaunchStatus` typu.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-117">Also notice that the conditional expression in the [conditional operator `?:`](../operators/conditional-operator.md) is of the `LaunchStatus` type.</span></span> <span data-ttu-id="ba6d9-118">Jest to możliwe, ponieważ `LaunchStatus` definiuje `true` operatora.</span><span class="sxs-lookup"><span data-stu-id="ba6d9-118">That is possible, because `LaunchStatus` defines the `true` operator.</span></span> <span data-ttu-id="ba6d9-119">Aby uzyskać więcej informacji, zobacz [wyrażeń logicznych](~/_csharplang/spec/expressions.md#boolean-expressions) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba6d9-119">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba6d9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba6d9-120">See also</span></span>

- [<span data-ttu-id="ba6d9-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ba6d9-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ba6d9-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ba6d9-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ba6d9-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ba6d9-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ba6d9-124">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ba6d9-124">C# Operators</span></span>](../operators/index.md)
- [<span data-ttu-id="ba6d9-125">`false` literał</span><span class="sxs-lookup"><span data-stu-id="ba6d9-125">`false` literal</span></span>](false-literal.md)