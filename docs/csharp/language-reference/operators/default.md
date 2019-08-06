---
title: domyślny operator — C# odwołanie
ms.custom: seodec18
description: Użyj domyślnego operatora, aby utworzyć wartość domyślną typu
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 5623cb9dc3790b5bb99635c41cb3f122f4c71d8e
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68804239"
---
# <a name="default-operator-c-reference"></a><span data-ttu-id="d1d53-103">Default — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="d1d53-103">default operator (C# reference)</span></span>

<span data-ttu-id="d1d53-104">Operator generuje [wartość domyślną typu.](../keywords/default-values-table.md) `default`</span><span class="sxs-lookup"><span data-stu-id="d1d53-104">The `default` operator produces the [default value](../keywords/default-values-table.md) of a type.</span></span> <span data-ttu-id="d1d53-105">Argument `default` operatora musi być nazwą typu lub parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="d1d53-105">The argument to the `default` operator must be the name of a type or a type parameter.</span></span>

<span data-ttu-id="d1d53-106">W poniższym przykładzie pokazano sposób użycia `default` operatora:</span><span class="sxs-lookup"><span data-stu-id="d1d53-106">The following example shows the usage of the `default` operator:</span></span>

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

<span data-ttu-id="d1d53-107">Możesz również użyć `default` słowa kluczowego jako domyślnej etykiety case [ `switch` w instrukcji](../keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="d1d53-107">You also use the `default` keyword as the default case label within the [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-literal"></a><span data-ttu-id="d1d53-108">domyślny literał</span><span class="sxs-lookup"><span data-stu-id="d1d53-108">default literal</span></span>

<span data-ttu-id="d1d53-109">Począwszy od C# 7,1, można użyć `default` literału, aby utworzyć wartość domyślną typu, gdy kompilator może wywnioskować typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d1d53-109">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="d1d53-110">Wyrażenie literału zwraca tę samą wartość `default(T)` , co wyrażenie, `T` gdzie jest typem wywnioskowanym. `default`</span><span class="sxs-lookup"><span data-stu-id="d1d53-110">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="d1d53-111">`default` Literału można użyć w dowolnym z następujących przypadków:</span><span class="sxs-lookup"><span data-stu-id="d1d53-111">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="d1d53-112">W przypisaniu lub inicjacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d1d53-112">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="d1d53-113">W deklaracji wartości domyślnej dla opcjonalnego parametru metody.</span><span class="sxs-lookup"><span data-stu-id="d1d53-113">In the declaration of the default value for an optional method parameter.</span></span>
- <span data-ttu-id="d1d53-114">W wywołaniu metody, aby podać wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="d1d53-114">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="d1d53-115">W instrukcji `return` lub jako wyrażenie w składowej zawierającej wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d1d53-115">In a `return` statement or as an expression in an expression-bodied member.</span></span>

<span data-ttu-id="d1d53-116">W poniższym przykładzie pokazano użycie `default` literału:</span><span class="sxs-lookup"><span data-stu-id="d1d53-116">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="d1d53-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d1d53-117">C# language specification</span></span>

<span data-ttu-id="d1d53-118">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia wartości domyślnej](~/_csharplang/spec/expressions.md#default-value-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d1d53-118">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d1d53-119">Aby uzyskać więcej informacji na `default` temat literału, zapoznaj się z uwagami dotyczącymi [funkcji](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span><span class="sxs-lookup"><span data-stu-id="d1d53-119">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1d53-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1d53-120">See also</span></span>

- [<span data-ttu-id="d1d53-121">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="d1d53-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d1d53-122">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d1d53-122">C# operators</span></span>](index.md)
- [<span data-ttu-id="d1d53-123">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="d1d53-123">Default values table</span></span>](../keywords/default-values-table.md)
