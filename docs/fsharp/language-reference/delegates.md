---
title: Delegaty (F#)
description: 'Dowiedz się, jak pracować z delegatów w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 56520cc631d889f390a7d4300be1cb3185306be9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="delegates"></a><span data-ttu-id="31372-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="31372-103">Delegates</span></span>

<span data-ttu-id="31372-104">Delegat reprezentuje wywołanie funkcji jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="31372-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="31372-105">W języku F # zazwyczaj należy użyć wartości funkcji do reprezentowania funkcje jako wartości pierwszej klasy; jednak delegatów są używane w programie .NET Framework i dlatego są wymagane, gdy współdziałać z interfejsów API, który będzie je.</span><span class="sxs-lookup"><span data-stu-id="31372-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="31372-106">Może również być używane tworzenia bibliotek przeznaczony do użycia z innych języków .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="31372-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="31372-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="31372-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="31372-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31372-108">Remarks</span></span>
<span data-ttu-id="31372-109">W poprzednich składni `type1` reprezentuje typ argumentu lub typów i `type2` reprezentuje typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="31372-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="31372-110">Typy argumentów, które są reprezentowane przez `type1` są automatycznie curried.</span><span class="sxs-lookup"><span data-stu-id="31372-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="31372-111">Sugeruje to, że dla tego typu formularz krotki Jeśli argumentów funkcji docelowej są curried i krotka ujętego w nawiasy dla argumentów, które znajdują się już w postaci spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="31372-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="31372-112">Automatyczne currying usuwa zestaw nawiasów, pozostawiając argumentu spójnej kolekcji, który pasuje do metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="31372-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="31372-113">Zapoznaj się przykładowy kod składni, które powinny być używane w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="31372-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="31372-114">Obiekty delegowane może zostać dołączony do F # funkcja wartości i statyczne lub wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="31372-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="31372-115">Bezpośrednio jako argumenty do delegowania Konstruktory mogą być przekazywane wartości funkcji języka F #.</span><span class="sxs-lookup"><span data-stu-id="31372-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="31372-116">Dla metody statycznej utworzymy przy użyciu nazwy klasy i metody obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="31372-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="31372-117">Dla metody wystąpienia musisz podać wystąpienie obiektu i metody w jeden argument.</span><span class="sxs-lookup"><span data-stu-id="31372-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="31372-118">W obu przypadkach dostęp do elementu członkowskiego operatora (`.`) jest używany.</span><span class="sxs-lookup"><span data-stu-id="31372-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="31372-119">`Invoke` Metody w typie delegata wywołuje funkcję hermetyzowany.</span><span class="sxs-lookup"><span data-stu-id="31372-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="31372-120">Ponadto delegatów mogą być przekazywane jako wartości funkcji, odwołując nazwę metody Invoke bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="31372-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="31372-121">Poniższy kod przedstawia składnię służący do tworzenia delegatów, które reprezentują różne metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="31372-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="31372-122">W zależności od tego, czy metoda jest metodą statyczną lub metodą wystąpienia oraz czy ma argumentów w postaci spójnej kolekcji lub w formularzu rozwinięte składnia deklarowanie i przypisywanie delegat jest nieco inne.</span><span class="sxs-lookup"><span data-stu-id="31372-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="31372-123">Poniższy kod przedstawia niektóre różne sposoby, którymi można pracować z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="31372-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="31372-124">Poniżej przedstawiono dane wyjściowe w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="31372-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="31372-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31372-125">See Also</span></span>
[<span data-ttu-id="31372-126">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="31372-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="31372-127">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="31372-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="31372-128">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="31372-128">Events</span></span>](members/events.md)
