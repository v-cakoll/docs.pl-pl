---
title: w (Modyfikator ogólny) — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713486"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="32af8-102">in (modyfikator ogólny) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="32af8-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="32af8-103">W przypadku parametrów typu `in` ogólnego słowo kluczowe określa, że parametr type jest zmienny.</span><span class="sxs-lookup"><span data-stu-id="32af8-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="32af8-104">Słowa kluczowego `in` można użyć w ogólnych interfejsów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="32af8-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="32af8-105">Contravariance umożliwia użycie mniej pochodnego typu niż określony przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="32af8-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="32af8-106">Pozwala to na niejawną konwersję klas, które implementują interfejsy kontrawariantne i niejawną konwersję typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="32af8-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="32af8-107">Kowariancja i kontrawariancji w parametrach typu ogólnego są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="32af8-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="32af8-108">Typ można zadeklarować kontrawarianty w interfejsie ogólnym lub delegować tylko wtedy, gdy definiuje typ parametrów metody, a nie typu zwracanego metody.</span><span class="sxs-lookup"><span data-stu-id="32af8-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="32af8-109">`In`, `ref`a `out` parametry muszą być niezmienne, co oznacza, że nie są ani kowariantne, ani kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="32af8-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="32af8-110">Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody do akceptowania argumentów mniej pochodnych typów niż te określone przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="32af8-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="32af8-111">Na przykład w <xref:System.Collections.Generic.IComparer%601> interfejsie typ T jest kontrawariantny, można `IComparer<Person>` przypisać obiekt typu `IComparer<Employee>` do obiektu typu bez użycia `Employee` specjalnych `Person`metod konwersji, jeśli dziedziczy .</span><span class="sxs-lookup"><span data-stu-id="32af8-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="32af8-112">Kontrataki można przypisać innego delegata tego samego typu, ale z mniej pochodnym parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="32af8-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="32af8-113">Aby uzyskać więcej informacji, zobacz [Kowariancja i wariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="32af8-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="32af8-114">Przeciwwariantny interfejs ogólny</span><span class="sxs-lookup"><span data-stu-id="32af8-114">Contravariant generic interface</span></span>

<span data-ttu-id="32af8-115">W poniższym przykładzie pokazano, jak zadeklarować, rozszerzyć i zaimplementować interfejs ogólny.</span><span class="sxs-lookup"><span data-stu-id="32af8-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="32af8-116">Pokazuje również, jak można użyć niejawnej konwersji dla klas, które implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="32af8-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="32af8-117">Kontrataki generyczny delegat</span><span class="sxs-lookup"><span data-stu-id="32af8-117">Contravariant generic delegate</span></span>

<span data-ttu-id="32af8-118">W poniższym przykładzie pokazano, jak zadeklarować, utworzyć wystąpienia i wywołać kontratak ogólnedelegata.</span><span class="sxs-lookup"><span data-stu-id="32af8-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="32af8-119">Pokazuje również, jak można niejawnie konwertować typ delegata.</span><span class="sxs-lookup"><span data-stu-id="32af8-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="32af8-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="32af8-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="32af8-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32af8-121">See also</span></span>

- [<span data-ttu-id="32af8-122">na zewnątrz</span><span class="sxs-lookup"><span data-stu-id="32af8-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="32af8-123">Kowariancja i kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="32af8-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="32af8-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="32af8-124">Modifiers</span></span>](index.md)
