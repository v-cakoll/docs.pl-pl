---
title: domyślne wyrażenia wartości — odwołanie do języka C#
description: Użyj domyślnych wyrażeń wartości, aby uzyskać wartość domyślną typu
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 2adfd8d24066e9dad50c3c18407d3ade71b4b68e
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507181"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="2f266-103">domyślne wyrażenia wartości (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="2f266-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="2f266-104">Domyślne wyrażenie wartości tworzy [wartość domyślną](../builtin-types/default-values.md) typu.</span><span class="sxs-lookup"><span data-stu-id="2f266-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="2f266-105">Istnieją dwa rodzaje domyślnych wyrażeń wartości: [domyślne](#default-operator) wywołanie operatora i [domyślny literał](#default-literal).</span><span class="sxs-lookup"><span data-stu-id="2f266-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="2f266-106">`default` Słowo kluczowe służy również jako domyślna etykieta sprawy w [ `switch` instrukcji](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="2f266-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="2f266-107">default, operator</span><span class="sxs-lookup"><span data-stu-id="2f266-107">default operator</span></span>

<span data-ttu-id="2f266-108">Argumentem `default` operatora musi być nazwa typu lub parametru typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2f266-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="2f266-109">domyślny literał</span><span class="sxs-lookup"><span data-stu-id="2f266-109">default literal</span></span>

<span data-ttu-id="2f266-110">Począwszy od języka C# 7.1, można użyć `default` literału do uzyskania domyślnej wartości typu, gdy kompilator można wywnioskować typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2f266-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="2f266-111">Wyrażenie `default` dosłowne tworzy taką `default(T)` samą `T` wartość jak wyrażenie, gdzie jest typem wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="2f266-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="2f266-112">`default` Literał można użyć w dowolnym z następujących przypadków:</span><span class="sxs-lookup"><span data-stu-id="2f266-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="2f266-113">W przypisywaniu lub inicjalizacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2f266-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="2f266-114">W deklaracji wartości domyślnej dla [parametru metody opcjonalnej](../../methods.md#optional-parameters-and-arguments).</span><span class="sxs-lookup"><span data-stu-id="2f266-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="2f266-115">W wywołaniu metody, aby podać wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="2f266-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="2f266-116">W [ `return` instrukcji](../keywords/return.md) lub jako wyrażenie w wyrażeniu-zabudowany [element członkowski](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="2f266-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="2f266-117">W poniższym przykładzie `default` pokazano użycie literału:</span><span class="sxs-lookup"><span data-stu-id="2f266-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="2f266-118">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2f266-118">C# language specification</span></span>

<span data-ttu-id="2f266-119">Aby uzyskać więcej informacji, zobacz [sekcję Domyślne wyrażenia wartości](~/_csharplang/spec/expressions.md#default-value-expressions) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="2f266-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="2f266-120">Aby uzyskać więcej `default` informacji na temat literału, zobacz [notatkę dotyczącą propozycji funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="2f266-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f266-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f266-121">See also</span></span>

- [<span data-ttu-id="2f266-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2f266-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2f266-123">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="2f266-123">C# operators</span></span>](index.md)
- [<span data-ttu-id="2f266-124">Domyślne wartości typów języka C#</span><span class="sxs-lookup"><span data-stu-id="2f266-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="2f266-125">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="2f266-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
