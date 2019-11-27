---
title: Out (modyfikator ogólny)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 0460015b44971fa638dba47183690ffcc89ca55f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351424"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="f8e63-102">Out (modyfikator ogólny) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8e63-102">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="f8e63-103">W przypadku parametrów typu ogólnego `Out` słowo kluczowe Określa, że typ jest współvariant.</span><span class="sxs-lookup"><span data-stu-id="f8e63-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8e63-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8e63-104">Remarks</span></span>

<span data-ttu-id="f8e63-105">Kowariancja umożliwia użycie bardziej pochodnego typu niż określony przez parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="f8e63-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="f8e63-106">Pozwala to na niejawną konwersję klas, które implementują interfejsy wariantów i niejawną konwersję typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="f8e63-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="f8e63-107">Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8e63-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="f8e63-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="f8e63-108">Rules</span></span>

<span data-ttu-id="f8e63-109">Możesz użyć słowa kluczowego `Out` w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="f8e63-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="f8e63-110">W interfejsie ogólnym parametr typu może być zadeklarowany jako współwariant, jeśli spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="f8e63-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="f8e63-111">Parametr typu jest używany tylko jako typ zwracany metod interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="f8e63-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f8e63-112">Istnieje jeden wyjątek dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="f8e63-112">There is one exception to this rule.</span></span> <span data-ttu-id="f8e63-113">Jeśli w interfejsie o niezmiennym jest kontrawariantne delegat generyczny jako parametr metody, można użyć typu współwariantu jako parametru typu ogólnego dla tego delegata.</span><span class="sxs-lookup"><span data-stu-id="f8e63-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="f8e63-114">Aby uzyskać więcej informacji na temat elementów delegowanych i kontrawariantne ogólnych, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Używanie wariancji dla delegatów typu Func i akcja](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f8e63-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="f8e63-115">Parametr typu nie jest używany jako ograniczenie ogólne metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f8e63-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="f8e63-116">W delegatze ogólnym parametr typu może być zadeklarowany jako współvariant, jeśli jest używany tylko jako zwracany typ metody i nie jest używany dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="f8e63-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="f8e63-117">Dla typów referencyjnych są obsługiwane Kowariancja i kontrawariancja, ale nie są one obsługiwane w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="f8e63-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="f8e63-118">W Visual Basic nie można zadeklarować zdarzeń w interfejsach współvariant bez określania typu delegata.</span><span class="sxs-lookup"><span data-stu-id="f8e63-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="f8e63-119">Ponadto interfejsy współwariantowe nie mogą mieć klas zagnieżdżonych, wyliczeniowych ani struktur, ale mogą mieć zagnieżdżone interfejsy.</span><span class="sxs-lookup"><span data-stu-id="f8e63-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="f8e63-120">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="f8e63-120">Behavior</span></span>

<span data-ttu-id="f8e63-121">Interfejs, który ma parametr typu klasy współdzielonej, umożliwia jej metodom zwrócenie większej liczby typów pochodnych niż te określone przez parametr typu.</span><span class="sxs-lookup"><span data-stu-id="f8e63-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="f8e63-122">Na przykład, ponieważ w .NET Framework 4, w <xref:System.Collections.Generic.IEnumerable%601>, typu T jest współwariantem, można przypisać obiekt typu `IEnumerable(Of String)` do obiektu typu `IEnumerable(Of Object)` bez użycia żadnych specjalnych metod konwersji.</span><span class="sxs-lookup"><span data-stu-id="f8e63-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="f8e63-123">Delegata, do którego można przypisać inny delegat tego samego typu, ale z bardziej pochodnym parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f8e63-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="f8e63-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8e63-124">Example</span></span>

<span data-ttu-id="f8e63-125">Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny typu "współvariant".</span><span class="sxs-lookup"><span data-stu-id="f8e63-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="f8e63-126">Przedstawiono w nim również sposób użycia niejawnej konwersji dla klas, które implementują interfejs współvariant.</span><span class="sxs-lookup"><span data-stu-id="f8e63-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="f8e63-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8e63-127">Example</span></span>

<span data-ttu-id="f8e63-128">Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata ogólnego typu.</span><span class="sxs-lookup"><span data-stu-id="f8e63-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="f8e63-129">Pokazano również, jak można użyć niejawnej konwersji typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="f8e63-129">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="f8e63-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8e63-130">See also</span></span>

- [<span data-ttu-id="f8e63-131">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="f8e63-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="f8e63-132">Podczas</span><span class="sxs-lookup"><span data-stu-id="f8e63-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
