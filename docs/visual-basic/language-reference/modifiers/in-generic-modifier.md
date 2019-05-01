---
title: In (modyfikator ogólny) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d8d503f0814a89c977cdc208eced026b2d8cb1fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802476"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="18207-102">In (modyfikator ogólny) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18207-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="18207-103">Dla parametrów typu genetycznego `In` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="18207-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18207-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18207-104">Remarks</span></span>  
 <span data-ttu-id="18207-105">Kontrawariancja umożliwia używania typu mniej pochodnego niż określona przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="18207-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="18207-106">Umożliwia to niejawna konwersja klasy, które implementują interfejsów typu variant i niejawnej konwersji typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="18207-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="18207-107">Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="18207-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="18207-108">reguły</span><span class="sxs-lookup"><span data-stu-id="18207-108">Rules</span></span>  
 <span data-ttu-id="18207-109">Możesz użyć `In` — słowo kluczowe w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="18207-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="18207-110">Parametr typu mogą być deklarowane kontrawariantnego w ogólny interfejs lub delegat, jeśli jest używany tylko jako typ argumentów metody i nie jest używana jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="18207-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="18207-111">`ByRef` Parametry nie mogą być kowariantny lub kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="18207-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="18207-112">Kowariancja i kontrawariancja są obsługiwane dla typów odwołań i nie jest obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="18207-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="18207-113">W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kontrawariantnego bez określania typu delegata.</span><span class="sxs-lookup"><span data-stu-id="18207-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="18207-114">Ponadto kontrawariantnego interfejsy nie mogą zagnieżdżać klas, wyliczeń lub struktur, ale mogą być zagnieżdżone interfejsów.</span><span class="sxs-lookup"><span data-stu-id="18207-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="18207-115">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="18207-115">Behavior</span></span>  
 <span data-ttu-id="18207-116">Interfejs, który ma kontrawariantnego parametru typu umożliwia jego metod przyjmowały argumenty mniej pochodne typy niż określony przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="18207-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="18207-117">Na przykład ponieważ w programie .NET Framework 4 w <xref:System.Collections.Generic.IComparer%601> interfejsu typu T jest kontrawariantny, można przypisać obiektu `IComparer(Of Person)` typ obiektu `IComparer(Of Employee)` typu bez przy użyciu dowolnej metody konwersji specjalne, jeśli `Person` dziedziczy `Employee`.</span><span class="sxs-lookup"><span data-stu-id="18207-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="18207-118">Kontrawariantnego delegata można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="18207-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18207-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="18207-119">Example</span></span>  
 <span data-ttu-id="18207-120">Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="18207-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="18207-121">Pokazuje również, jak można użyć niejawna konwersja dla klas, które implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="18207-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="18207-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="18207-122">Example</span></span>  
 <span data-ttu-id="18207-123">Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania to delegat generyczny kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="18207-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="18207-124">Pokazuje również, jak można niejawnie przekonwertować typu delegata.</span><span class="sxs-lookup"><span data-stu-id="18207-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="18207-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18207-125">See also</span></span>

- [<span data-ttu-id="18207-126">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="18207-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="18207-127">limit</span><span class="sxs-lookup"><span data-stu-id="18207-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
