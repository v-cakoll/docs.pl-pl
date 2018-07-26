---
title: out — Modyfikator ogólny (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245089"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="62a0b-102">out — Modyfikator ogólny (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="62a0b-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="62a0b-103">Dla parametrów typu genetycznego `out` — słowo kluczowe Określa, że parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="62a0b-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="62a0b-104">Możesz użyć `out` — słowo kluczowe w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="62a0b-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="62a0b-105">Kowariancja umożliwia użycie typu bardziej pochodnego niż określona przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="62a0b-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="62a0b-106">Umożliwia to niejawna konwersja klasy, które implementują interfejsów typu variant i niejawnej konwersji typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="62a0b-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="62a0b-107">Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="62a0b-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="62a0b-108">Interfejs, który ma kowariantnego parametru typu umożliwia jego metod zwrócić więcej typów pochodnych niż określony przez parametr typu.</span><span class="sxs-lookup"><span data-stu-id="62a0b-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="62a0b-109">Na przykład ponieważ w programie .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerable(Of String)` typ obiektu `IEnumerable(Of Object)` typu bez przy użyciu dowolnej metody konwersji specjalne.</span><span class="sxs-lookup"><span data-stu-id="62a0b-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="62a0b-110">Kowariantne delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="62a0b-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="62a0b-111">Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="62a0b-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62a0b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="62a0b-112">Example</span></span>  
 <span data-ttu-id="62a0b-113">Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kowariantny.</span><span class="sxs-lookup"><span data-stu-id="62a0b-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="62a0b-114">Pokazano również, jak używać niejawna konwersja dla klas, które implementują interfejs kowariantny.</span><span class="sxs-lookup"><span data-stu-id="62a0b-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="62a0b-115">W interfejsie ogólnego parametr typu mogą być deklarowane jako kowariantny, jeśli spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="62a0b-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="62a0b-116">Parametr typu jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="62a0b-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="62a0b-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="62a0b-117">There is one exception to this rule.</span></span> <span data-ttu-id="62a0b-118">Jeśli w interfejsie kowariantne Delegat ogólny kontrawariantny, jako parametru metody, można użyć kowariantnego typu co parametr typu ogólnego, dla tego delegata.</span><span class="sxs-lookup"><span data-stu-id="62a0b-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="62a0b-119">Aby uzyskać więcej informacji na temat kowariantne i kontrawariantne delegatów ogólnych, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych Func i](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="62a0b-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="62a0b-120">Parametr typu nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="62a0b-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62a0b-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="62a0b-121">Example</span></span>  
 <span data-ttu-id="62a0b-122">Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania kowariantne Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="62a0b-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="62a0b-123">Pokazano również, jak można niejawnie przekonwertować typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="62a0b-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="62a0b-124">Delegat ogólny typ może być zadeklarowana kowariantne Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="62a0b-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="62a0b-125">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="62a0b-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62a0b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62a0b-126">See Also</span></span>  
 [<span data-ttu-id="62a0b-127">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="62a0b-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="62a0b-128">in</span><span class="sxs-lookup"><span data-stu-id="62a0b-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="62a0b-129">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="62a0b-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
