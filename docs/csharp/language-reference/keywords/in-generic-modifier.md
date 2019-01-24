---
title: in (modyfikator ogólny) - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: f736540a37d3226bccfc07749dcf06ca018663e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694574"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="a08b2-102">in (modyfikator ogólny) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a08b2-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="a08b2-103">Dla parametrów typu genetycznego `in` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="a08b2-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="a08b2-104">Możesz użyć `in` — słowo kluczowe w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="a08b2-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="a08b2-105">Kontrawariancja umożliwia używania typu mniej pochodnego niż określona przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="a08b2-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="a08b2-106">Dzięki temu niejawnej konwersji klas, które implementują interfejsy kontrawariantnego i niejawnej konwersji typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="a08b2-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="a08b2-107">Kowariancji i kontrawariancji w parametrach typu ogólnego są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="a08b2-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="a08b2-108">Typ może być zadeklarowana kontrawariantnego w ogólny interfejs lub delegat tylko wtedy, gdy definiuje typ parametrów metody, a nie typ zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="a08b2-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="a08b2-109">`In`, `ref`, i `out` parametry muszą być niezmiennej, co oznacza, są one ani kowariantny lub kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="a08b2-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="a08b2-110">Interfejs, który ma kontrawariantnego parametru typu umożliwia jego metod przyjmowały argumenty mniej pochodne typy niż określony przez parametr typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a08b2-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="a08b2-111">Na przykład w <xref:System.Collections.Generic.IComparer%601> interfejsu typu T jest kontrawariantny, można przypisać obiektu `IComparer<Person>` typ obiektu `IComparer<Employee>` typu bez przy użyciu dowolnej metody konwersji specjalne, jeśli `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="a08b2-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="a08b2-112">Kontrawariantnego delegata można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a08b2-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="a08b2-113">Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="a08b2-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="a08b2-114">Kontrawariantnego interfejs ogólny</span><span class="sxs-lookup"><span data-stu-id="a08b2-114">Contravariant generic interface</span></span>

<span data-ttu-id="a08b2-115">Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="a08b2-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="a08b2-116">Pokazuje również, jak można użyć niejawna konwersja dla klas, które implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="a08b2-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="a08b2-117">Delegat ogólny kontrawariantnego</span><span class="sxs-lookup"><span data-stu-id="a08b2-117">Contravariant generic delegate</span></span>

<span data-ttu-id="a08b2-118">Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania to delegat generyczny kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="a08b2-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="a08b2-119">Pokazuje również, jak można niejawnie przekonwertować typu delegata.</span><span class="sxs-lookup"><span data-stu-id="a08b2-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="a08b2-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a08b2-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a08b2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a08b2-121">See also</span></span>

- [<span data-ttu-id="a08b2-122">out</span><span class="sxs-lookup"><span data-stu-id="a08b2-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="a08b2-123">Kowariancja i kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="a08b2-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="a08b2-124">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="a08b2-124">Modifiers</span></span>](modifiers.md)
