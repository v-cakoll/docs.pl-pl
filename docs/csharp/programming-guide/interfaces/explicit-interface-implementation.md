---
title: Implementacja interfejsu jawnego C# — Przewodnik programowania
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628153"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="4b7b2-102">Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4b7b2-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="4b7b2-103">Jeśli [Klasa](../../language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski o tym samym podpisie, a następnie wdrożenie tego elementu członkowskiego w klasie spowoduje, że oba interfejsy używają tego elementu członkowskiego jako ich implementacji.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="4b7b2-104">W poniższym przykładzie wszystkie wywołania do `Paint` wywołują tę samą metodę.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="4b7b2-105">Ten pierwszy przykład definiuje typy:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="4b7b2-106">Poniższy przykład wywołuje metody:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="4b7b2-107">Gdy dwa elementy członkowskie interfejsu nie wykonują tej samej funkcji, prowadzi do niepoprawnej implementacji jednego lub obu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="4b7b2-108">Istnieje możliwość jawnej implementacji elementu członkowskiego interfejsu — tworzenie składowej klasy, która jest wywoływana tylko przez interfejs i jest specyficzna dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="4b7b2-109">Nazwij element członkowski klasy przy użyciu nazwy interfejsu i kropki.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="4b7b2-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="4b7b2-111">`IControl.Paint` elementu członkowskiego klasy jest dostępna tylko za pomocą interfejsu `IControl`, a `ISurface.Paint` jest dostępny tylko za pomocą `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="4b7b2-112">Obie implementacje metod są oddzielne i nie są dostępne bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="4b7b2-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="4b7b2-114">Jawna implementacja służy również do rozwiązywania przypadków, gdy dwa interfejsy deklarują różne elementy członkowskie o tej samej nazwie, takie jak właściwość i metoda.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="4b7b2-115">Aby zaimplementować oba interfejsy, Klasa musi używać jawnej implementacji dla właściwości `P`lub metody `P`lub obu, aby uniknąć błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="4b7b2-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="4b7b2-117">Jeśli klasa dziedziczy implementację metody z interfejsu, ta metoda jest dostępna tylko za pośrednictwem typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-117">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="4b7b2-118">Dziedziczony element członkowski nie jest wyświetlany jako część interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-118">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="4b7b2-119">Poniższy przykład definiuje domyślną implementację metody interfejsu:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-119">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="4b7b2-120">Poniższy przykład wywołuje domyślną implementację:</span><span class="sxs-lookup"><span data-stu-id="4b7b2-120">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="4b7b2-121">Każda klasa implementująca interfejs `IControl` może przesłonić domyślną metodę `Paint`, jako metodę publiczną lub jako jawną implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4b7b2-121">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b7b2-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b7b2-122">See also</span></span>

- [<span data-ttu-id="4b7b2-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4b7b2-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4b7b2-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="4b7b2-124">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="4b7b2-125">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4b7b2-125">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="4b7b2-126">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="4b7b2-126">Inheritance</span></span>](../classes-and-structs/inheritance.md)
