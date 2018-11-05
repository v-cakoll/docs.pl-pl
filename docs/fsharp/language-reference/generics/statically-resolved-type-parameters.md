---
title: Statycznie rozwiązywane parametry typu (F#)
description: 'Dowiedz się, jak używać języka F # statystycznie rozpoznany typ parametru, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania.'
ms.date: 05/16/2016
ms.openlocfilehash: 747917fef2746dcbf363ef4b717ace5e47229800
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "48032780"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="b5702-103">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="b5702-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="b5702-104">A *statystycznie rozpoznany typ parametru* jest parametrem typu, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b5702-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="b5702-105">Są poprzedzone symbolem, daszek (^).</span><span class="sxs-lookup"><span data-stu-id="b5702-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5702-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5702-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="b5702-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5702-107">Remarks</span></span>

<span data-ttu-id="b5702-108">W języku F # istnieją dwa odrębne rodzaje parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="b5702-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="b5702-109">Pierwszy rodzaj jest parametrem standardowym typu rodzajowego.</span><span class="sxs-lookup"><span data-stu-id="b5702-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="b5702-110">Te są oznaczane apostrofem ('), podobnie jak w `'T` i `'U`.</span><span class="sxs-lookup"><span data-stu-id="b5702-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="b5702-111">Są one równoważnymi parametrami typu rodzajowego w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5702-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="b5702-112">Inny rodzaj jest statycznie rozwiązany i jest oznaczany symbolem daszka, podobnie jak w `^T` i `^U`.</span><span class="sxs-lookup"><span data-stu-id="b5702-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="b5702-113">Statycznie rozwiązywane parametry typu są szczególnie przydatne w połączeniu z ograniczeniami elementu członkowskiego, które są ograniczeniami, które pozwalają na określenie, że argument typu musi mieć danego członka lub członków, aby możliwe było użycie.</span><span class="sxs-lookup"><span data-stu-id="b5702-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="b5702-114">Nie ma możliwości do utworzenia tego rodzaju ograniczenia przy użyciu parametru regularnego typu rodzajowego.</span><span class="sxs-lookup"><span data-stu-id="b5702-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="b5702-115">W poniższej tabeli podsumowano podobieństwa i różnice między dwoma rodzajami parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="b5702-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="b5702-116">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b5702-116">Feature</span></span>|<span data-ttu-id="b5702-117">Ogólny</span><span class="sxs-lookup"><span data-stu-id="b5702-117">Generic</span></span>|<span data-ttu-id="b5702-118">Statycznie rozwiązane</span><span class="sxs-lookup"><span data-stu-id="b5702-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="b5702-119">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5702-119">Syntax</span></span>|<span data-ttu-id="b5702-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="b5702-120">`'T`, `'U`</span></span>|<span data-ttu-id="b5702-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="b5702-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="b5702-122">Czas rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="b5702-122">Resolution time</span></span>|<span data-ttu-id="b5702-123">Czas wykonywania</span><span class="sxs-lookup"><span data-stu-id="b5702-123">Run time</span></span>|<span data-ttu-id="b5702-124">Czas kompilacji</span><span class="sxs-lookup"><span data-stu-id="b5702-124">Compile time</span></span>|
|<span data-ttu-id="b5702-125">Ograniczenia elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b5702-125">Member constraints</span></span>|<span data-ttu-id="b5702-126">Nie można używać z ograniczeniami elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b5702-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="b5702-127">Może być używany z ograniczeniami elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b5702-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="b5702-128">Generowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b5702-128">Code generation</span></span>|<span data-ttu-id="b5702-129">Typ (lub metoda) ze standardowymi parametrami ogólnego typu powoduje generowanie jednego ogólnego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="b5702-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="b5702-130">Wiele wystąpień typów i metod jest generowanych, po jednym dla każdego typu, który jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="b5702-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="b5702-131">Za pomocą typów</span><span class="sxs-lookup"><span data-stu-id="b5702-131">Use with types</span></span>|<span data-ttu-id="b5702-132">Może być stosowany na typach.</span><span class="sxs-lookup"><span data-stu-id="b5702-132">Can be used on types.</span></span>|<span data-ttu-id="b5702-133">Nie może być stosowany na typach.</span><span class="sxs-lookup"><span data-stu-id="b5702-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="b5702-134">Za pomocą wbudowanej funkcji</span><span class="sxs-lookup"><span data-stu-id="b5702-134">Use with inline functions</span></span>|<span data-ttu-id="b5702-135">Nie.</span><span class="sxs-lookup"><span data-stu-id="b5702-135">No.</span></span> <span data-ttu-id="b5702-136">Funkcja śródwierszowa nie mogą być parametryzowane ze standardowym parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b5702-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="b5702-137">Tak.</span><span class="sxs-lookup"><span data-stu-id="b5702-137">Yes.</span></span> <span data-ttu-id="b5702-138">Statycznie rozwiązywane parametry typu nie można używać na funkcje lub metody, które nie są wbudowane.</span><span class="sxs-lookup"><span data-stu-id="b5702-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="b5702-139">Wiele F # funkcji biblioteki podstawowej, zwłaszcza operatory, ma statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="b5702-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="b5702-140">Te funkcje i operatory są wbudowane i powodują skuteczne generowanie kodu do obliczeń numerycznych.</span><span class="sxs-lookup"><span data-stu-id="b5702-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="b5702-141">Wbudowane metody i funkcje, które używają operatorów lub innych funkcji, które mają statycznie rozwiązywane parametry typu, można również użyć parametrów typu statycznie rozpoznanych, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b5702-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="b5702-142">Często wnioskowanie o typie wnioskuje takie wbudowane funkcje, aby mieć statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="b5702-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="b5702-143">Poniższy przykład przedstawia definicję operatora która została wywnioskowana, ma parametr typu statycznie rozpoznanych.</span><span class="sxs-lookup"><span data-stu-id="b5702-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="b5702-144">Rozpoznać typ `(+@)` opiera się na wykorzystaniu obu `(+)` i `(*)`, z którym spowodować, że wniosek typu wywnioskowuje ograniczenia Członkowskie na statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="b5702-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="b5702-145">Rozwiązany typ, jak pokazano w interpretera F # jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b5702-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="b5702-146">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="b5702-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="b5702-147">Począwszy od F # 4.1, można również określić konkretny typ nazwy w podpisach parametrów typu statycznie rozpoznanych.</span><span class="sxs-lookup"><span data-stu-id="b5702-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="b5702-148">W poprzednich wersjach języka nazwę typu można wywnioskować faktycznie przez kompilator, ale faktycznie nie można określić w podpisie.</span><span class="sxs-lookup"><span data-stu-id="b5702-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="b5702-149">Począwszy od F # 4.1 możesz również określić konkretny typ nazwy w podpisach parametrów typu statycznie rozpoznanych.</span><span class="sxs-lookup"><span data-stu-id="b5702-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="b5702-150">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="b5702-150">Here's an example:</span></span>

```fsharp
let inline konst x _ = x

type CFunctor() = 
    static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
    static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

    // default implementation of replace
    static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

    // call overridden replace if present
    static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
        ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="b5702-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5702-151">See also</span></span>

- [<span data-ttu-id="b5702-152">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="b5702-152">Generics</span></span>](index.md)
- [<span data-ttu-id="b5702-153">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="b5702-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="b5702-154">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="b5702-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="b5702-155">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="b5702-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="b5702-156">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="b5702-156">Inline Functions</span></span>](../functions/inline-functions.md)
