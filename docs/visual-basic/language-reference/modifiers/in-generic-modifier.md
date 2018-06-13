---
title: In (modyfikator ogólny) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d1d9209cd583ac96ece59660ad29c76a66d3395a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597435"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="7b241-102">In (modyfikator ogólny) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b241-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="7b241-103">Parametry typu ogólnego `In` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="7b241-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b241-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b241-104">Remarks</span></span>  
 <span data-ttu-id="7b241-105">Kontrawariancja pozwala na użycie typu mniej pochodnego od określonej przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="7b241-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="7b241-106">Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="7b241-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="7b241-107">Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="7b241-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7b241-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="7b241-108">Rules</span></span>  
 <span data-ttu-id="7b241-109">Można użyć `In` — słowo kluczowe w interfejsach i delegatów.</span><span class="sxs-lookup"><span data-stu-id="7b241-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="7b241-110">Parametr typu mogą być deklarowane kontrawariantnego w ogólny interfejs lub delegat, jeśli jest używany tylko jako typ argumentów metody i nie jest używany jako typ zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="7b241-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="7b241-111">`ByRef` Parametry nie mogą być kowariantnego lub kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="7b241-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="7b241-112">Kowariancja i kontrawariancja są obsługiwane dla typów referencyjnych i nie jest obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="7b241-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="7b241-113">W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kontrawariantnego bez określania typu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="7b241-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="7b241-114">Ponadto kontrawariantnego interfejsów nie mogą mieć zagnieżdżonych klas, wyliczeń lub struktury, ale można mieć zagnieżdżonych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7b241-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7b241-115">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="7b241-115">Behavior</span></span>  
 <span data-ttu-id="7b241-116">Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody akceptować argumenty mniej typów pochodnych niż określony przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7b241-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="7b241-117">Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IComparer%601> interfejsu, jest typu T kontrawariantny, można przypisać obiektu `IComparer(Of Person)` typu do obiektu `IComparer(Of Employee)` typu bez użycia żadnych metod konwersji specjalne `Person` dziedziczy `Employee`.</span><span class="sxs-lookup"><span data-stu-id="7b241-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="7b241-118">Delegat kontrawariantnego można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7b241-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b241-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b241-119">Example</span></span>  
 <span data-ttu-id="7b241-120">Poniższy przykład pokazuje, jak można zadeklarować, rozszerzać i implementować interfejs generyczny kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="7b241-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="7b241-121">Pokazuje też, jak skorzystać z niejawnej konwersji dla klas, które implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="7b241-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7b241-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b241-122">Example</span></span>  
 <span data-ttu-id="7b241-123">Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kontrawariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="7b241-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="7b241-124">Pokazuje też, jak można niejawnie przekonwertować typu delegata.</span><span class="sxs-lookup"><span data-stu-id="7b241-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b241-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b241-125">See Also</span></span>  
 [<span data-ttu-id="7b241-126">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="7b241-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="7b241-127">limit</span><span class="sxs-lookup"><span data-stu-id="7b241-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
