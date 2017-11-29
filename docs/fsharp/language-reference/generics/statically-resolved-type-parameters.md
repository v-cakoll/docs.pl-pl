---
title: "Statycznie rozwiązywane parametry typu (F#)"
description: "Dowiedz się, jak używać F # statycznie rozwiązywane typ parametru, który zostanie zastąpiony rzeczywisty typ w czasie kompilacji zamiast w czasie wykonywania."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 88b4590a4323e75949c1915503b51793283792de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="a6dcb-104">Statycznie rozwiązywane parametry typu</span><span class="sxs-lookup"><span data-stu-id="a6dcb-104">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="a6dcb-105">A *parametr typu statycznie rozwiązywane* jest parametrem typu, który jest zastępowany rzeczywisty typ w czasie kompilacji zamiast w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-105">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="a6dcb-106">Są one poprzedzone symbolem daszek (^).</span><span class="sxs-lookup"><span data-stu-id="a6dcb-106">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="a6dcb-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6dcb-107">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="a6dcb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6dcb-108">Remarks</span></span>
<span data-ttu-id="a6dcb-109">W języku F # istnieją dwa różne typy parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-109">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="a6dcb-110">Rodzaj pierwszy jest parametr standardowa typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-110">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="a6dcb-111">Te są oznaczeni apostrof ('), podobnie jak w `'T` i `'U`.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-111">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="a6dcb-112">Są one równoważne parametry typu ogólnego w innych językach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-112">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="a6dcb-113">Innego typu jest statycznie rozwiązane i jest określane przez symbol karetki, podobnie jak w `^T` i `^U`.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-113">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="a6dcb-114">Statycznie rozwiązywane parametry typu są szczególnie przydatne w połączeniu z ograniczenia elementu członkowskiego, które są ograniczenia, które pozwalają określić, że typem argumentu musi być określonego elementu członkowskiego lub elementy członkowskie, aby mogły być używane.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-114">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="a6dcb-115">Nie istnieje sposób tworzenia tego rodzaju ograniczenia za pomocą parametru typu ogólnego regularne.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-115">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="a6dcb-116">W poniższej tabeli przedstawiono podobieństwa i różnice między dwa rodzaje parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-116">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="a6dcb-117">Funkcja</span><span class="sxs-lookup"><span data-stu-id="a6dcb-117">Feature</span></span>|<span data-ttu-id="a6dcb-118">Ogólny</span><span class="sxs-lookup"><span data-stu-id="a6dcb-118">Generic</span></span>|<span data-ttu-id="a6dcb-119">Statycznie rozwiązywane</span><span class="sxs-lookup"><span data-stu-id="a6dcb-119">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="a6dcb-120">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6dcb-120">Syntax</span></span>|<span data-ttu-id="a6dcb-121">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="a6dcb-121">`'T`, `'U`</span></span>|<span data-ttu-id="a6dcb-122">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="a6dcb-122">`^T`, `^U`</span></span>|
|<span data-ttu-id="a6dcb-123">Czas rozpoznawania nazw</span><span class="sxs-lookup"><span data-stu-id="a6dcb-123">Resolution time</span></span>|<span data-ttu-id="a6dcb-124">Czas wykonywania</span><span class="sxs-lookup"><span data-stu-id="a6dcb-124">Run time</span></span>|<span data-ttu-id="a6dcb-125">Czas kompilacji</span><span class="sxs-lookup"><span data-stu-id="a6dcb-125">Compile time</span></span>|
|<span data-ttu-id="a6dcb-126">Ograniczenia elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="a6dcb-126">Member constraints</span></span>|<span data-ttu-id="a6dcb-127">Nie można używać z ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-127">Cannot be used with member constraints.</span></span>|<span data-ttu-id="a6dcb-128">Można z ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-128">Can be used with member constraints.</span></span>|
|<span data-ttu-id="a6dcb-129">Generowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a6dcb-129">Code generation</span></span>|<span data-ttu-id="a6dcb-130">Typu (lub metody) z parametry typu ogólnego standardowe powoduje generowanie jednego typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-130">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="a6dcb-131">Wiele wystąpień typów i metod są generowane, jeden dla każdego typu, który jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-131">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="a6dcb-132">Za pomocą typów</span><span class="sxs-lookup"><span data-stu-id="a6dcb-132">Use with types</span></span>|<span data-ttu-id="a6dcb-133">Można na typach.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-133">Can be used on types.</span></span>|<span data-ttu-id="a6dcb-134">Nie można używać typów.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-134">Cannot be used on types.</span></span>|
|<span data-ttu-id="a6dcb-135">Za pomocą funkcji śródwierszowych</span><span class="sxs-lookup"><span data-stu-id="a6dcb-135">Use with inline functions</span></span>|<span data-ttu-id="a6dcb-136">Nie.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-136">No.</span></span> <span data-ttu-id="a6dcb-137">Nie mogą być parametryczne wbudowanej funkcji z parametrem standardowa typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-137">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="a6dcb-138">Tak.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-138">Yes.</span></span> <span data-ttu-id="a6dcb-139">Statycznie rozwiązywane parametry typu nie można używać na funkcje i metody, które nie są wbudowane.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-139">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="a6dcb-140">Wiele F # biblioteka funkcji podstawowych, szczególnie operatory ma statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-140">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="a6dcb-141">Te funkcje i operatory są wbudowane i spowodować generowanie kodu wydajne w obliczeniach liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-141">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="a6dcb-142">Wbudowane metody i funkcje, które operatory lub innych funkcji, które mają statycznie rozwiązywane parametry typu można również użyć statycznie rozwiązywane parametry typu samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-142">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="a6dcb-143">Wnioskowanie o typie wnioskuje często takich funkcji śródwierszowych, aby mieć statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-143">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="a6dcb-144">Poniższy przykład przedstawia definicję operatora, która jest wartością parametru typu statycznie rozwiązywane.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-144">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="a6dcb-145">Rozpoznać typu `(+@)` opiera się na korzystanie z obu `(+)` i `(*)`, z którego spowodować wnioskowanie o typie w celu uwzględnienia ograniczenia elementu członkowskiego na statycznie rozwiązywane parametry typu.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-145">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="a6dcb-146">Rozpoznać typu, jak pokazano w F # interpretera ma następującą składnię.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-146">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member (+) : ^a * ^b -> ^d) and
(^a or ^c) : (static member (+) : ^a * ^c -> ^b)
```

<span data-ttu-id="a6dcb-147">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="a6dcb-147">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="a6dcb-148">Począwszy od 4.1 F #, można również określić nazwy typu konkretnego w podpisach parametru typu statycznie rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-148">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="a6dcb-149">W poprzednich wersjach językowych Nazwa typu faktycznie można wywnioskować przez kompilator, ale faktycznie nie można określić w podpisie.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-149">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="a6dcb-150">Począwszy od F # 4.1 należy także określić nazwy typów konkretnych w podpisach parametru typu statycznie rozwiązywane.</span><span class="sxs-lookup"><span data-stu-id="a6dcb-150">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="a6dcb-151">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="a6dcb-151">Here's an example:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a6dcb-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6dcb-152">See Also</span></span>
[<span data-ttu-id="a6dcb-153">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="a6dcb-153">Generics</span></span>](index.md)

[<span data-ttu-id="a6dcb-154">Wnioskowanie o typie</span><span class="sxs-lookup"><span data-stu-id="a6dcb-154">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="a6dcb-155">Automatyczna Generalizacja</span><span class="sxs-lookup"><span data-stu-id="a6dcb-155">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="a6dcb-156">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="a6dcb-156">Constraints</span></span>](constraints.md)

[<span data-ttu-id="a6dcb-157">Funkcje śródwierszowe</span><span class="sxs-lookup"><span data-stu-id="a6dcb-157">Inline Functions</span></span>](../functions/inline-functions.md)
