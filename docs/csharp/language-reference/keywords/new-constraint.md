---
title: nowe ograniczenie — C# odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713357"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="34eba-102">nowe ograniczenie (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="34eba-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="34eba-103">Ograniczenie `new` określa, że argument typu w deklaracji klasy ogólnej musi mieć publiczny Konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="34eba-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="34eba-104">Aby użyć ograniczenia `new`, typ nie może być abstrakcyjny.</span><span class="sxs-lookup"><span data-stu-id="34eba-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="34eba-105">Zastosuj ograniczenie `new` do parametru typu, gdy Klasa ogólna tworzy nowe wystąpienia typu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="34eba-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="34eba-106">W przypadku użycia ograniczenia `new()` z innymi ograniczeniami należy określić wartość Last:</span><span class="sxs-lookup"><span data-stu-id="34eba-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="34eba-107">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="34eba-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="34eba-108">Można również użyć słowa kluczowego `new`, aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [modyfikator deklaracji składowej](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="34eba-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="34eba-109">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="34eba-109">C# language specification</span></span>

<span data-ttu-id="34eba-110">Aby uzyskać więcej informacji, zobacz sekcję [ograniczenia parametrów typu](~/_csharplang/spec/classes.md#type-parameter-constraints) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="34eba-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34eba-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34eba-111">See also</span></span>

- [<span data-ttu-id="34eba-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="34eba-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="34eba-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="34eba-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="34eba-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="34eba-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="34eba-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="34eba-115">Generics</span></span>](../../programming-guide/generics/index.md)
