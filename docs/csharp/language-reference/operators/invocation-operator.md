---
title: operator () - C# odwołania
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 3a0af33739c9cb4d090842219eba4ece9700ef89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689232"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1eb81-102">() — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="1eb81-102">() operator (C# Reference)</span></span>

<span data-ttu-id="1eb81-103">Nawiasy, `()`, są zwykle używane dla wywołania metody lub delegata lub wyrażenia cast.</span><span class="sxs-lookup"><span data-stu-id="1eb81-103">Parentheses, `()`, are typically used for method or delegate invocation or in cast expressions.</span></span>

<span data-ttu-id="1eb81-104">Możesz także użyć nawiasów, aby określić kolejność, w którym ma być operacji w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="1eb81-104">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="1eb81-105">Aby uzyskać więcej informacji, zobacz [Dodawanie nawiasów](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) części [operatory](../../programming-guide/statements-expressions-operators/operators.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="1eb81-105">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="1eb81-106">Listy uporządkowane według poziomu pierwszeństwo operatorów, zobacz [ C# operatory](index.md).</span><span class="sxs-lookup"><span data-stu-id="1eb81-106">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="method-invocation"></a><span data-ttu-id="1eb81-107">Wywołanie metody</span><span class="sxs-lookup"><span data-stu-id="1eb81-107">Method invocation</span></span>

<span data-ttu-id="1eb81-108">Poniższy przykład przedstawia sposób wywołania metody, z lub bez argumentów i delegata:</span><span class="sxs-lookup"><span data-stu-id="1eb81-108">The following example demonstrates how to invoke a method, with or without arguments, and a delegate:</span></span>

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

<span data-ttu-id="1eb81-109">Można także użyć nawiasów podczas wywołujesz [Konstruktor](../../programming-guide/classes-and-structs/constructors.md) z [ `new` ](../keywords/new-operator.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="1eb81-109">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with a [`new`](../keywords/new-operator.md) operator.</span></span>

<span data-ttu-id="1eb81-110">Aby uzyskać więcej informacji o metodach, zobacz [metody](../../programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="1eb81-110">For more information about methods, see [Methods](../../programming-guide/classes-and-structs/methods.md).</span></span> <span data-ttu-id="1eb81-111">Aby uzyskać więcej informacji na temat obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="1eb81-111">For more information about delegates, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="cast-expression"></a><span data-ttu-id="1eb81-112">Wyrażenie CAST</span><span class="sxs-lookup"><span data-stu-id="1eb81-112">Cast expression</span></span>

<span data-ttu-id="1eb81-113">Wyrażenie cast w postaci `(T)E` wywołuje operatora konwersji można przekonwertować wartości wyrażenia `E` na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="1eb81-113">A cast expression of the form `(T)E` invokes a conversion operator to convert the value of expression `E` to type `T`.</span></span> <span data-ttu-id="1eb81-114">Jeśli istnieje nie jawna konwersja z typu `E` na typ `T`, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1eb81-114">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="1eb81-115">Aby dowiedzieć się, jak definiowanie operatora konwersji, zobacz [jawne](../keywords/explicit.md) i [niejawne](../keywords/implicit.md) artykuły — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1eb81-115">For information about how to define a conversion operator, see the [explicit](../keywords/explicit.md) and [implicit](../keywords/implicit.md) keyword articles.</span></span>

<span data-ttu-id="1eb81-116">W poniższym przykładzie pokazano konwersja typu typy liczbowe:</span><span class="sxs-lookup"><span data-stu-id="1eb81-116">The following example demonstrates type conversion between numeric types:</span></span>

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

<span data-ttu-id="1eb81-117">Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych jawne konwersje między typów liczbowych, zobacz [Tabela jawnych konwersji liczbowych](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="1eb81-117">For more information about predefined explicit conversions between numeric types, see [Explicit numeric conversions table](../keywords/explicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="1eb81-118">Aby uzyskać więcej informacji, zobacz [konwersje rzutowania i typ](../../programming-guide/types/casting-and-type-conversions.md) i [operatory konwersji](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="1eb81-118">For more information, see [Casting and type conversions](../../programming-guide/types/casting-and-type-conversions.md) and [Conversion operators](../../programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1eb81-119">Overloadability — operator</span><span class="sxs-lookup"><span data-stu-id="1eb81-119">Operator overloadability</span></span>

<span data-ttu-id="1eb81-120">Operator `()` nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="1eb81-120">The operator `()` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1eb81-121">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1eb81-121">C# language specification</span></span>

<span data-ttu-id="1eb81-122">Aby uzyskać więcej informacji, zobacz [wyrażenia wywołania](~/_csharplang/spec/expressions.md#invocation-expressions) i [rzutowane wyrażenia,](~/_csharplang/spec/expressions.md#cast-expressions) sekcje [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1eb81-122">For more information, see the [Invocation expressions](~/_csharplang/spec/expressions.md#invocation-expressions) and [Cast expressions](~/_csharplang/spec/expressions.md#cast-expressions) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1eb81-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1eb81-123">See also</span></span>

- [<span data-ttu-id="1eb81-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1eb81-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1eb81-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1eb81-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1eb81-126">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1eb81-126">C# Operators</span></span>](index.md)