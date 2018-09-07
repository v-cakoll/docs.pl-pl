---
title: var (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ab49a4f4fcbc990a1fd21139397d70fa9fbf5dd8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44088066"
---
# <a name="var-c-reference"></a><span data-ttu-id="72dd1-102">var (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="72dd1-102">var (C# Reference)</span></span>
<span data-ttu-id="72dd1-103">Począwszy od Visual C# 3.0, zmienne, które są zadeklarowane w zakresie metoda może mieć niejawne "type" `var`.</span><span class="sxs-lookup"><span data-stu-id="72dd1-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="72dd1-104">Niejawnie wpisane zmiennej lokalnej jest jednoznacznie określone typy, tak jak w przypadku możesz typu była zadeklarowana, ale kompilator Określa typ.</span><span class="sxs-lookup"><span data-stu-id="72dd1-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="72dd1-105">Poniższe dwie deklaracje `i` są funkcjonalnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="72dd1-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```csharp  
var i = 10; // Implicitly typed. 
int i = 10; // Explicitly typed. 
```  
  
 <span data-ttu-id="72dd1-106">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="72dd1-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72dd1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="72dd1-107">Example</span></span>  
 <span data-ttu-id="72dd1-108">Poniższy przykład przedstawia dwa wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="72dd1-108">The following example shows two query expressions.</span></span> <span data-ttu-id="72dd1-109">W pierwszym wyrażeniu użytkowania `var` jest dozwolone, ale nie jest wymagana, ponieważ typ wyniku zapytania może być jawnie wyrażona jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="72dd1-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="72dd1-110">Jednak w drugim wyrażeniu `var` umożliwia wynik, który ma być kolekcją typów anonimowych, i nazwę tego typu nie jest dostępny z wyjątkiem kompilatorowi sam.</span><span class="sxs-lookup"><span data-stu-id="72dd1-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="72dd1-111">Korzystanie z `var` eliminuje konieczność Utwórz nową klasę dla wyniku.</span><span class="sxs-lookup"><span data-stu-id="72dd1-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="72dd1-112">Należy pamiętać, że w przykładzie 2, `foreach` zmiennej iteracyjnej `item` również musi być wpisana niejawnie.</span><span class="sxs-lookup"><span data-stu-id="72dd1-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="72dd1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72dd1-113">See Also</span></span>

- [<span data-ttu-id="72dd1-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="72dd1-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="72dd1-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="72dd1-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="72dd1-116">Jawnie wpisane zmienne lokalne</span><span class="sxs-lookup"><span data-stu-id="72dd1-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
