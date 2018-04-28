---
title: Statycznie rozwiązywane parametry typu (F#)
description: 'Dowiedz się, jak używać F # statycznie rozwiązywane typ parametru, który zostanie zastąpiony rzeczywisty typ w czasie kompilacji zamiast w czasie wykonywania.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da730014f1c40b6c79d72e4f46a18ef36f50de36
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="0aa51-103">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="0aa51-103">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="0aa51-104">A *parametr typu statycznie rozwiązywane* jest parametrem typu, który jest zastępowany rzeczywisty typ w czasie kompilacji zamiast w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0aa51-104">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="0aa51-105">Są one poprzedzone symbolem daszek (^).</span><span class="sxs-lookup"><span data-stu-id="0aa51-105">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="0aa51-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0aa51-106">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="0aa51-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0aa51-107">Remarks</span></span>
<span data-ttu-id="0aa51-108">W języku F # istnieją dwa różne typy parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="0aa51-108">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="0aa51-109">Rodzaj pierwszy jest parametr standardowa typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0aa51-109">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="0aa51-110">Te są oznaczeni apostrof ('), podobnie jak w `'T` i `'U`.</span><span class="sxs-lookup"><span data-stu-id="0aa51-110">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="0aa51-111">Są one równoważne parametry typu ogólnego w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0aa51-111">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="0aa51-112">Innego typu jest statycznie rozwiązane i jest określane przez symbol karetki, podobnie jak w `^T` i `^U`.</span><span class="sxs-lookup"><span data-stu-id="0aa51-112">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="0aa51-113">Statycznie rozwiązywane parametry typu są szczególnie przydatne w połączeniu z ograniczenia elementu członkowskiego, które są ograniczenia, które pozwalają określić, że typem argumentu musi być określonego elementu członkowskiego lub elementy członkowskie, aby mogły być używane.</span><span class="sxs-lookup"><span data-stu-id="0aa51-113">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="0aa51-114">Nie istnieje sposób tworzenia tego rodzaju ograniczenia za pomocą parametru typu ogólnego regularne.</span><span class="sxs-lookup"><span data-stu-id="0aa51-114">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="0aa51-115">W poniższej tabeli przedstawiono podobieństwa i różnice między dwa rodzaje parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="0aa51-115">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="0aa51-116">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0aa51-116">Feature</span></span>|<span data-ttu-id="0aa51-117">Ogólny</span><span class="sxs-lookup"><span data-stu-id="0aa51-117">Generic</span></span>|<span data-ttu-id="0aa51-118">Statycznie rozwiązywane</span><span class="sxs-lookup"><span data-stu-id="0aa51-118">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="0aa51-119">Składnia</span><span class="sxs-lookup"><span data-stu-id="0aa51-119">Syntax</span></span>|<span data-ttu-id="0aa51-120">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="0aa51-120">`'T`, `'U`</span></span>|<span data-ttu-id="0aa51-121">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="0aa51-121">`^T`, `^U`</span></span>|
|<span data-ttu-id="0aa51-122">Czas rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="0aa51-122">Resolution time</span></span>|<span data-ttu-id="0aa51-123">Czas wykonywania</span><span class="sxs-lookup"><span data-stu-id="0aa51-123">Run time</span></span>|<span data-ttu-id="0aa51-124">Czas kompilacji</span><span class="sxs-lookup"><span data-stu-id="0aa51-124">Compile time</span></span>|
|<span data-ttu-id="0aa51-125">Ograniczenia elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="0aa51-125">Member constraints</span></span>|<span data-ttu-id="0aa51-126">Nie można używać z ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0aa51-126">Cannot be used with member constraints.</span></span>|<span data-ttu-id="0aa51-127">Można z ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0aa51-127">Can be used with member constraints.</span></span>|
|<span data-ttu-id="0aa51-128">Generowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0aa51-128">Code generation</span></span>|<span data-ttu-id="0aa51-129">Typu (lub metody) z parametry typu ogólnego standardowe powoduje generowanie jednego typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="0aa51-129">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="0aa51-130">Wiele wystąpień typów i metod są generowane, jeden dla każdego typu, który jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="0aa51-130">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="0aa51-131">Za pomocą typów</span><span class="sxs-lookup"><span data-stu-id="0aa51-131">Use with types</span></span>|<span data-ttu-id="0aa51-132">Można na typach.</span><span class="sxs-lookup"><span data-stu-id="0aa51-132">Can be used on types.</span></span>|<span data-ttu-id="0aa51-133">Nie można używać typów.</span><span class="sxs-lookup"><span data-stu-id="0aa51-133">Cannot be used on types.</span></span>|
|<span data-ttu-id="0aa51-134">Za pomocą funkcji śródwierszowych</span><span class="sxs-lookup"><span data-stu-id="0aa51-134">Use with inline functions</span></span>|<span data-ttu-id="0aa51-135">Nie.</span><span class="sxs-lookup"><span data-stu-id="0aa51-135">No.</span></span> <span data-ttu-id="0aa51-136">Nie mogą być parametryczne wbudowanej funkcji z parametrem standardowa typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="0aa51-136">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="0aa51-137">Tak.</span><span class="sxs-lookup"><span data-stu-id="0aa51-137">Yes.</span></span> <span data-ttu-id="0aa51-138">Statycznie rozwiązywane parametry typu nie można używać na funkcje i metody, które nie są wbudowane.</span><span class="sxs-lookup"><span data-stu-id="0aa51-138">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="0aa51-139">Wiele F # biblioteka funkcji podstawowych, szczególnie operatory ma statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0aa51-139">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="0aa51-140">Te funkcje i operatory są wbudowane i spowodować generowanie kodu wydajne w obliczeniach liczbowych.</span><span class="sxs-lookup"><span data-stu-id="0aa51-140">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="0aa51-141">Wbudowane metody i funkcje, które operatory lub innych funkcji, które mają statycznie rozwiązywane parametry typu można również użyć statycznie rozwiązywane parametry typu samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="0aa51-141">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="0aa51-142">Wnioskowanie o typie wnioskuje często takich funkcji śródwierszowych, aby mieć statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0aa51-142">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="0aa51-143">Poniższy przykład przedstawia definicję operatora, która jest wartością parametru typu statycznie rozwiązywane.</span><span class="sxs-lookup"><span data-stu-id="0aa51-143">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="0aa51-144">Rozpoznać typu `(+@)` opiera się na korzystanie z obu `(+)` i `(*)`, z którego spowodować wnioskowanie o typie w celu uwzględnienia ograniczenia elementu członkowskiego na statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0aa51-144">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="0aa51-145">Rozpoznać typu, jak pokazano w F # interpretera ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="0aa51-145">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="0aa51-146">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="0aa51-146">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="0aa51-147">Począwszy od 4.1 F #, można również określić nazwy typu konkretnego w podpisach parametru typu statycznie rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="0aa51-147">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="0aa51-148">W poprzednich wersjach językowych Nazwa typu faktycznie można wywnioskować przez kompilator, ale faktycznie nie można określić w podpisie.</span><span class="sxs-lookup"><span data-stu-id="0aa51-148">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="0aa51-149">Począwszy od F # 4.1 należy także określić nazwy typów konkretnych w podpisach parametru typu statycznie rozwiązywane.</span><span class="sxs-lookup"><span data-stu-id="0aa51-149">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="0aa51-150">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="0aa51-150">Here's an example:</span></span>

```fsharp
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

## <a name="see-also"></a><span data-ttu-id="0aa51-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0aa51-151">See Also</span></span>
[<span data-ttu-id="0aa51-152">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="0aa51-152">Generics</span></span>](index.md)

[<span data-ttu-id="0aa51-153">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="0aa51-153">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="0aa51-154">Automatyczna generalizacja</span><span class="sxs-lookup"><span data-stu-id="0aa51-154">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="0aa51-155">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="0aa51-155">Constraints</span></span>](constraints.md)

[<span data-ttu-id="0aa51-156">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="0aa51-156">Inline Functions</span></span>](../functions/inline-functions.md)
