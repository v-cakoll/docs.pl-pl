---
title: Delegaty (F#)
description: "Dowiedz się, jak pracować z delegatów w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="1ab4c-104">Delegaty</span><span class="sxs-lookup"><span data-stu-id="1ab4c-104">Delegates</span></span>

<span data-ttu-id="1ab4c-105">Delegat reprezentuje wywołanie funkcji jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-105">A delegate represents a function call as an object.</span></span> <span data-ttu-id="1ab4c-106">W języku F # zazwyczaj należy użyć wartości funkcji do reprezentowania funkcje jako wartości pierwszej klasy; jednak delegatów są używane w programie .NET Framework i dlatego są wymagane, gdy współdziałać z interfejsów API, który będzie je.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-106">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="1ab4c-107">Może również być używane tworzenia bibliotek przeznaczony do użycia z innych języków .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-107">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="1ab4c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ab4c-108">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="1ab4c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ab4c-109">Remarks</span></span>
<span data-ttu-id="1ab4c-110">W poprzednich składni `type1` reprezentuje typ argumentu lub typów i `type2` reprezentuje typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-110">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="1ab4c-111">Typy argumentów, które są reprezentowane przez `type1` są automatycznie curried.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-111">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="1ab4c-112">Sugeruje to, że dla tego typu formularz krotki Jeśli argumentów funkcji docelowej są curried i krotka ujętego w nawiasy dla argumentów, które znajdują się już w postaci spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-112">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="1ab4c-113">Automatyczne currying usuwa zestaw nawiasów, pozostawiając argumentu spójnej kolekcji, który pasuje do metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-113">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="1ab4c-114">Zapoznaj się przykładowy kod składni, które powinny być używane w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-114">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="1ab4c-115">Obiekty delegowane może zostać dołączony do F # funkcja wartości i statyczne lub wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-115">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="1ab4c-116">Bezpośrednio jako argumenty do delegowania Konstruktory mogą być przekazywane wartości funkcji języka F #.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-116">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="1ab4c-117">Dla metody statycznej utworzymy przy użyciu nazwy klasy i metody obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-117">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="1ab4c-118">Dla metody wystąpienia musisz podać wystąpienie obiektu i metody w jeden argument.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-118">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="1ab4c-119">W obu przypadkach dostęp do elementu członkowskiego operatora (`.`) jest używany.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-119">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="1ab4c-120">`Invoke` Metody w typie delegata wywołuje funkcję hermetyzowany.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-120">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="1ab4c-121">Ponadto delegatów mogą być przekazywane jako wartości funkcji, odwołując nazwę metody Invoke bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-121">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="1ab4c-122">Poniższy kod przedstawia składnię służący do tworzenia delegatów, które reprezentują różne metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-122">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="1ab4c-123">W zależności od tego, czy metoda jest metodą statyczną lub metodą wystąpienia oraz czy ma argumentów w postaci spójnej kolekcji lub w formularzu rozwinięte składnia deklarowanie i przypisywanie delegat jest nieco inne.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-123">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="1ab4c-124">Poniższy kod przedstawia niektóre różne sposoby, którymi można pracować z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-124">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="1ab4c-125">Poniżej przedstawiono dane wyjściowe w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1ab4c-125">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="1ab4c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ab4c-126">See Also</span></span>
[<span data-ttu-id="1ab4c-127">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="1ab4c-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1ab4c-128">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="1ab4c-128">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="1ab4c-129">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1ab4c-129">Events</span></span>](members/events.md)
