---
title: nowe ograniczenie — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713357"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="c364d-102">nowe ograniczenie (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="c364d-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="c364d-103">Ograniczenie `new` określa, że argument typu w deklaracji klasy ogólnej musi mieć konstruktora public parameterless.</span><span class="sxs-lookup"><span data-stu-id="c364d-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="c364d-104">Aby użyć `new` ograniczenia, typ nie może być abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="c364d-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="c364d-105">Zastosuj `new` ograniczenie do parametru typu, gdy klasa ogólna tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c364d-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="c364d-106">W przypadku `new()` używania ograniczenia z innymi ograniczeniami należy je określić jako ostatnie:</span><span class="sxs-lookup"><span data-stu-id="c364d-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="c364d-107">Aby uzyskać więcej informacji, zobacz [Ograniczenia parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c364d-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="c364d-108">Można również użyć `new` słowa kluczowego, aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [modyfikator deklaracji elementu członkowskiego](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="c364d-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c364d-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c364d-109">C# language specification</span></span>

<span data-ttu-id="c364d-110">Aby uzyskać więcej informacji, zobacz sekcję [Ograniczeń parametrów type](~/_csharplang/spec/classes.md#type-parameter-constraints) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="c364d-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c364d-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c364d-111">See also</span></span>

- [<span data-ttu-id="c364d-112">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c364d-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="c364d-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="c364d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c364d-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c364d-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c364d-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c364d-115">Generics</span></span>](../../programming-guide/generics/index.md)
