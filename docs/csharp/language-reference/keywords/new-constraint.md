---
title: New — ograniczenie - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: de0798319d91032143cb806d6d39338c4f51ac8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661168"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="7f251-102">New — ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7f251-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="7f251-103">`new` Ograniczenie Określa, że dowolny argument typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f251-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="7f251-104">Aby użyć nowego ograniczenia, typ nie może być abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="7f251-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="7f251-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f251-105">Example</span></span>

<span data-ttu-id="7f251-106">Zastosuj `new` ograniczenie parametru typu, gdy ogólne klasy tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7f251-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="7f251-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f251-107">Example</span></span>

<span data-ttu-id="7f251-108">Kiedy używasz `new()` ograniczenie z innymi ograniczeniami, musi być określona ostatnio:</span><span class="sxs-lookup"><span data-stu-id="7f251-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="7f251-109">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7f251-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f251-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7f251-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7f251-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f251-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="7f251-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7f251-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="7f251-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7f251-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f251-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7f251-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7f251-115">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="7f251-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="7f251-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7f251-116">Generics</span></span>](../../programming-guide/generics/index.md)