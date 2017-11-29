---
title: "new — Ograniczenie (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="e66c5-102">new — Ograniczenie (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e66c5-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="e66c5-103">`new` Ograniczenia Określa, że wszystkich argumentów typu w deklaracji klasy ogólnej musi mieć publicznego konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="e66c5-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="e66c5-104">Aby użyć nowego ograniczenia, typu nie mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="e66c5-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e66c5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e66c5-105">Example</span></span>  
 <span data-ttu-id="e66c5-106">Zastosuj `new` ograniczenia parametru typu w klasie ogólnego tworzy nowych wystąpień tego typu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e66c5-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e66c5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e66c5-107">Example</span></span>  
 <span data-ttu-id="e66c5-108">Jeśli używasz `new()` ograniczenia inne ograniczenia, musi zostać określona ostatnich:</span><span class="sxs-lookup"><span data-stu-id="e66c5-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="e66c5-109">Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e66c5-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e66c5-110">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e66c5-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e66c5-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e66c5-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="e66c5-112">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="e66c5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e66c5-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e66c5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e66c5-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e66c5-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e66c5-115">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="e66c5-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="e66c5-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="e66c5-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
