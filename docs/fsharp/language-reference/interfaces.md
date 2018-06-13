---
title: Interfejsy (F#)
description: 'Dowiedz się, jak F # interfejsy określić zestawy pokrewnych elementów członkowskich, które implementują innych klas.'
ms.date: 05/16/2016
ms.openlocfilehash: 54ae8a2840ce26814be25f08c3ed02e12df6b7c0
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058904"
---
# <a name="interfaces"></a><span data-ttu-id="4d508-103">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4d508-103">Interfaces</span></span>

<span data-ttu-id="4d508-104">*Interfejsy* określić zestawy pokrewnych elementów członkowskich, które implementują innych klas.</span><span class="sxs-lookup"><span data-stu-id="4d508-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d508-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d508-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="4d508-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d508-106">Remarks</span></span>
<span data-ttu-id="4d508-107">Deklaracji interfejsów przypominać deklaracji klasy, z wyjątkiem tego, czy nie elementy członkowskie są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="4d508-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="4d508-108">Zamiast tego, wszystkie elementy członkowskie są abstrakcyjnego, wskazywany przez słowo kluczowe `abstract`.</span><span class="sxs-lookup"><span data-stu-id="4d508-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="4d508-109">Dla metody abstrakcyjne nie podawaj treści metody.</span><span class="sxs-lookup"><span data-stu-id="4d508-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="4d508-110">Jednak udostępnia domyślną implementację dołączenie oddzielnych definicji elementu członkowskiego jako metoda razem z `default` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4d508-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="4d508-111">W ten sposób jest odpowiednikiem tworzenia wirtualnej metody w klasie podstawowej w innych językach .NET.</span><span class="sxs-lookup"><span data-stu-id="4d508-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="4d508-112">Metoda wirtualna może zostać przesłonięta klas implementujących interfejs.</span><span class="sxs-lookup"><span data-stu-id="4d508-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="4d508-113">Dostępność domyślne dla interfejsów jest `public`.</span><span class="sxs-lookup"><span data-stu-id="4d508-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="4d508-114">Każdy parametr metody można opcjonalnie nadaj nazwę przy użyciu normalnego F # składni:</span><span class="sxs-lookup"><span data-stu-id="4d508-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="4d508-115">W powyższych `ISprintable` przykład `Print` metoda ma jeden parametr typu `string` o nazwie `format`.</span><span class="sxs-lookup"><span data-stu-id="4d508-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="4d508-116">Istnieją dwa sposoby implementować interfejsów: przy użyciu wyrażeń obiektów i przy użyciu typu klasy.</span><span class="sxs-lookup"><span data-stu-id="4d508-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="4d508-117">W obu przypadkach wyrażenie typu lub obiekt klasy zawiera treść metody dla metody abstrakcyjne interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4d508-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="4d508-118">Implementacje są specyficzne dla każdego typu, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="4d508-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="4d508-119">W związku z tym metody interfejsu w różnych typów mogą się różnić od siebie.</span><span class="sxs-lookup"><span data-stu-id="4d508-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="4d508-120">Słowa kluczowe `interface` i `end`, którego oznaczenie początek i koniec definicji, są opcjonalne, gdy używasz lightweight — składnia.</span><span class="sxs-lookup"><span data-stu-id="4d508-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="4d508-121">Jeśli nie używasz słowa kluczowe, kompilator próbuje rozpoznać, czy typ jest klasą lub interfejsem, analizując konstrukcje, których używasz.</span><span class="sxs-lookup"><span data-stu-id="4d508-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="4d508-122">Jeśli zdefiniować elementu członkowskiego lub użyj składni inne klasy, typ jest interpretowana jako klasa.</span><span class="sxs-lookup"><span data-stu-id="4d508-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="4d508-123">Styl kodowania platformy .NET jest rozpoczęcie wszystkie interfejsy z wielką `I`.</span><span class="sxs-lookup"><span data-stu-id="4d508-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="4d508-124">Implementowanie interfejsów przy użyciu typu klasy</span><span class="sxs-lookup"><span data-stu-id="4d508-124">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="4d508-125">Można wdrożyć jeden lub więcej interfejsów w typie klasy przy użyciu `interface` — słowo kluczowe, nazwę interfejsu i `with` — słowo kluczowe, a następnie definicji elementu członkowskiego interfejsu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4d508-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="4d508-126">Implementacje interfejsu są dziedziczone, więc nie trzeba ich reimplement żadnych klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4d508-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="4d508-127">Wywołanie metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="4d508-127">Calling Interface Methods</span></span>
<span data-ttu-id="4d508-128">Metody interfejsu można wywołać tylko za pośrednictwem interfejsu, nie za pomocą dowolnego obiektu typu, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="4d508-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="4d508-129">W związku z tym może być konieczne rozszerzające typ interfejsu za pomocą `:>` operator lub `upcast` operatora w celu wywołania tych metod.</span><span class="sxs-lookup"><span data-stu-id="4d508-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="4d508-130">Aby wywołać metodę interfejsu, gdy obiekt typu `SomeClass`, należy najpierw rozszerzające obiektu na typ interfejsu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4d508-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="4d508-131">Alternatywą jest Zadeklaruj metodę dla obiektu z tym upcasts i wywołuje metodę interfejsu, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4d508-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="4d508-132">Implementowanie interfejsów przy użyciu wyrażeń obiektów</span><span class="sxs-lookup"><span data-stu-id="4d508-132">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="4d508-133">Wyrażenia obiektów podaj krótki sposób implementowania interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4d508-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="4d508-134">Są one przydatne, gdy jest konieczne tworzenie typu nazwanego, i chcesz obiekt, który obsługuje metod interfejsu, bez żadnych dodatkowych metod.</span><span class="sxs-lookup"><span data-stu-id="4d508-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="4d508-135">Poniższy kod przedstawia wyrażenie obiektu.</span><span class="sxs-lookup"><span data-stu-id="4d508-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="4d508-136">Dziedziczenie — interfejs</span><span class="sxs-lookup"><span data-stu-id="4d508-136">Interface Inheritance</span></span>
<span data-ttu-id="4d508-137">Interfejsy może dziedziczyć z jednego lub więcej interfejsach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="4d508-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="4d508-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d508-138">See Also</span></span>
[<span data-ttu-id="4d508-139">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="4d508-139">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4d508-140">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="4d508-140">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="4d508-141">Klasy</span><span class="sxs-lookup"><span data-stu-id="4d508-141">Classes</span></span>](classes.md)
