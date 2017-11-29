---
title: "out — Modyfikator ogólny (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5c63fe2229d4b7190397d3ba98fa150c84a12fb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="be166-102">out — Modyfikator ogólny (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="be166-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="be166-103">Parametry typu ogólnego `out` — słowo kluczowe Określa, że parametr typu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="be166-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="be166-104">Można użyć `out` — słowo kluczowe w interfejsach i delegatów.</span><span class="sxs-lookup"><span data-stu-id="be166-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="be166-105">Kowariancja pozwala na użycie typu bardziej pochodnego od określonej przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="be166-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="be166-106">Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="be166-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="be166-107">Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="be166-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="be166-108">Interfejs, który ma parametr typu kowariantnego umożliwia sposobów niż określony przez parametr typu bardziej pochodnego typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="be166-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="be166-109">Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerabe(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez korzystania z żadnych metod konwersji specjalnych.</span><span class="sxs-lookup"><span data-stu-id="be166-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="be166-110">Kowariantnego delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodny parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="be166-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="be166-111">Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="be166-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be166-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="be166-112">Example</span></span>  
 <span data-ttu-id="be166-113">Poniższy przykład pokazuje, jak zadeklarować, rozszerzać i implementacji kowariantnego interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="be166-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="be166-114">On również przedstawia użycie niejawna konwersja dla klas implementujących interfejs kowariantny.</span><span class="sxs-lookup"><span data-stu-id="be166-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="be166-115">W interfejsie ogólny parametru typu mogą być deklarowane jako kowariantnego, spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="be166-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="be166-116">Parametr typu jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="be166-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be166-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="be166-117">There is one exception to this rule.</span></span> <span data-ttu-id="be166-118">Jeśli w interfejsie kowariantnego to delegat generyczny kontrawariantnego jako parametr metody, można użyć typu kowariantnego jako parametr typu ogólnego dla tego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="be166-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="be166-119">Aby uzyskać więcej informacji na temat kowariantnego i kontrawariantnego delegatów, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancję Func i delegatów akcji](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="be166-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="be166-120">Parametr typu nie jest używany jako ogólne ograniczenia dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="be166-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be166-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="be166-121">Example</span></span>  
 <span data-ttu-id="be166-122">Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kowariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="be166-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="be166-123">Widoczny jest również sposób niejawnie przekonwertować typu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="be166-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="be166-124">Delegat ogólny typu mogą być deklarowane kowariantnego Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="be166-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="be166-125">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="be166-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be166-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be166-126">See Also</span></span>  
 [<span data-ttu-id="be166-127">Wariancje w interfejsach</span><span class="sxs-lookup"><span data-stu-id="be166-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="be166-128">w</span><span class="sxs-lookup"><span data-stu-id="be166-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="be166-129">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="be166-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
