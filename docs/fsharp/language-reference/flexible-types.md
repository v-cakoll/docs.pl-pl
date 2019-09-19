---
title: Typy elastyczne
description: Dowiedz się, F# jak używać elastycznej adnotacji typu, która wskazuje, że parametr, zmienna lub wartość ma typ zgodny z określonym typem.
ms.date: 05/16/2016
ms.openlocfilehash: bf05f78f163d1f9c73c667df60925b66a5315627
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083067"
---
# <a name="flexible-types"></a><span data-ttu-id="213f5-103">Typy elastyczne</span><span class="sxs-lookup"><span data-stu-id="213f5-103">Flexible Types</span></span>

<span data-ttu-id="213f5-104">Typ *elastycznyj adnotacji* wskazuje, że parametr, zmienna lub wartość ma typ, który jest zgodny z określonym typem, gdzie zgodność jest określana na podstawie położenia w hierarchii obiektów klasy lub interfejsów zorientowanych na obiekt.</span><span class="sxs-lookup"><span data-stu-id="213f5-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="213f5-105">Typy elastyczne są przydatne w przypadku, gdy konwersja automatyczna na typy wyższe w hierarchii typów nie występuje, ale mimo to chcesz włączyć funkcję do pracy z dowolnym typem w hierarchii lub dowolnym typem, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="213f5-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="213f5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="213f5-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="213f5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="213f5-107">Remarks</span></span>

<span data-ttu-id="213f5-108">W poprzedniej składni *Typ* reprezentuje typ podstawowy lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="213f5-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="213f5-109">Elastyczny typ jest równoważny z typem ogólnym, który ma ograniczenie, które ogranicza dozwolone typy do typów, które są zgodne z typem podstawowym lub interfejsem.</span><span class="sxs-lookup"><span data-stu-id="213f5-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="213f5-110">Oznacza to, że dwa następujące wiersze kodu są równoważne.</span><span class="sxs-lookup"><span data-stu-id="213f5-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="213f5-111">Elastyczne typy są przydatne w kilku typach sytuacji.</span><span class="sxs-lookup"><span data-stu-id="213f5-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="213f5-112">Na przykład jeśli masz funkcję wyższej kolejności (funkcja, która przyjmuje funkcję jako argument), często przydatna jest funkcja zwracająca typ elastyczny.</span><span class="sxs-lookup"><span data-stu-id="213f5-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="213f5-113">W poniższym przykładzie użycie elastycznego typu z argumentem sekwencji w `iterate2` włącza funkcję wyższego rzędu do pracy z funkcjami, które generują sekwencje, tablice, listy i wszelkie inne wyliczalne typy.</span><span class="sxs-lookup"><span data-stu-id="213f5-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="213f5-114">Weź pod uwagę następujące dwie funkcje, z których jedna zwraca sekwencję, a druga zwraca typ elastyczny.</span><span class="sxs-lookup"><span data-stu-id="213f5-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="213f5-115">W innym przykładzie należy rozważyć funkcję biblioteki [SEQ. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) :</span><span class="sxs-lookup"><span data-stu-id="213f5-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="213f5-116">Do tej funkcji można przekazać dowolną z następujących wyliczalnych sekwencji:</span><span class="sxs-lookup"><span data-stu-id="213f5-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="213f5-117">Lista list</span><span class="sxs-lookup"><span data-stu-id="213f5-117">A list of lists</span></span>
- <span data-ttu-id="213f5-118">Lista tablic</span><span class="sxs-lookup"><span data-stu-id="213f5-118">A list of arrays</span></span>
- <span data-ttu-id="213f5-119">Tablica list</span><span class="sxs-lookup"><span data-stu-id="213f5-119">An array of lists</span></span>
- <span data-ttu-id="213f5-120">Tablica sekwencji</span><span class="sxs-lookup"><span data-stu-id="213f5-120">An array of sequences</span></span>
- <span data-ttu-id="213f5-121">Wszystkie inne kombinacje wyliczalnych sekwencji</span><span class="sxs-lookup"><span data-stu-id="213f5-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="213f5-122">Poniższy kod służy `Seq.concat` do zademonstrowania scenariuszy, które można obsługiwać przy użyciu elastycznych typów.</span><span class="sxs-lookup"><span data-stu-id="213f5-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="213f5-123">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="213f5-123">The output is as follows.</span></span>

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="213f5-124">W F#, podobnie jak w innych językach zorientowanych obiektowo, istnieją konteksty, w których typy pochodne lub typy, które implementują interfejsy są automatycznie konwertowane na typ podstawowy lub typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="213f5-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="213f5-125">Te konwersje automatyczne występują w argumentach bezpośrednich, ale nie w przypadku, gdy typ znajduje się w pozycji podrzędnej, jako część bardziej złożonego typu, takiego jak typ zwracany typu funkcji lub jako argument typu.</span><span class="sxs-lookup"><span data-stu-id="213f5-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="213f5-126">W ten sposób, elastyczny zapis typu jest szczególnie przydatny, gdy typ, który jest stosowany, jest częścią bardziej złożonego typu.</span><span class="sxs-lookup"><span data-stu-id="213f5-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="213f5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="213f5-127">See also</span></span>

- [<span data-ttu-id="213f5-128">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="213f5-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="213f5-129">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="213f5-129">Generics</span></span>](./generics/index.md)
