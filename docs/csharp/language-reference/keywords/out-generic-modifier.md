---
title: out — słowo kluczowe (modyfikator ogólny C# ) — odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713289"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="d107d-102">out (modyfikator ogólny) (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="d107d-102">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="d107d-103">W przypadku parametrów typu ogólnego `out` słowo kluczowe Określa, że parametr typu jest współwariantem.</span><span class="sxs-lookup"><span data-stu-id="d107d-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="d107d-104">Możesz użyć słowa kluczowego `out` w interfejsach ogólnych i delegatach.</span><span class="sxs-lookup"><span data-stu-id="d107d-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="d107d-105">Kowariancja umożliwia użycie bardziej pochodnego typu niż określony przez parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="d107d-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="d107d-106">Pozwala to na niejawną konwersję klas, które implementują interfejsy współwariantu i niejawną konwersję typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="d107d-106">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="d107d-107">Dla typów referencyjnych są obsługiwane Kowariancja i kontrawariancja, ale nie są one obsługiwane w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="d107d-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="d107d-108">Interfejs, który ma parametr typu klasy współdzielonej, umożliwia jej metodom zwrócenie większej liczby typów pochodnych niż te określone przez parametr typu.</span><span class="sxs-lookup"><span data-stu-id="d107d-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="d107d-109">Na przykład, ponieważ w .NET Framework 4, w <xref:System.Collections.Generic.IEnumerable%601>, typu T jest współwariantem, można przypisać obiekt typu `IEnumerable(Of String)` do obiektu typu `IEnumerable(Of Object)` bez użycia żadnych specjalnych metod konwersji.</span><span class="sxs-lookup"><span data-stu-id="d107d-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="d107d-110">Delegata, do którego można przypisać inny delegat tego samego typu, ale z bardziej pochodnym parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d107d-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="d107d-111">Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="d107d-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="d107d-112">Przykład — interfejs ogólny typu "-Variant"</span><span class="sxs-lookup"><span data-stu-id="d107d-112">Example - covariant generic interface</span></span>

<span data-ttu-id="d107d-113">Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny typu "współvariant".</span><span class="sxs-lookup"><span data-stu-id="d107d-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="d107d-114">Przedstawiono w nim również sposób użycia niejawnej konwersji dla klas, które implementują interfejs współvariant.</span><span class="sxs-lookup"><span data-stu-id="d107d-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="d107d-115">W interfejsie ogólnym parametr typu może być zadeklarowany jako współwariant, jeśli spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="d107d-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="d107d-116">Parametr typu jest używany tylko jako typ zwracany metod interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="d107d-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d107d-117">Istnieje jeden wyjątek dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="d107d-117">There is one exception to this rule.</span></span> <span data-ttu-id="d107d-118">Jeśli w interfejsie o niezmiennym jest kontrawariantne delegat generyczny jako parametr metody, można użyć typu współwariantu jako parametru typu ogólnego dla tego delegata.</span><span class="sxs-lookup"><span data-stu-id="d107d-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="d107d-119">Aby uzyskać więcej informacji na temat elementów delegowanych i kontrawariantne ogólnych, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Używanie wariancji dla delegatów typu Func i akcja](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d107d-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="d107d-120">Parametr typu nie jest używany jako ograniczenie ogólne metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d107d-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="d107d-121">Przykład — delegat generyczny ogólny</span><span class="sxs-lookup"><span data-stu-id="d107d-121">Example - covariant generic delegate</span></span>

<span data-ttu-id="d107d-122">Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata ogólnego typu.</span><span class="sxs-lookup"><span data-stu-id="d107d-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="d107d-123">Pokazuje również, jak niejawnie skonwertować typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="d107d-123">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="d107d-124">W delegatze ogólnym typ może być zadeklarowany jako współwariant, jeśli jest używany tylko jako zwracany typ metody i nie jest używany dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="d107d-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d107d-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d107d-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d107d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d107d-126">See also</span></span>

- [<span data-ttu-id="d107d-127">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="d107d-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="d107d-128">in</span><span class="sxs-lookup"><span data-stu-id="d107d-128">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="d107d-129">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="d107d-129">Modifiers</span></span>](index.md)
