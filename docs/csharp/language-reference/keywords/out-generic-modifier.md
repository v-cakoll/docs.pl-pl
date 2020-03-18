---
title: out — słowo kluczowe (modyfikator ogólny) — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713289"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="bcbba-102">out (ogólny modyfikator) (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="bcbba-102">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="bcbba-103">W przypadku parametrów typu `out` ogólnego słowo kluczowe określa, że parametr type jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="bcbba-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="bcbba-104">Słowa kluczowego `out` można użyć w ogólnych interfejsów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="bcbba-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="bcbba-105">Kowariancja umożliwia użycie typu bardziej pochodnego niż określony przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="bcbba-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="bcbba-106">Pozwala to na niejawną konwersję klas, które implementują interfejsy kowariantne i niejawną konwersję typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="bcbba-106">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="bcbba-107">Kowariancja i contravariance są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="bcbba-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="bcbba-108">Interfejs, który ma parametr typu kowariantnego umożliwia jego metody, aby zwrócić więcej typów pochodnych niż określone przez parametr typu.</span><span class="sxs-lookup"><span data-stu-id="bcbba-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="bcbba-109">Na przykład, ponieważ w .NET <xref:System.Collections.Generic.IEnumerable%601>Framework 4 w typie T jest kowariantny, można przypisać obiekt `IEnumerable(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez użycia żadnych specjalnych metod konwersji.</span><span class="sxs-lookup"><span data-stu-id="bcbba-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="bcbba-110">Współwariantdelegata można przypisać innego delegata tego samego typu, ale z bardziej pochodnym parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="bcbba-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="bcbba-111">Aby uzyskać więcej informacji, zobacz [Kowariancja i wariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="bcbba-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="bcbba-112">Przykład — kowariantny interfejs ogólny</span><span class="sxs-lookup"><span data-stu-id="bcbba-112">Example - covariant generic interface</span></span>

<span data-ttu-id="bcbba-113">W poniższym przykładzie pokazano, jak zadeklarować, rozszerzyć i zaimplementować kowariantny interfejs ogólny.</span><span class="sxs-lookup"><span data-stu-id="bcbba-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="bcbba-114">Pokazuje również, jak używać niejawnej konwersji dla klas, które implementują interfejs kowariantny.</span><span class="sxs-lookup"><span data-stu-id="bcbba-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="bcbba-115">W interfejsie ogólnym parametr typu można zadeklarować jako kowariantny, jeśli spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="bcbba-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="bcbba-116">Parametr type jest używany tylko jako zwracany typ metod interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="bcbba-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bcbba-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="bcbba-117">There is one exception to this rule.</span></span> <span data-ttu-id="bcbba-118">Jeśli w interfejsie kowariantykowym masz kontrataki ogólnedelegatjako parametr metody, można użyć typu kowariantowego jako parametru typu ogólnego dla tego delegata.</span><span class="sxs-lookup"><span data-stu-id="bcbba-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="bcbba-119">Aby uzyskać więcej informacji na temat kowariantyicznych i przeciwwariantowych delegatów ogólnych, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Używanie wariancji dla delegatów metodycznych akcji i akcji.](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="bcbba-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="bcbba-120">Parametr type nie jest używany jako ograniczenie ogólne dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bcbba-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="bcbba-121">Przykład — współwariantowy delegat ogólny</span><span class="sxs-lookup"><span data-stu-id="bcbba-121">Example - covariant generic delegate</span></span>

<span data-ttu-id="bcbba-122">W poniższym przykładzie pokazano, jak zadeklarować, utworzyć wystąpienia i wywołać kowariantycznego delegata ogólnego.</span><span class="sxs-lookup"><span data-stu-id="bcbba-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="bcbba-123">Pokazuje również, jak niejawnie konwertować typy delegatów.</span><span class="sxs-lookup"><span data-stu-id="bcbba-123">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="bcbba-124">W delegacie rodzajowym typ można zadeklarować jako kowarianty, jeśli jest używany tylko jako typ zwracany metody i nie jest używany dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="bcbba-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bcbba-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bcbba-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bcbba-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bcbba-126">See also</span></span>

- [<span data-ttu-id="bcbba-127">Wariancje w interfejsach ogólnych</span><span class="sxs-lookup"><span data-stu-id="bcbba-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="bcbba-128">Cala</span><span class="sxs-lookup"><span data-stu-id="bcbba-128">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="bcbba-129">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="bcbba-129">Modifiers</span></span>](index.md)
