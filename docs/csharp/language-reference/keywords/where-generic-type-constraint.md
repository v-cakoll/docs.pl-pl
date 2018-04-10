---
title: where — Ograniczenie typu ogólnego (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="4b049-102">where — Ograniczenie typu ogólnego (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4b049-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="4b049-103">W definicji typu ogólnego `where` klauzuli służy do określania warunków ograniczających dla typów, które mogą być używane jako argumenty dla parametru typu zdefiniowanego w deklaracji ogólnej.</span><span class="sxs-lookup"><span data-stu-id="4b049-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="4b049-104">Na przykład można zadeklarować klasy ogólnej, `MyGenericClass`, że parametr typu `T` implementuje <xref:System.IComparable%601> interfejsu:</span><span class="sxs-lookup"><span data-stu-id="4b049-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="4b049-105">Aby uzyskać więcej informacji o tym, gdzie klauzula w wyrażeniu zapytania, zobacz [gdzie klauzuli](../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4b049-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="4b049-106">Oprócz ograniczeń interfejsu `where` klauzuli mogą zawierać ograniczenia klasy podstawowej, które stwierdza, że typ musi mieć określony klasy jako klasę podstawową (lub w tej samej klasy), aby można używać jako argumentu typu dla tego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="4b049-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="4b049-107">Jeśli używane jest takie ograniczenie, musi występować przed wszystkimi innymi ograniczeniami dla tego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="4b049-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 <span data-ttu-id="4b049-108">`where` Klauzuli mogą również obejmować ograniczenie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4b049-108">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="4b049-109">Można utworzyć wystąpienia typu parametru za pomocą operatora new; Jednak w tym celu parametr typu musi być ograniczone przez ograniczenie konstruktora `new()`.</span><span class="sxs-lookup"><span data-stu-id="4b049-109">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="4b049-110">[Ograniczenia new()](../../../csharp/language-reference/keywords/new-constraint.md) umożliwia kompilatora wiedzieć, że wszelkie argumentu typu dostarczonego musi mieć dostęp bez parametrów--lub konstruktora domyślnego —.</span><span class="sxs-lookup"><span data-stu-id="4b049-110">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="4b049-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4b049-111">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 <span data-ttu-id="4b049-112">`new()` Ograniczenia pojawia się w ostatniej `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4b049-112">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="4b049-113">Wiele parametrów typu, za pomocą jednego `where` klauzula dla każdego parametru typu, na przykład:</span><span class="sxs-lookup"><span data-stu-id="4b049-113">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 <span data-ttu-id="4b049-114">Można również dołączyć ograniczenia na parametry metody rodzajowe podobny do tego typu:</span><span class="sxs-lookup"><span data-stu-id="4b049-114">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="4b049-115">Zauważ, że opis ograniczenia parametru typu delegatów składni jest takie samo jak w przypadku metod:</span><span class="sxs-lookup"><span data-stu-id="4b049-115">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="4b049-116">Informacje ogólne delegatów, zobacz [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4b049-116">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="4b049-117">Aby uzyskać więcej informacji o składni i użycia ograniczenia, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4b049-117">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4b049-118">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4b049-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b049-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b049-119">See Also</span></span>  
 [<span data-ttu-id="4b049-120">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4b049-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4b049-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4b049-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4b049-122">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="4b049-122">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="4b049-123">New — ograniczenie</span><span class="sxs-lookup"><span data-stu-id="4b049-123">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="4b049-124">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="4b049-124">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
