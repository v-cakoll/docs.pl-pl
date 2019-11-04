---
title: in (modyfikator ogólny) — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 0806169b9b1c3521dcf89f5ea0fa5aec188030c2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422771"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="23545-102">in (modyfikator ogólny) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="23545-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="23545-103">W przypadku parametrów typu ogólnego `in` słowo kluczowe Określa, że parametr typu jest kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="23545-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="23545-104">Możesz użyć słowa kluczowego `in` w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="23545-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="23545-105">Kontrawariancja umożliwia użycie mniej pochodnego typu niż określony przez parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="23545-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="23545-106">Pozwala to na niejawną konwersję klas, które implementują interfejsy kontrawariantne i niejawną konwersję typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="23545-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="23545-107">W przypadku typów referencyjnych są obsługiwane Kowariancja i kontrawariancja w parametrach typu ogólnego, ale nie są one obsługiwane w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="23545-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="23545-108">Typ może być zadeklarowany jako kontrawariantne w ogólnym interfejsie lub delegatze tylko wtedy, gdy definiuje typ parametrów metody, a nie typ zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="23545-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="23545-109">parametry `In`, `ref`i `out` muszą być niezmienne, co oznacza, że nie są one ani współvariant ani kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="23545-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="23545-110">Interfejs, który ma parametr typu kontrawariantne, umożliwia jej metodom akceptowanie argumentów o mniejszych typach pochodnych niż te określone przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="23545-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="23545-111">Na przykład, w interfejsie <xref:System.Collections.Generic.IComparer%601>, wpisz T to kontrawariantne, można przypisać obiekt typu `IComparer<Person>` do obiektu typu `IComparer<Employee>` bez użycia żadnych specjalnych metod konwersji, jeśli `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="23545-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="23545-112">Delegatowi kontrawariantne można przypisać inny delegat tego samego typu, ale przy użyciu mniej pochodnego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="23545-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="23545-113">Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="23545-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="23545-114">Kontrawariantne — interfejs ogólny</span><span class="sxs-lookup"><span data-stu-id="23545-114">Contravariant generic interface</span></span>

<span data-ttu-id="23545-115">Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="23545-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="23545-116">Pokazano również, jak można użyć niejawnej konwersji dla klas implementujących ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="23545-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="23545-117">Delegat ogólny kontrawariantne</span><span class="sxs-lookup"><span data-stu-id="23545-117">Contravariant generic delegate</span></span>

<span data-ttu-id="23545-118">Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata generycznego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="23545-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="23545-119">Pokazuje również, jak można niejawnie skonwertować typ delegata.</span><span class="sxs-lookup"><span data-stu-id="23545-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="23545-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="23545-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="23545-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23545-121">See also</span></span>

- [<span data-ttu-id="23545-122">out</span><span class="sxs-lookup"><span data-stu-id="23545-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="23545-123">Kowariancja i kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="23545-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="23545-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="23545-124">Modifiers</span></span>](index.md)
