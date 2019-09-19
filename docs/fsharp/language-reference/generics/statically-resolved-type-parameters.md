---
title: Statycznie rozwiązywane parametry typu
description: Dowiedz się, jak F# używać statycznie rozpoznanego parametru typu, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania.
ms.date: 05/16/2016
ms.openlocfilehash: bc3310192cdaa5ae4862b8aee46b6152f61da38a
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082927"
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="54194-103">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="54194-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="54194-104">*Statycznie rozpoznany parametr typu* jest parametrem typu, który jest zastępowany rzeczywistym typem w czasie kompilacji, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="54194-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="54194-105">Są poprzedzone symbolem karetki (^).</span><span class="sxs-lookup"><span data-stu-id="54194-105">They are preceded by a caret (^) symbol.</span></span>

## <a name="syntax"></a><span data-ttu-id="54194-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="54194-106">Syntax</span></span>

```fsharp
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="54194-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54194-107">Remarks</span></span>

<span data-ttu-id="54194-108">W F# języku istnieją dwa odrębne rodzaje parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="54194-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="54194-109">Pierwszy rodzaj jest standardowym parametrem typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="54194-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="54194-110">Są one wskazywane przez apostrof ('), jak w `'T` i `'U`.</span><span class="sxs-lookup"><span data-stu-id="54194-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="54194-111">Są one odpowiednikami parametrów typu ogólnego w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54194-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="54194-112">Inny rodzaj jest statycznie rozpoznany i jest wskazywany przez symbol karetki, jak w `^T` i `^U`.</span><span class="sxs-lookup"><span data-stu-id="54194-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="54194-113">Statycznie rozpoznane parametry typu są szczególnie przydatne w połączeniu z ograniczeniami elementu członkowskiego, które są ograniczeniami, które umożliwiają określenie, że argument typu musi mieć określonego członka lub członków, aby można go było używać.</span><span class="sxs-lookup"><span data-stu-id="54194-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="54194-114">Nie ma możliwości utworzenia tego rodzaju ograniczenia przy użyciu zwykłego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="54194-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="54194-115">W poniższej tabeli zestawiono podobieństwa i różnice między dwoma rodzajami parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="54194-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="54194-116">Funkcja</span><span class="sxs-lookup"><span data-stu-id="54194-116">Feature</span></span>|<span data-ttu-id="54194-117">Ogólny</span><span class="sxs-lookup"><span data-stu-id="54194-117">Generic</span></span>|<span data-ttu-id="54194-118">Statycznie rozwiązane</span><span class="sxs-lookup"><span data-stu-id="54194-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="54194-119">Składnia</span><span class="sxs-lookup"><span data-stu-id="54194-119">Syntax</span></span>|<span data-ttu-id="54194-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="54194-120">`'T`, `'U`</span></span>|<span data-ttu-id="54194-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="54194-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="54194-122">Czas rozwiązania</span><span class="sxs-lookup"><span data-stu-id="54194-122">Resolution time</span></span>|<span data-ttu-id="54194-123">W czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="54194-123">Run time</span></span>|<span data-ttu-id="54194-124">Czas kompilacji</span><span class="sxs-lookup"><span data-stu-id="54194-124">Compile time</span></span>|
|<span data-ttu-id="54194-125">Ograniczenia elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="54194-125">Member constraints</span></span>|<span data-ttu-id="54194-126">Nie można używać z ograniczeniami elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="54194-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="54194-127">Może być używany z ograniczeniami elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="54194-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="54194-128">Generowanie kodu</span><span class="sxs-lookup"><span data-stu-id="54194-128">Code generation</span></span>|<span data-ttu-id="54194-129">Typ (lub metoda) ze standardowymi parametrami typu ogólnego skutkuje generowaniem pojedynczego typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="54194-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="54194-130">Generowanych jest wiele wystąpień typów i metod, jeden dla każdego typu, który jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="54194-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="54194-131">Używanie z typami</span><span class="sxs-lookup"><span data-stu-id="54194-131">Use with types</span></span>|<span data-ttu-id="54194-132">Może być używany w typach.</span><span class="sxs-lookup"><span data-stu-id="54194-132">Can be used on types.</span></span>|<span data-ttu-id="54194-133">Nie można używać w typach.</span><span class="sxs-lookup"><span data-stu-id="54194-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="54194-134">Używanie z funkcjami wbudowanymi</span><span class="sxs-lookup"><span data-stu-id="54194-134">Use with inline functions</span></span>|<span data-ttu-id="54194-135">Nie.</span><span class="sxs-lookup"><span data-stu-id="54194-135">No.</span></span> <span data-ttu-id="54194-136">Wbudowana funkcja nie może być sparametryzowana przy użyciu standardowego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="54194-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="54194-137">Tak.</span><span class="sxs-lookup"><span data-stu-id="54194-137">Yes.</span></span> <span data-ttu-id="54194-138">Parametry typu rozpoznane statycznie nie mogą być używane w funkcjach lub metodach, które nie są wbudowane.</span><span class="sxs-lookup"><span data-stu-id="54194-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="54194-139">Wiele F# podstawowych funkcji biblioteki, w szczególności operatorów, ma statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="54194-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="54194-140">Te funkcje i operatory są wbudowane i powodują wydajne generowanie kodu dla obliczeń numerycznych.</span><span class="sxs-lookup"><span data-stu-id="54194-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="54194-141">Metody wbudowane i funkcje, które używają operatorów lub używają innych funkcji, które mają parametry typu statycznie rozpoznane, mogą również używać parametrów typu statycznie rozpoznanych.</span><span class="sxs-lookup"><span data-stu-id="54194-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="54194-142">Często, wnioskowanie o typie wnioskuje, że funkcje wbudowane, które mają statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="54194-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="54194-143">Poniższy przykład ilustruje definicję operatora, który jest wywnioskowany, aby miał statycznie rozpoznany parametr typu.</span><span class="sxs-lookup"><span data-stu-id="54194-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="54194-144">Rozpoznany typ `(+@)` jest oparty na użyciu obu `(+)` i `(*)`, obu, z których wynika, że wnioskowanie o typie do wnioskowania ograniczeń składowych na statycznie rozpoznanych parametrach typu.</span><span class="sxs-lookup"><span data-stu-id="54194-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="54194-145">Rozpoznany typ, jak pokazano w F# interpreterze, jest następujący.</span><span class="sxs-lookup"><span data-stu-id="54194-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="54194-146">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="54194-146">The output is as follows.</span></span>

```console
2
1.500000
```

<span data-ttu-id="54194-147">Począwszy od F# 4,1, można także określić konkretne nazwy typów w sygnaturach parametrów typu, które są rozpoznawane statycznie.</span><span class="sxs-lookup"><span data-stu-id="54194-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="54194-148">W poprzednich wersjach języka nazwa typu mogła zostać wywnioskowana przez kompilator, ale nie można jej było określić w podpisie.</span><span class="sxs-lookup"><span data-stu-id="54194-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="54194-149">Począwszy od F# 4,1, można także określić konkretne nazwy typów w sygnaturach parametrów typu, które są rozpoznawane statycznie.</span><span class="sxs-lookup"><span data-stu-id="54194-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="54194-150">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="54194-150">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="54194-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54194-151">See also</span></span>

- [<span data-ttu-id="54194-152">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="54194-152">Generics</span></span>](index.md)
- [<span data-ttu-id="54194-153">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="54194-153">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="54194-154">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="54194-154">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="54194-155">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="54194-155">Constraints</span></span>](constraints.md)
- [<span data-ttu-id="54194-156">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="54194-156">Inline Functions</span></span>](../functions/inline-functions.md)
