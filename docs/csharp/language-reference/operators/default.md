---
title: domyślny operator — C# odwołanie
description: Użyj operatora domyślnego, aby utworzyć wartość domyślną typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 651c4698514aee8cf4dab75ea32c98493e19a30b
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964622"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="77da7-103">Default — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="77da7-103">default operator (C# reference)</span></span>

<span data-ttu-id="77da7-104">Operator `default` generuje [wartość domyślną](../builtin-types/default-values.md) typu.</span><span class="sxs-lookup"><span data-stu-id="77da7-104">The `default` operator produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="77da7-105">Argument operatora `default` musi być nazwą typu lub parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="77da7-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="77da7-106">Poniższy przykład pokazuje użycie operatora `default`:</span><span class="sxs-lookup"><span data-stu-id="77da7-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="77da7-107">Możesz również użyć słowa kluczowego `default` jako domyślnej etykiety case w [instrukcji`switch`](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="77da7-107">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="77da7-108">domyślny literał</span><span class="sxs-lookup"><span data-stu-id="77da7-108">default literal</span></span>

<span data-ttu-id="77da7-109">Począwszy od C# 7,1, można użyć literału `default`, aby utworzyć wartość domyślną typu, gdy kompilator może wywnioskować typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="77da7-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="77da7-110">Wyrażenie `default` literału zwraca tę samą wartość co wyrażenie `default(T)`, gdzie `T` jest typem wywnioskowanym.</span><span class="sxs-lookup"><span data-stu-id="77da7-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="77da7-111">Literału `default` można użyć w dowolnym z następujących przypadków:</span><span class="sxs-lookup"><span data-stu-id="77da7-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="77da7-112">W przypisaniu lub inicjacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="77da7-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="77da7-113">W deklaracji wartości domyślnej dla [opcjonalnego parametru metody](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="77da7-113">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="77da7-114">W wywołaniu metody, aby podać wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="77da7-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="77da7-115">W [instrukcji`return`](../keywords/return.md) lub jako wyrażenie w [składowej](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)zawierającej wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="77da7-115">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="77da7-116">Poniższy przykład pokazuje użycie literału `default`:</span><span class="sxs-lookup"><span data-stu-id="77da7-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="77da7-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="77da7-117">C# language specification</span></span>

<span data-ttu-id="77da7-118">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia wartości domyślnej](~/_csharplang/spec/expressions.md#default-value-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="77da7-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="77da7-119">Aby uzyskać więcej informacji na temat literału `default`, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="77da7-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77da7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77da7-120">See also</span></span>

- [<span data-ttu-id="77da7-121">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="77da7-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="77da7-122">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="77da7-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="77da7-123">Wartości domyślne C# typów</span><span class="sxs-lookup"><span data-stu-id="77da7-123">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="77da7-124">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="77da7-124">Generics in .NET</span></span>](../../../standard/generics/index.md)
