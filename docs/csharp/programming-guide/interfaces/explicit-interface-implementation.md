---
title: Implementacja interfejsu jawnego — przewodnik programowania języka C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167676"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="1c360-102">Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1c360-102">Explicit Interface Implementation (C# Programming Guide)</span></span>

<span data-ttu-id="1c360-103">Jeśli [klasa](../../language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski z tym samym podpisem, a następnie implementacji tego elementu członkowskiego w klasie spowoduje, że oba interfejsy do użycia tego elementu członkowskiego jako ich implementacji.</span><span class="sxs-lookup"><span data-stu-id="1c360-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="1c360-104">W poniższym przykładzie wszystkie `Paint` wywołania tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="1c360-104">In the following example, all the calls to `Paint` invoke the same method.</span></span> <span data-ttu-id="1c360-105">Ten pierwszy przykład definiuje typy:</span><span class="sxs-lookup"><span data-stu-id="1c360-105">This first sample defines the types:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

<span data-ttu-id="1c360-106">Poniższy przykład wywołuje metody:</span><span class="sxs-lookup"><span data-stu-id="1c360-106">The following sample calls the methods:</span></span>

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

<span data-ttu-id="1c360-107">Gdy dwa elementy członkowskie interfejsu nie wykonują tej samej funkcji, prowadzi do niepoprawnej implementacji jednego lub obu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1c360-107">When two interface members don't perform the same function, it leads to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="1c360-108">Istnieje możliwość zaimplementowania elementu członkowskiego interfejsu jawnie — tworzenie elementu członkowskiego klasy, który jest wywoływany tylko za pośrednictwem interfejsu i jest specyficzne dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c360-108">It's possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="1c360-109">Nazwij element członkowski klasy nazwą interfejsu i kropką.</span><span class="sxs-lookup"><span data-stu-id="1c360-109">Name the class member with the name of the interface and a period.</span></span> <span data-ttu-id="1c360-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1c360-110">For example:</span></span>

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

<span data-ttu-id="1c360-111">Element `IControl.Paint` członkowski klasy `IControl` jest dostępny `ISurface.Paint` tylko za `ISurface`pośrednictwem interfejsu i jest dostępny tylko za pośrednictwem .</span><span class="sxs-lookup"><span data-stu-id="1c360-111">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="1c360-112">Obie implementacje metody są oddzielne i nie są dostępne bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="1c360-112">Both method implementations are separate, and neither are available directly on the class.</span></span> <span data-ttu-id="1c360-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1c360-113">For example:</span></span>

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

<span data-ttu-id="1c360-114">Implementacja jawna jest również używany do rozwiązywania przypadków, w których dwa interfejsy każdy deklarują różne elementy członkowskie o tej samej nazwie, takich jak właściwość i metoda.</span><span class="sxs-lookup"><span data-stu-id="1c360-114">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method.</span></span> <span data-ttu-id="1c360-115">Aby zaimplementować oba interfejsy, klasa musi używać `P`jawnej `P`implementacji dla właściwości lub metody lub obu, aby uniknąć błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1c360-115">To implement both interfaces, a class has to use explicit implementation either for the property `P`, or the method `P`, or both, to avoid a compiler error.</span></span> <span data-ttu-id="1c360-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1c360-116">For example:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

<span data-ttu-id="1c360-117">Począwszy od [języka C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), można zdefiniować implementację dla elementów członkowskich zadeklarowanych w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1c360-117">Beginning with [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), you can define an implementation for members declared in an interface.</span></span> <span data-ttu-id="1c360-118">Jeśli klasa dziedziczy implementacji metody z interfejsu, ta metoda jest dostępna tylko za pośrednictwem odwołania typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c360-118">If a class inherits a method implementation from an interface, that method is only accessible through a reference of the interface type.</span></span> <span data-ttu-id="1c360-119">Dziedziczony element członkowski nie jest wyświetlany jako część interfejsu publicznego.</span><span class="sxs-lookup"><span data-stu-id="1c360-119">The inherited member doesn't appear as part of the public interface.</span></span> <span data-ttu-id="1c360-120">Poniższy przykład definiuje domyślną implementację dla metody interfejsu:</span><span class="sxs-lookup"><span data-stu-id="1c360-120">The following sample defines a default implementation for an interface method:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

<span data-ttu-id="1c360-121">Poniższy przykład wywołuje domyślną implementację:</span><span class="sxs-lookup"><span data-stu-id="1c360-121">The following sample invokes the default implementation:</span></span>

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

<span data-ttu-id="1c360-122">Każda klasa, która `IControl` implementuje interfejs `Paint` można zastąpić metodę domyślną, jako metodę publiczną lub jako implementacja interfejsu jawnego.</span><span class="sxs-lookup"><span data-stu-id="1c360-122">Any class that implements the `IControl` interface can override the default `Paint` method, either as a public method, or as an explicit interface implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c360-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c360-123">See also</span></span>

- [<span data-ttu-id="1c360-124">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="1c360-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1c360-125">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="1c360-125">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="1c360-126">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1c360-126">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="1c360-127">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="1c360-127">Inheritance</span></span>](../classes-and-structs/inheritance.md)
