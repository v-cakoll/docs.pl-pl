---
title: Out (modyfikator ogólny) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: fa14e83af16cd30a72ca1c165596fa9320842fce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053928"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="7ac93-102">Out (modyfikator ogólny) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ac93-102">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="7ac93-103">Dla parametrów typu genetycznego `Out` — słowo kluczowe Określa, że typ jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="7ac93-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ac93-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ac93-104">Remarks</span></span>

<span data-ttu-id="7ac93-105">Kowariancja umożliwia użycie typu bardziej pochodnego niż określona przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="7ac93-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="7ac93-106">Umożliwia to niejawna konwersja klasy, które implementują interfejsów typu variant i niejawnej konwersji typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="7ac93-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="7ac93-107">Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ac93-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="7ac93-108">reguły</span><span class="sxs-lookup"><span data-stu-id="7ac93-108">Rules</span></span>

<span data-ttu-id="7ac93-109">Możesz użyć `Out` — słowo kluczowe w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="7ac93-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="7ac93-110">W interfejsie ogólnego parametr typu mogą być deklarowane jako kowariantny, jeśli spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="7ac93-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="7ac93-111">Parametr typu jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="7ac93-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ac93-112">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="7ac93-112">There is one exception to this rule.</span></span> <span data-ttu-id="7ac93-113">Jeśli w interfejsie kowariantne Delegat ogólny kontrawariantny, jako parametru metody, można użyć kowariantnego typu co parametr typu ogólnego, dla tego delegata.</span><span class="sxs-lookup"><span data-stu-id="7ac93-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="7ac93-114">Aby uzyskać więcej informacji na temat kowariantne i kontrawariantne delegatów ogólnych, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych Func i](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7ac93-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="7ac93-115">Parametr typu nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7ac93-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="7ac93-116">Delegat ogólny parametr typu mogą być deklarowane kowariantne Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="7ac93-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="7ac93-117">Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="7ac93-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="7ac93-118">W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kowariantne bez określania typu delegata.</span><span class="sxs-lookup"><span data-stu-id="7ac93-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="7ac93-119">Ponadto kowariantne interfejsy nie mogą zagnieżdżać klas, wyliczeń lub struktur, ale mogą być zagnieżdżone interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7ac93-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="7ac93-120">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="7ac93-120">Behavior</span></span>

<span data-ttu-id="7ac93-121">Interfejs, który ma kowariantnego parametru typu umożliwia jego metod zwrócić więcej typów pochodnych niż określony przez parametr typu.</span><span class="sxs-lookup"><span data-stu-id="7ac93-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="7ac93-122">Na przykład ponieważ w programie .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerable(Of String)` typ obiektu `IEnumerable(Of Object)` typu bez przy użyciu dowolnej metody konwersji specjalne.</span><span class="sxs-lookup"><span data-stu-id="7ac93-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="7ac93-123">Kowariantne delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7ac93-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="7ac93-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ac93-124">Example</span></span>

<span data-ttu-id="7ac93-125">Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kowariantny.</span><span class="sxs-lookup"><span data-stu-id="7ac93-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="7ac93-126">Pokazano również, jak używać niejawna konwersja dla klas, które implementują interfejs kowariantny.</span><span class="sxs-lookup"><span data-stu-id="7ac93-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="7ac93-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ac93-127">Example</span></span>

<span data-ttu-id="7ac93-128">Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania kowariantne Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="7ac93-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="7ac93-129">Pokazuje również, jak można użyć niejawnej konwersji na typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="7ac93-129">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="7ac93-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ac93-130">See also</span></span>

- [<span data-ttu-id="7ac93-131">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="7ac93-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="7ac93-132">W</span><span class="sxs-lookup"><span data-stu-id="7ac93-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
