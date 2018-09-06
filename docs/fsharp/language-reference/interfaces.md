---
title: Interfejsy (F#)
description: 'Dowiedz się, jak interfejsy F # określić zestawy powiązane elementy członkowskie, które implementują innych klas.'
ms.date: 05/16/2016
ms.openlocfilehash: 6d7f8ee9ea17d2294933f88577c30a96975ae5d4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802823"
---
# <a name="interfaces"></a><span data-ttu-id="38e26-103">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="38e26-103">Interfaces</span></span>

<span data-ttu-id="38e26-104">*Interfejsy* określić zestawy pokrewnych elementów członkowskich, które implementują innych klas.</span><span class="sxs-lookup"><span data-stu-id="38e26-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="38e26-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="38e26-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="38e26-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38e26-106">Remarks</span></span>

<span data-ttu-id="38e26-107">Deklaracje interfejsu przypominają deklaracji klasy, z tą różnicą, że żadne składowe są implementowane.</span><span class="sxs-lookup"><span data-stu-id="38e26-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="38e26-108">Zamiast tego wszystkie elementy członkowskie są abstrakcyjne, wskazane przez słowo kluczowe `abstract`.</span><span class="sxs-lookup"><span data-stu-id="38e26-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="38e26-109">Nie udostępniają treści metody metody abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="38e26-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="38e26-110">Jednak udostępnia domyślną implementację, umieszczając również oddzielne definicji elementu członkowskiego jako metoda wraz z `default` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="38e26-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="38e26-111">To jest odpowiednikiem tworzenie wirtualnej metody w klasie bazowej, w innych językach .NET.</span><span class="sxs-lookup"><span data-stu-id="38e26-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="38e26-112">Metoda wirtualna może być zastąpiona w klasach, które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="38e26-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="38e26-113">Wartość domyślna dostępu dla interfejsów `public`.</span><span class="sxs-lookup"><span data-stu-id="38e26-113">The default accessibility for interfaces is `public`.</span></span>

<span data-ttu-id="38e26-114">Każdy parametr metody można opcjonalnie nadać nazwę przy użyciu normalnego języka F # składni:</span><span class="sxs-lookup"><span data-stu-id="38e26-114">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="38e26-115">W powyższych `ISprintable` przykład `Print` metoda ma jeden parametr typu `string` o nazwie `format`.</span><span class="sxs-lookup"><span data-stu-id="38e26-115">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="38e26-116">Istnieją dwa sposoby, aby zaimplementować interfejsów: przy użyciu wyrażeń obiektów i za pomocą typu klasy.</span><span class="sxs-lookup"><span data-stu-id="38e26-116">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="38e26-117">W obu przypadkach wyrażenie typu lub obiektu klasy zawiera treści metod dla metody abstrakcyjne interfejsu.</span><span class="sxs-lookup"><span data-stu-id="38e26-117">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="38e26-118">Implementacje są właściwe dla każdego typu, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="38e26-118">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="38e26-119">W związku z tym metod interfejsu w różnych typach może się różnić od siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="38e26-119">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="38e26-120">Słowa kluczowe `interface` i `end`, które oznaczania początku i końca definicji, są opcjonalne, jeśli używasz składni lekkiej.</span><span class="sxs-lookup"><span data-stu-id="38e26-120">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="38e26-121">Jeśli nie używasz tych słów kluczowych, kompilator próbuje rozpoznać, czy typ jest klasą lub interfejs, analizując konstrukcje, których używasz.</span><span class="sxs-lookup"><span data-stu-id="38e26-121">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="38e26-122">Jeśli możesz definiować element członkowski lub inną składnię klasy, typ jest interpretowany jako klasa.</span><span class="sxs-lookup"><span data-stu-id="38e26-122">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="38e26-123">Styl kodowania platformy .NET jest rozpoczęcie wszystkie interfejsy z wielkiej litery `I`.</span><span class="sxs-lookup"><span data-stu-id="38e26-123">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>

## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="38e26-124">Implementacja interfejsów przy użyciu typów klas</span><span class="sxs-lookup"><span data-stu-id="38e26-124">Implementing Interfaces by Using Class Types</span></span>

<span data-ttu-id="38e26-125">Można wdrożyć jeden lub więcej interfejsów w typie klasy przy użyciu `interface` — słowo kluczowe, nazwy interfejsu, a `with` — słowo kluczowe, a następnie definicji składowej interfejsu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="38e26-125">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="38e26-126">Implementacje interfejsu są dziedziczone, dzięki czemu nie trzeba ich ponownie wszystkie klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="38e26-126">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>

## <a name="calling-interface-methods"></a><span data-ttu-id="38e26-127">Wywoływanie metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="38e26-127">Calling Interface Methods</span></span>

<span data-ttu-id="38e26-128">Metody interfejsu może być wywoływana tylko za pośrednictwem interfejsu, a nie przy użyciu dowolnego obiektu typu, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="38e26-128">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="38e26-129">W związku z tym, może być konieczne rozszerzające typ interfejsu za pomocą `:>` operatora lub `upcast` operatora w celu wywołania tych metod.</span><span class="sxs-lookup"><span data-stu-id="38e26-129">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="38e26-130">Aby wywołać metodę interfejsu, w przypadku obiektu o typie `SomeClass`, należy najpierw rozszerzające obiektu do typu interfejsu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="38e26-130">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="38e26-131">Alternatywą jest do deklarowania metody dla obiektu tego upcasts i wywołuje metodę interfejsu, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="38e26-131">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]

## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="38e26-132">Implementacja interfejsów przy użyciu wyrażeń obiektów</span><span class="sxs-lookup"><span data-stu-id="38e26-132">Implementing Interfaces by Using Object Expressions</span></span>

<span data-ttu-id="38e26-133">Wyrażenia obiektów umożliwiają krótki do implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="38e26-133">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="38e26-134">Są one przydatne, gdy nie trzeba tworzyć nazwany typ, a Ty chcesz po prostu obiekt, który obsługuje metody interfejsu, bez żadnych dodatkowych metod.</span><span class="sxs-lookup"><span data-stu-id="38e26-134">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="38e26-135">Wyrażenie obiektu to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="38e26-135">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]

## <a name="interface-inheritance"></a><span data-ttu-id="38e26-136">Dziedziczenia interfejsu</span><span class="sxs-lookup"><span data-stu-id="38e26-136">Interface Inheritance</span></span>

<span data-ttu-id="38e26-137">Interfejsy mogą dziedziczyć jeden lub więcej podstawowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="38e26-137">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]

## <a name="see-also"></a><span data-ttu-id="38e26-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38e26-138">See also</span></span>

- [<span data-ttu-id="38e26-139">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="38e26-139">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="38e26-140">Wyrażenia obiektów</span><span class="sxs-lookup"><span data-stu-id="38e26-140">Object Expressions</span></span>](object-expressions.md)
- [<span data-ttu-id="38e26-141">Klasy</span><span class="sxs-lookup"><span data-stu-id="38e26-141">Classes</span></span>](classes.md)
