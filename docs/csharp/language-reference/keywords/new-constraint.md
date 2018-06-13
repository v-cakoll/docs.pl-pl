---
title: new — Ograniczenie (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268999"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="57ecf-102">new — Ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="57ecf-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="57ecf-103">`new` Ograniczenia Określa, że wszystkich argumentów typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="57ecf-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="57ecf-104">Aby użyć nowego ograniczenia, typu nie mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="57ecf-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57ecf-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="57ecf-105">Example</span></span>  
 <span data-ttu-id="57ecf-106">Zastosuj `new` ograniczenia parametru typu w klasie ogólnego tworzy nowych wystąpień tego typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="57ecf-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="57ecf-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="57ecf-107">Example</span></span>  
 <span data-ttu-id="57ecf-108">Jeśli używasz `new()` ograniczenia inne ograniczenia, musi zostać określona ostatnich:</span><span class="sxs-lookup"><span data-stu-id="57ecf-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="57ecf-109">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="57ecf-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="57ecf-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="57ecf-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="57ecf-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57ecf-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="57ecf-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="57ecf-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="57ecf-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="57ecf-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="57ecf-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="57ecf-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="57ecf-115">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="57ecf-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="57ecf-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="57ecf-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
