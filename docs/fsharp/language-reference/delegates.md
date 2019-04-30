---
title: Delegaty
description: Dowiedz się, jak pracować z delegatów w F#.
ms.date: 05/16/2016
ms.openlocfilehash: 772685488b7caef92123979d817929c631248afb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766080"
---
# <a name="delegates"></a><span data-ttu-id="92bbb-103">Delegaty</span><span class="sxs-lookup"><span data-stu-id="92bbb-103">Delegates</span></span>

<span data-ttu-id="92bbb-104">Obiekt delegowany reprezentuje wywołanie funkcji jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="92bbb-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="92bbb-105">W F#, zazwyczaj należy używać wartości funkcji do reprezentowania funkcje jako wartości pierwszej klasy. Jednak obiekty delegowane są używane w programie .NET Framework i dlatego są wymagane podczas współdziałania z interfejsami API, które ich wymagają.</span><span class="sxs-lookup"><span data-stu-id="92bbb-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="92bbb-106">One może również służyć podczas tworzenia bibliotek przeznaczone do użycia z innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92bbb-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="92bbb-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="92bbb-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="92bbb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92bbb-108">Remarks</span></span>

<span data-ttu-id="92bbb-109">W poprzedniej składni `type1` reprezentuje argument typu lub typów i `type2` reprezentuje typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="92bbb-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="92bbb-110">Typy argumentów, które są reprezentowane przez `type1` są automatycznie przenoszeni.</span><span class="sxs-lookup"><span data-stu-id="92bbb-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="92bbb-111">Sugeruje to, że dla tego typu, możesz użyć formularzu krotki, jeśli są przenoszeni argumentów funkcji docelowej i krotki ujęty w nawiasy dla argumentów, które już znajdują się w formularzu krotki.</span><span class="sxs-lookup"><span data-stu-id="92bbb-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="92bbb-112">Automatyczne currying usuwa zestaw nawiasów, pozostawiając argument spójnej kolekcji, który pasuje do metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="92bbb-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="92bbb-113">Zobacz przykład kodu dla składni, do którego należy używać w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="92bbb-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="92bbb-114">Delegaty mogą być dołączane do F# funkcji wartości i statyczne lub wystąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="92bbb-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="92bbb-115">F#wartości funkcji mogą być przekazywane bezpośrednio jako argumenty do delegowanie konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="92bbb-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="92bbb-116">W przypadku statycznej metody delegata konstruowania przy użyciu nazwy klasy i metody.</span><span class="sxs-lookup"><span data-stu-id="92bbb-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="92bbb-117">Dla metody wystąpienia możesz podać wystąpienie obiektu i metody w jeden argument.</span><span class="sxs-lookup"><span data-stu-id="92bbb-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="92bbb-118">W obu przypadkach należy uzyskać dostęp — operator (`.`) jest używany.</span><span class="sxs-lookup"><span data-stu-id="92bbb-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="92bbb-119">`Invoke` Metody na typ delegata wywołania zhermetyzowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="92bbb-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="92bbb-120">Ponadto delegatów mogą być przekazywane jako wartości funkcji, odwołując się do nazwy metody Invoke, bez nawiasów.</span><span class="sxs-lookup"><span data-stu-id="92bbb-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="92bbb-121">Poniższy kod przedstawia składnię utworzenie obiektów delegowanych, które reprezentują różne metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="92bbb-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="92bbb-122">W zależności od tego, czy metoda jest metodą statyczną lub metodą wystąpienia oraz czy ma argumentów w formularzu krotki lub formularzu rozwinięte składnia do deklarowania i przypisywanie delegata jest nieco inny.</span><span class="sxs-lookup"><span data-stu-id="92bbb-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="92bbb-123">Poniższy kod przedstawia niektóre różne sposoby korzystania z obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="92bbb-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="92bbb-124">Dane wyjściowe w poprzednim przykładzie kodu jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="92bbb-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="92bbb-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92bbb-125">See also</span></span>

- [<span data-ttu-id="92bbb-126">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="92bbb-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="92bbb-127">Parametry i argumenty</span><span class="sxs-lookup"><span data-stu-id="92bbb-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="92bbb-128">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92bbb-128">Events</span></span>](members/events.md)