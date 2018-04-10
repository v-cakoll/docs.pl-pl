---
title: var (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e0df25eb46bb769214412646d0ac3a7a576b3b73
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="var-c-reference"></a><span data-ttu-id="10a47-102">var (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="10a47-102">var (C# Reference)</span></span>
<span data-ttu-id="10a47-103">Począwszy od programu Visual C# 3.0, zmienne, które są zadeklarowane w zakresie metody może mieć niejawna "type" `var`.</span><span class="sxs-lookup"><span data-stu-id="10a47-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="10a47-104">Niejawnie wpisane zmienna lokalna jest silnie typizowane, tak jakby użytkownik typ ma zadeklarowany, ale kompilator Określa typ.</span><span class="sxs-lookup"><span data-stu-id="10a47-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="10a47-105">Deklaracje następujące dwa `i` działają tak samo:</span><span class="sxs-lookup"><span data-stu-id="10a47-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="10a47-106">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="10a47-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10a47-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="10a47-107">Example</span></span>  
 <span data-ttu-id="10a47-108">Poniższy przykład przedstawia dwa wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="10a47-108">The following example shows two query expressions.</span></span> <span data-ttu-id="10a47-109">W pierwszym wyrażeniu stosowania `var` jest dozwolone, ale nie jest wymagana, ponieważ typ wyniku zapytania można jawnie określone jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="10a47-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="10a47-110">Jednak w drugie wyrażenie `var` umożliwia wynik, który ma być kolekcją typów anonimowych i nazwę tego typu nie jest dostępny z wyjątkiem do samej siebie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="10a47-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="10a47-111">Użycie `var` nie ma konieczności Utwórz nową klasę dla wyniku.</span><span class="sxs-lookup"><span data-stu-id="10a47-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="10a47-112">Należy pamiętać, że w przykładzie #2 `foreach` zmiennej iteracji `item` musi również być niejawnie wpisanych.</span><span class="sxs-lookup"><span data-stu-id="10a47-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="10a47-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10a47-113">See Also</span></span>  
 [<span data-ttu-id="10a47-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="10a47-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="10a47-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="10a47-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="10a47-116">Jawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="10a47-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
