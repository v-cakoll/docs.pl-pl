---
title: Delegaty
description: Dowiedz się, jak korzystać z F#delegatów w programie.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630370"
---
# <a name="delegates"></a><span data-ttu-id="7bee3-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="7bee3-103">Delegates</span></span>

<span data-ttu-id="7bee3-104">Delegat reprezentuje wywołanie funkcji jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="7bee3-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="7bee3-105">W F#programie zazwyczaj należy używać wartości funkcji do reprezentowania funkcji jako wartości pierwszej klasy; Jednakże Delegaty są używane w .NET Framework i dlatego są potrzebne podczas współpracy z interfejsami API, które oczekują.</span><span class="sxs-lookup"><span data-stu-id="7bee3-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="7bee3-106">Mogą być również używane podczas tworzenia bibliotek przeznaczonych do użycia w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7bee3-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="7bee3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bee3-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="7bee3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bee3-108">Remarks</span></span>

<span data-ttu-id="7bee3-109">W poprzedniej składni, `type1` reprezentuje typ argumentu lub typy i `type2` reprezentuje zwracany typ.</span><span class="sxs-lookup"><span data-stu-id="7bee3-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="7bee3-110">Typy argumentów, które są reprezentowane przez `type1` są automatycznie rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="7bee3-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="7bee3-111">Sugeruje to, że dla tego typu używasz formularza spójnego, jeśli argumenty funkcji docelowej to rozwinięte, a krotka w nawiasach dla argumentów, które znajdują się już w formularzu krotki.</span><span class="sxs-lookup"><span data-stu-id="7bee3-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="7bee3-112">Automatyczna currying usuwa zestaw nawiasów, pozostawiając argument krotki pasujący do metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="7bee3-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="7bee3-113">Zapoznaj się z przykładem kodu dla składni, która powinna być używana w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="7bee3-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="7bee3-114">Delegaty mogą być dołączane do F# wartości funkcji i statycznych lub wystąpień metod.</span><span class="sxs-lookup"><span data-stu-id="7bee3-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="7bee3-115">F#wartości funkcji można przekazać bezpośrednio jako argumenty do delegatów konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="7bee3-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="7bee3-116">Dla metody statycznej można skonstruować delegata przy użyciu nazwy klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="7bee3-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="7bee3-117">Dla metody wystąpienia, należy podać wystąpienie obiektu i metodę w jednym argumencie.</span><span class="sxs-lookup"><span data-stu-id="7bee3-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="7bee3-118">W obu przypadkach używany jest operator dostępu do elementu`.`członkowskiego ().</span><span class="sxs-lookup"><span data-stu-id="7bee3-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="7bee3-119">`Invoke` Metoda w typie delegata wywołuje funkcję hermetyzowaną.</span><span class="sxs-lookup"><span data-stu-id="7bee3-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="7bee3-120">Ponadto Delegaty mogą być przesyłane jako wartości funkcji przez odwołanie się do nazwy metody Invoke bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="7bee3-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="7bee3-121">Poniższy kod przedstawia składnię tworzenia delegatów reprezentujących różne metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="7bee3-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="7bee3-122">W zależności od tego, czy metoda jest metodą statyczną czy metodą wystąpienia i czy ma argumenty w formularzu krotki lub formularzu rozwinięte, składnia do deklarowania i przypisywania delegata jest nieco inna.</span><span class="sxs-lookup"><span data-stu-id="7bee3-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="7bee3-123">Poniższy kod przedstawia niektóre różne sposoby pracy z delegatami.</span><span class="sxs-lookup"><span data-stu-id="7bee3-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="7bee3-124">Poniżej przedstawiono dane wyjściowe poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="7bee3-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="7bee3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bee3-125">See also</span></span>

- [<span data-ttu-id="7bee3-126">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7bee3-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7bee3-127">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="7bee3-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="7bee3-128">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7bee3-128">Events</span></span>](./members/events.md)
