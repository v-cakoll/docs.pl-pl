---
title: Typy elastyczne (F#)
description: "Dowiedz się, jak używać F # elastycznym typem adnotacji, co oznacza, że parametr, zmiennej lub wartość ma typ, który jest zgodny z określonym typem."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a><span data-ttu-id="9c6fd-104">Typy elastyczne</span><span class="sxs-lookup"><span data-stu-id="9c6fd-104">Flexible Types</span></span>

<span data-ttu-id="9c6fd-105">A *adnotacji typu elastyczne* oznacza, że parametr, zmiennej lub wartość ma typ, który jest zgodny z określonym typem, których zgodność jest określany przez położenie w hierarchii zorientowane obiektowo interfejsów lub klas.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-105">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="9c6fd-106">Typy elastyczne przydają się szczególnie, gdy automatycznej konwersji do typów wyżej w hierarchii typów nie występuje, ale nadal chcesz włączyć funkcjonalność programu do pracy z dowolnego typu w hierarchii lub dowolnego typu, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-106">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c6fd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c6fd-107">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="9c6fd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c6fd-108">Remarks</span></span>

<span data-ttu-id="9c6fd-109">W poprzednich składni *typu* reprezentuje typu podstawowego lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-109">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="9c6fd-110">Elastyczne typu jest odpowiednikiem typu ogólnego, który ma ograniczenie, która ogranicza dozwolonymi typami do typów, które są zgodne z typem base lub interface.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-110">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="9c6fd-111">Oznacza to, że następujące dwa wiersze kodu są równoważne.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-111">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="9c6fd-112">Typy elastyczne są przydatne w kilku sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-112">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="9c6fd-113">Na przykład jeśli masz wyższej funkcji order (funkcja przyjmuje jako argument funkcji), warto często elastyczne typ zwracany funkcji.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-113">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="9c6fd-114">W poniższym przykładzie użycie elastyczne typu z argumentem sekwencji w `iterate2` umożliwia wyższej funkcji order do pracy z funkcjami, które generują sekwencji, tablic, list i innego typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-114">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="9c6fd-115">Należy wziąć pod uwagę następujące dwie funkcje, jeden z których zwraca sekwencji, drugi z nich zwraca typ elastyczne.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-115">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="9c6fd-116">Inny przykład wziąć pod uwagę [SEQ.concat —](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkcja biblioteki:</span><span class="sxs-lookup"><span data-stu-id="9c6fd-116">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="9c6fd-117">Żadnego z następujących wyliczalny sekwencji można przekazać do tej funkcji:</span><span class="sxs-lookup"><span data-stu-id="9c6fd-117">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="9c6fd-118">Listę list</span><span class="sxs-lookup"><span data-stu-id="9c6fd-118">A list of lists</span></span>
- <span data-ttu-id="9c6fd-119">Lista tablic</span><span class="sxs-lookup"><span data-stu-id="9c6fd-119">A list of arrays</span></span>
- <span data-ttu-id="9c6fd-120">Tablica list</span><span class="sxs-lookup"><span data-stu-id="9c6fd-120">An array of lists</span></span>
- <span data-ttu-id="9c6fd-121">Tablica sekwencji</span><span class="sxs-lookup"><span data-stu-id="9c6fd-121">An array of sequences</span></span>
- <span data-ttu-id="9c6fd-122">Dowolną kombinację wyliczalny sekwencji</span><span class="sxs-lookup"><span data-stu-id="9c6fd-122">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="9c6fd-123">Poniższy kod używa `Seq.concat` aby zademonstrować scenariusze, które można obsługiwać przy użyciu typy elastyczne.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-123">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="9c6fd-124">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="9c6fd-124">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="9c6fd-125">W języku F # jak w innych językach zorientowane obiektowo istnieją kontekstów, w których typy pochodne lub typów, które implementują interfejsy są automatycznie konwertowane na typ podstawowy lub typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-125">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="9c6fd-126">Te automatycznej konwersji wystąpić w argumentach bezpośrednio, ale nie w przypadku, gdy typem jest w stanie podrzędny, jako część typu bardziej złożonych, takie jak typ zwracany typ funkcji lub jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-126">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="9c6fd-127">W związku z tym notacji elastycznym typem jest szczególnie przydatna, jeśli typ, który chcesz zastosować go do jest częścią typu bardziej złożonych.</span><span class="sxs-lookup"><span data-stu-id="9c6fd-127">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c6fd-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c6fd-128">See Also</span></span>

[<span data-ttu-id="9c6fd-129">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="9c6fd-129">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9c6fd-130">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="9c6fd-130">Generics</span></span>](generics/index.md)
