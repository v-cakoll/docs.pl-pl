---
title: nowe ograniczenie — odwołanie w C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 6f6d1b663d03dc9b3adf0e7055dcffacc79d83dc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795342"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="beb39-102">New — ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="beb39-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="beb39-103">`new` Ograniczenie określa, że argument typu w deklaracji klasy ogólnej musi mieć publiczny Konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="beb39-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="beb39-104">Aby użyć `new` ograniczenia, typ nie może być abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="beb39-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="beb39-105">Zastosuj `new` ograniczenie do parametru typu, gdy Klasa ogólna tworzy nowe wystąpienia typu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="beb39-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="beb39-106">W `new()` przypadku użycia ograniczenia z innymi ograniczeniami należy je określić Last:</span><span class="sxs-lookup"><span data-stu-id="beb39-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="beb39-107">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="beb39-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="beb39-108">Możesz również użyć słowa kluczowego, `new` aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [modyfikator deklaracji składowej](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="beb39-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="beb39-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="beb39-109">C# language specification</span></span>

<span data-ttu-id="beb39-110">Aby uzyskać więcej informacji, zobacz sekcję [ograniczenia parametrów typu](~/_csharplang/spec/classes.md#type-parameter-constraints) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="beb39-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="beb39-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="beb39-111">See also</span></span>

- [<span data-ttu-id="beb39-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="beb39-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="beb39-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="beb39-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="beb39-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="beb39-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="beb39-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="beb39-115">Generics</span></span>](../../programming-guide/generics/index.md)
