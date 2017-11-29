---
title: "in (modyfikator ogólny) (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="0e8b6-102">in (modyfikator ogólny) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0e8b6-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="0e8b6-103">Parametry typu ogólnego `in` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="0e8b6-104">Można użyć `in` — słowo kluczowe w interfejsach i delegatów.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="0e8b6-105">Kontrawariancja pozwala na użycie typu mniej pochodnego od określonej przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="0e8b6-106">Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="0e8b6-107">Kowariancja i kontrawariancja w ogólnych parametrów typu są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="0e8b6-108">Typem może być deklarowana kontrawariantnego w ogólnym interfejsem ani obiektem delegowanym, jeśli jest używany tylko jako typ argumentów metody i nie jest używany jako typ zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="0e8b6-109">`Ref`i `out` parametrów nie może być wariantem.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="0e8b6-110">Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody akceptować argumenty mniej typów pochodnych niż określony przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="0e8b6-111">Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IComparer%601> interfejsu, jest typu T kontrawariantny, można przypisać obiektu `IComparer(Of Person)` typu do obiektu `IComparer(Of Employee)` typu bez użycia żadnych metod konwersji specjalne `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="0e8b6-112">Delegat kontrawariantnego można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="0e8b6-113">Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="0e8b6-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e8b6-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e8b6-114">Example</span></span>  
 <span data-ttu-id="0e8b6-115">Poniższy przykład pokazuje, jak można zadeklarować, rozszerzać i implementować interfejs generyczny kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="0e8b6-116">Pokazuje też, jak skorzystać z niejawnej konwersji dla klas, które implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="0e8b6-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e8b6-117">Example</span></span>  
 <span data-ttu-id="0e8b6-118">Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kontrawariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="0e8b6-119">Pokazuje też, jak można niejawnie przekonwertować typu delegata.</span><span class="sxs-lookup"><span data-stu-id="0e8b6-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0e8b6-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0e8b6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e8b6-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e8b6-121">See Also</span></span>  
 [<span data-ttu-id="0e8b6-122">limit</span><span class="sxs-lookup"><span data-stu-id="0e8b6-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="0e8b6-123">Kowariancja i Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="0e8b6-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="0e8b6-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="0e8b6-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
