---
title: New — ograniczenie (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 9948fc65030a4636c5d23db4ef8c3a584018d2f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482154"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="9ff8d-102">New — ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9ff8d-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="9ff8d-103">`new` Ograniczenie Określa, że dowolny argument typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="9ff8d-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="9ff8d-104">Aby użyć nowego ograniczenia, typ nie może być abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="9ff8d-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="9ff8d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ff8d-105">Example</span></span>

<span data-ttu-id="9ff8d-106">Zastosuj `new` ograniczenie parametru typu, gdy ogólne klasy tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9ff8d-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="9ff8d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ff8d-107">Example</span></span>

<span data-ttu-id="9ff8d-108">Kiedy używasz `new()` ograniczenie z innymi ograniczeniami, musi być określona ostatnio:</span><span class="sxs-lookup"><span data-stu-id="9ff8d-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="9ff8d-109">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9ff8d-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9ff8d-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9ff8d-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9ff8d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ff8d-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="9ff8d-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9ff8d-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9ff8d-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9ff8d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9ff8d-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9ff8d-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9ff8d-115">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="9ff8d-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="9ff8d-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="9ff8d-116">Generics</span></span>](../../programming-guide/generics/index.md)