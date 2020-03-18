---
title: operator domyślny — odwołanie do języka C#
description: Użyj domyślnego operatora do wytworzenia wartości domyślnej typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399484"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="1913b-103">operator domyślny (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="1913b-103">default operator (C# reference)</span></span>

<span data-ttu-id="1913b-104">Operator `default` tworzy [wartość domyślną](../builtin-types/default-values.md) typu.</span><span class="sxs-lookup"><span data-stu-id="1913b-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="1913b-105">Argument `default` do operatora musi być nazwa typu lub parametrtypu.</span><span class="sxs-lookup"><span data-stu-id="1913b-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="1913b-106">W poniższym przykładzie przedstawiono `default` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="1913b-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="1913b-107">Słowo `default` kluczowe jest również używane jako domyślna etykieta sprawy w [ `switch` instrukcji](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="1913b-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="1913b-108">literał domyślny</span><span class="sxs-lookup"><span data-stu-id="1913b-108">default literal</span></span>

<span data-ttu-id="1913b-109">Począwszy od Języka C# 7.1, można użyć `default` literału do produkcji wartości domyślnej typu, gdy kompilator można wywnioskować typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1913b-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="1913b-110">Wyrażenie `default` literału tworzy tę `default(T)` samą `T` wartość co wyrażenie, w którym jest typem wywnioskowanym.</span><span class="sxs-lookup"><span data-stu-id="1913b-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="1913b-111">Literału `default` można użyć w dowolnym z następujących przypadków:</span><span class="sxs-lookup"><span data-stu-id="1913b-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="1913b-112">W przypisaniu lub inicjowaniu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1913b-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="1913b-113">W deklaracji wartości domyślnej dla [parametru metody opcjonalnej](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="1913b-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="1913b-114">W wywołaniu metody, aby podać wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="1913b-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="1913b-115">W [ `return` instrukcji](../keywords/return.md) lub jako wyrażenie w [element członkowski zabudowany wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="1913b-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="1913b-116">W poniższym przykładzie przedstawiono `default` użycie literału:</span><span class="sxs-lookup"><span data-stu-id="1913b-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="1913b-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1913b-117">C# language specification</span></span>

<span data-ttu-id="1913b-118">Aby uzyskać więcej informacji, zobacz [sekcję Domyślne wyrażenia wartości](~/_csharplang/spec/expressions.md#default-value-expressions) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="1913b-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="1913b-119">Aby uzyskać więcej `default` informacji na temat literału, zobacz [notatkę propozycji funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="1913b-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1913b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1913b-120">See also</span></span>

- [<span data-ttu-id="1913b-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1913b-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1913b-122">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1913b-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="1913b-123">Domyślne wartości typów Języka C#</span><span class="sxs-lookup"><span data-stu-id="1913b-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="1913b-124">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="1913b-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
