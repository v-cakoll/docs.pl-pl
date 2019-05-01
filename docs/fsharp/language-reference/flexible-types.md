---
title: Typy elastyczne
description: Dowiedz się, jak używać F# adnotacji typu elastyczne, co oznacza, że parametr, zmienna lub wartość ma typ, który jest zgodny z określonym typem.
ms.date: 05/16/2016
ms.openlocfilehash: 32857cc317bc6b4b7baf53b623b551e8e0733e41
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981386"
---
# <a name="flexible-types"></a><span data-ttu-id="7d8a6-103">Typy elastyczne</span><span class="sxs-lookup"><span data-stu-id="7d8a6-103">Flexible Types</span></span>

<span data-ttu-id="7d8a6-104">A *adnotacji typu elastyczne* oznacza, że parametr, zmienna lub wartość ma typ, który jest zgodny z określonego typu, w którym zgodność jest określana przez pozycji w hierarchii zorientowane obiektowo, klas lub interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="7d8a6-105">Typy elastyczne przydają się szczególnie, gdy automatycznej konwersji do typów wyżej w hierarchii typów nie występuje, ale nadal chcesz włączyć własne funkcje do pracy z dowolnego typu w hierarchii lub dowolny typ, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d8a6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d8a6-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="7d8a6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d8a6-107">Remarks</span></span>

<span data-ttu-id="7d8a6-108">W poprzedniej składni *typu* reprezentuje typem bazowym lub interfejsem.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="7d8a6-109">Typ ogólny, który ma ograniczenie, które ogranicza dozwolonymi typami na typy, które są zgodne z typem base lub interface odpowiada elastycznym typem.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="7d8a6-110">Oznacza to, że następujące dwa wiersze kodu są równoważne.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="7d8a6-111">Typy elastyczne są przydatne w kilku sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="7d8a6-112">Na przykład w przypadku wyższych funkcji order (funkcji, która przyjmuje funkcję jako argument) jest często przydatne do funkcji elastyczne typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="7d8a6-113">W poniższym przykładzie użycie elastycznym typem z argumentem sekwencji w `iterate2` umożliwia wyższe funkcji kolejność pracy z funkcjami, które generują sekwencje, tablic, list i innego typu wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="7d8a6-114">Należy wziąć pod uwagę następujące dwie funkcje, jeden z zwraca ona sekwencji innych, które zwraca elastycznym typem.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="7d8a6-115">Inny przykład należy wziąć pod uwagę [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkcja biblioteki:</span><span class="sxs-lookup"><span data-stu-id="7d8a6-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="7d8a6-116">Można przekazać dowolny poniższe sekwencje wyliczalny dotyczących wyłącznie tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="7d8a6-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="7d8a6-117">Listę list</span><span class="sxs-lookup"><span data-stu-id="7d8a6-117">A list of lists</span></span>
- <span data-ttu-id="7d8a6-118">Listy tablic</span><span class="sxs-lookup"><span data-stu-id="7d8a6-118">A list of arrays</span></span>
- <span data-ttu-id="7d8a6-119">Array, list</span><span class="sxs-lookup"><span data-stu-id="7d8a6-119">An array of lists</span></span>
- <span data-ttu-id="7d8a6-120">Tablica sekwencji</span><span class="sxs-lookup"><span data-stu-id="7d8a6-120">An array of sequences</span></span>
- <span data-ttu-id="7d8a6-121">Dowolną kombinację wyliczalny sekwencji</span><span class="sxs-lookup"><span data-stu-id="7d8a6-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="7d8a6-122">Poniższy kod używa `Seq.concat` aby zademonstrować scenariusze, które mogą być obsługiwane za pomocą typy elastyczne.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="7d8a6-123">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="7d8a6-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="7d8a6-124">W F#, tak jak w innych językach obiektowych istnieją typy pochodne kontekstów, w którym lub typy, które implementują interfejsy są automatycznie konwertowane na typ podstawowy lub typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="7d8a6-125">Automatycznej konwersji występują w argumentach bezpośredni, ale nie wtedy, gdy typ jest w stanie podrzędny, jako część bardziej złożonych typów, takich jak typ zwracany typ funkcji lub jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="7d8a6-126">W związku z tym notacji elastycznym typem jest szczególnie przydatna, gdy typ, który chcesz zastosować go do jest częścią typu bardziej złożone.</span><span class="sxs-lookup"><span data-stu-id="7d8a6-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d8a6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d8a6-127">See also</span></span>

- [<span data-ttu-id="7d8a6-128">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="7d8a6-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7d8a6-129">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7d8a6-129">Generics</span></span>](generics/index.md)