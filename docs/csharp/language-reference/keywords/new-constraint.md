---
title: new — Ograniczenie (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199466"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="5b91b-102">new — Ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5b91b-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="5b91b-103">`new` Ograniczenie Określa, że dowolny argument typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="5b91b-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="5b91b-104">Aby użyć nowego ograniczenia, typ nie może być abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="5b91b-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b91b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b91b-105">Example</span></span>  
 <span data-ttu-id="5b91b-106">Zastosuj `new` ograniczenie parametru typu, gdy ogólne klasy tworzy nowe wystąpienia typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5b91b-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="5b91b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b91b-107">Example</span></span>  
 <span data-ttu-id="5b91b-108">Kiedy używasz `new()` ograniczenie z innymi ograniczeniami, musi być określona ostatnio:</span><span class="sxs-lookup"><span data-stu-id="5b91b-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="5b91b-109">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5b91b-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5b91b-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5b91b-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b91b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b91b-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="5b91b-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5b91b-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5b91b-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5b91b-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5b91b-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5b91b-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5b91b-115">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="5b91b-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="5b91b-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5b91b-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
