---
title: In (modyfikator ogólny) — Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004870"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="90968-102">In (modyfikator ogólny) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90968-102">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="90968-103">W przypadku parametrów typu ogólnego słowo kluczowe `In` Określa, że parametr typu jest kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="90968-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="90968-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90968-104">Remarks</span></span>

<span data-ttu-id="90968-105">Kontrawariancja umożliwia użycie mniej pochodnego typu niż określony przez parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="90968-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="90968-106">Pozwala to na niejawną konwersję klas, które implementują interfejsy wariantów i niejawną konwersję typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="90968-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="90968-107">Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="90968-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="90968-108">Przepisy</span><span class="sxs-lookup"><span data-stu-id="90968-108">Rules</span></span>

<span data-ttu-id="90968-109">Możesz użyć słowa kluczowego `In` w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="90968-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="90968-110">Parametr typu może być zadeklarowany jako kontrawariantne w interfejsie generycznym lub delegatze, jeśli jest używany tylko jako typ argumentów metody i nie jest używany jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="90968-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="90968-111">parametry `ByRef` nie mogą być typu współvariant ani kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="90968-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="90968-112">Kowariancja i kontrawariancja są obsługiwane dla typów referencyjnych i nie są obsługiwane w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="90968-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="90968-113">W Visual Basic nie można zadeklarować zdarzeń w interfejsach kontrawariantne bez określania typu delegata.</span><span class="sxs-lookup"><span data-stu-id="90968-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="90968-114">Interfejsy kontrawariantne nie mogą również zawierać klas zagnieżdżonych, wyliczeniowych ani struktur, ale mogą mieć zagnieżdżone interfejsy.</span><span class="sxs-lookup"><span data-stu-id="90968-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="90968-115">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="90968-115">Behavior</span></span>

<span data-ttu-id="90968-116">Interfejs, który ma parametr typu kontrawariantne, umożliwia jej metodom akceptowanie argumentów o mniejszych typach pochodnych niż te określone przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="90968-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="90968-117">Na przykład, ponieważ w .NET Framework 4, w interfejsie <xref:System.Collections.Generic.IComparer%601> typ T to kontrawariantne, można przypisać obiekt typu `IComparer(Of Person)` do obiektu typu `IComparer(Of Employee)` bez użycia żadnych specjalnych metod konwersji, jeśli `Employee` dziedziczy po `Person`.</span><span class="sxs-lookup"><span data-stu-id="90968-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="90968-118">Delegatowi kontrawariantne można przypisać inny delegat tego samego typu, ale przy użyciu mniej pochodnego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="90968-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="90968-119">Przykład — kontrawariantne Generic Interface</span><span class="sxs-lookup"><span data-stu-id="90968-119">Example - contravariant generic interface</span></span>

<span data-ttu-id="90968-120">Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="90968-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="90968-121">Pokazano również, jak można użyć niejawnej konwersji dla klas implementujących ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="90968-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="90968-122">Przykład — Delegat ogólny kontrawariantne</span><span class="sxs-lookup"><span data-stu-id="90968-122">Example - contravariant generic delegate</span></span>

<span data-ttu-id="90968-123">Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata generycznego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="90968-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="90968-124">Pokazuje również, jak można niejawnie skonwertować typ delegata.</span><span class="sxs-lookup"><span data-stu-id="90968-124">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="90968-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90968-125">See also</span></span>

- [<span data-ttu-id="90968-126">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="90968-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="90968-127">Określoną</span><span class="sxs-lookup"><span data-stu-id="90968-127">Out</span></span>](out-generic-modifier.md)
