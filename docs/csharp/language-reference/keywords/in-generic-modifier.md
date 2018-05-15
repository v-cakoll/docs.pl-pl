---
title: in (modyfikator ogólny) (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 003ce26fe9ba315eefc748a406754026231004b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="77aa5-102">in (modyfikator ogólny) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="77aa5-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="77aa5-103">Parametry typu ogólnego `in` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="77aa5-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="77aa5-104">Można użyć `in` — słowo kluczowe w interfejsach i delegatów.</span><span class="sxs-lookup"><span data-stu-id="77aa5-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="77aa5-105">Kontrawariancja pozwala na użycie typu mniej pochodnego od określonej przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="77aa5-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="77aa5-106">Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="77aa5-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="77aa5-107">Kowariancja i kontrawariancja w ogólnych parametrów typu są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="77aa5-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="77aa5-108">Typem może być deklarowana kontrawariantnego w ogólnym interfejsem ani obiektem delegowanym tylko wtedy, gdy definiuje typ parametrów metody, a nie typ zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="77aa5-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="77aa5-109">`In`, `ref`, i `out` parametry muszą być niezmienna, co oznacza ich nie należą do żadnej kowariantnego lub kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="77aa5-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>
  
 <span data-ttu-id="77aa5-110">Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody akceptować argumenty mniej typów pochodnych niż określony przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77aa5-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="77aa5-111">Na przykład w <xref:System.Collections.Generic.IComparer%601> interfejsu, jest typu T kontrawariantny, można przypisać obiektu `IComparer<Person>` typu do obiektu `IComparer<Employee>` typu bez użycia żadnych metod konwersji specjalne `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="77aa5-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="77aa5-112">Delegat kontrawariantnego można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="77aa5-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="77aa5-113">Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="77aa5-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="contravariant-generic-interface"></a><span data-ttu-id="77aa5-114">Interfejs ogólny kontrawariantnego</span><span class="sxs-lookup"><span data-stu-id="77aa5-114">Contravariant generic interface</span></span>   

 <span data-ttu-id="77aa5-115">Poniższy przykład pokazuje, jak można zadeklarować, rozszerzać i implementować interfejs generyczny kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="77aa5-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="77aa5-116">Pokazuje też, jak skorzystać z niejawnej konwersji dla klas, które implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="77aa5-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a><span data-ttu-id="77aa5-117">Delegat ogólny kontrawariantnego</span><span class="sxs-lookup"><span data-stu-id="77aa5-117">Contravariant generic delegate</span></span>  

 <span data-ttu-id="77aa5-118">Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kontrawariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="77aa5-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="77aa5-119">Pokazuje też, jak można niejawnie przekonwertować typu delegata.</span><span class="sxs-lookup"><span data-stu-id="77aa5-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="77aa5-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="77aa5-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77aa5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77aa5-121">See Also</span></span>  
 [<span data-ttu-id="77aa5-122">out</span><span class="sxs-lookup"><span data-stu-id="77aa5-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="77aa5-123">Kowariancja i kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="77aa5-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="77aa5-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="77aa5-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
