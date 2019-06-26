---
title: New — ograniczenie - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401493"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="0f4cc-102">New — ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0f4cc-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="0f4cc-103">`new` Ograniczenie Określa, że argument typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="0f4cc-104">Aby użyć `new` ograniczenia, typ nie może być abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="0f4cc-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="0f4cc-105">Zastosuj `new` ograniczenie parametru typu, gdy klasa generyczna tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0f4cc-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="0f4cc-106">Kiedy używasz `new()` ograniczenie z innymi ograniczeniami, musi być określona ostatnio:</span><span class="sxs-lookup"><span data-stu-id="0f4cc-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="0f4cc-107">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0f4cc-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="0f4cc-108">Można również użyć `new` słowa kluczowego [utworzenia wystąpienia typu](../operators/new-operator.md) lub jako [modyfikator deklaracji elementu członkowskiego](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="0f4cc-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0f4cc-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0f4cc-109">C# language specification</span></span>

<span data-ttu-id="0f4cc-110">Aby uzyskać więcej informacji, zobacz [ograniczenia parametru typu](~/_csharplang/spec/classes.md#type-parameter-constraints) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0f4cc-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f4cc-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f4cc-111">See also</span></span>

- [<span data-ttu-id="0f4cc-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0f4cc-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="0f4cc-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0f4cc-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0f4cc-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0f4cc-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0f4cc-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="0f4cc-115">Generics</span></span>](../../programming-guide/generics/index.md)
