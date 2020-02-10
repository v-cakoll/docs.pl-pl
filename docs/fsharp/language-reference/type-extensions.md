---
title: Rozszerzenia typu
description: Dowiedz F# się, jak rozszerzenia typów umożliwiają dodawanie nowych elementów członkowskich do wcześniej zdefiniowanego typu obiektu.
ms.date: 02/05/2020
ms.openlocfilehash: 9ab3a007783f67fd8d80cff840ac3085fdcd60f7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092684"
---
# <a name="type-extensions"></a><span data-ttu-id="be0d8-103">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="be0d8-103">Type extensions</span></span>

<span data-ttu-id="be0d8-104">Rozszerzenia typu (nazywane również _powiększeniami_) są rodziną funkcji, które umożliwiają dodawanie nowych elementów członkowskich do wcześniej zdefiniowanego typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="be0d8-105">Te trzy funkcje są następujące:</span><span class="sxs-lookup"><span data-stu-id="be0d8-105">The three features are:</span></span>

- <span data-ttu-id="be0d8-106">Wewnętrzne rozszerzenia typów</span><span class="sxs-lookup"><span data-stu-id="be0d8-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="be0d8-107">Opcjonalne rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="be0d8-107">Optional type extensions</span></span>
- <span data-ttu-id="be0d8-108">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="be0d8-108">Extension methods</span></span>

<span data-ttu-id="be0d8-109">Każdy z nich może być używany w różnych scenariuszach i ma różne kompromisy.</span><span class="sxs-lookup"><span data-stu-id="be0d8-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="be0d8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="be0d8-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="be0d8-111">Wewnętrzne rozszerzenia typów</span><span class="sxs-lookup"><span data-stu-id="be0d8-111">Intrinsic type extensions</span></span>

<span data-ttu-id="be0d8-112">Wewnętrzny typ wewnętrzny to rozszerzenie typu, które rozszerza typ zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="be0d8-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="be0d8-113">Wewnętrzne rozszerzenia typu muszą być zdefiniowane w tym samym pliku **i** w tej samej przestrzeni nazw lub module co typ, który rozszerza.</span><span class="sxs-lookup"><span data-stu-id="be0d8-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="be0d8-114">Wszystkie inne definicje spowodują, że są one [opcjonalnymi rozszerzeniami typów](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="be0d8-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="be0d8-115">Wewnętrzne rozszerzenia typów są czasami bardziej przejrzystym sposobem oddzielania funkcjonalności od deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="be0d8-116">Poniższy przykład pokazuje, jak zdefiniować rozszerzenie typu wewnętrznego:</span><span class="sxs-lookup"><span data-stu-id="be0d8-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="be0d8-117">Użycie rozszerzenia typu umożliwia rozdzielenie następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="be0d8-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="be0d8-118">Deklaracja typu `Variant`</span><span class="sxs-lookup"><span data-stu-id="be0d8-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="be0d8-119">Funkcja drukowania klasy `Variant` w zależności od jej "kształtu"</span><span class="sxs-lookup"><span data-stu-id="be0d8-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="be0d8-120">Sposób dostępu do funkcji drukowania przy użyciu notacji `.`w stylu obiektu</span><span class="sxs-lookup"><span data-stu-id="be0d8-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="be0d8-121">Jest to alternatywa dla definiowania wszystkiego jako elementu członkowskiego na `Variant`.</span><span class="sxs-lookup"><span data-stu-id="be0d8-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="be0d8-122">Chociaż nie jest to jeszcze lepsze rozwiązanie, może to być przejrzysta reprezentacja funkcji w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="be0d8-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="be0d8-123">Wewnętrzne rozszerzenia typów są kompilowane jako elementy członkowskie typu, które rozszerzają i pojawiają się w typie, gdy typ jest rozpatrywany przez odbicie.</span><span class="sxs-lookup"><span data-stu-id="be0d8-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="be0d8-124">Opcjonalne rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="be0d8-124">Optional type extensions</span></span>

<span data-ttu-id="be0d8-125">Opcjonalne rozszerzenie typu to rozszerzenie, które pojawia się poza oryginalnym modułem, przestrzenią nazw lub zestawem rozszerzanego typu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="be0d8-126">Opcjonalne rozszerzenia typu są przydatne do rozszerzania typu, który nie został jeszcze zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="be0d8-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="be0d8-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="be0d8-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="be0d8-128">Teraz możesz uzyskiwać dostęp do `RepeatElements` tak, jakby był członkiem <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak moduł `Extensions` jest otwarty w zakresie, w którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="be0d8-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="be0d8-129">Rozszerzenia opcjonalne nie są wyświetlane na rozszerzonym typie, gdy są badane według odbicia.</span><span class="sxs-lookup"><span data-stu-id="be0d8-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="be0d8-130">Rozszerzenia opcjonalne muszą znajdować się w modułach i są tylko w zakresie, gdy moduł, który zawiera rozszerzenie, jest otwarty lub jest w innym zakresie.</span><span class="sxs-lookup"><span data-stu-id="be0d8-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="be0d8-131">Opcjonalne elementy członkowskie rozszerzenia są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazaniem niejawnie jako pierwszy parametr.</span><span class="sxs-lookup"><span data-stu-id="be0d8-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="be0d8-132">Jednak działają tak, jakby były członkami wystąpienia lub statycznymi elementami członkowskimi zgodnie z ich deklarowaniem.</span><span class="sxs-lookup"><span data-stu-id="be0d8-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="be0d8-133">Opcjonalne elementy członkowskie rozszerzenia nie są również widoczne C# dla użytkowników ani Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="be0d8-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="be0d8-134">Mogą być używane tylko w innym F# kodzie.</span><span class="sxs-lookup"><span data-stu-id="be0d8-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="be0d8-135">Ogólne ograniczenie wewnętrznych i opcjonalnych rozszerzeń typów</span><span class="sxs-lookup"><span data-stu-id="be0d8-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="be0d8-136">Istnieje możliwość zadeklarować rozszerzenie typu w typie ogólnym, w którym zmienna typu jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="be0d8-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="be0d8-137">Wymóg polega na tym, że ograniczenie deklaracji rozszerzenia jest zgodne z ograniczeniem zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="be0d8-138">Jednak nawet wtedy, gdy ograniczenia są dopasowywane między zadeklarowanym typem a rozszerzeniem typu, można wywnioskować ograniczenie przez treść rozszerzonego elementu członkowskiego, który nakłada inny wymóg w parametrze typu niż zadeklarowany typ.</span><span class="sxs-lookup"><span data-stu-id="be0d8-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="be0d8-139">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="be0d8-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="be0d8-140">Nie ma możliwości uzyskania tego kodu do pracy z opcjonalnym rozszerzeniem typu:</span><span class="sxs-lookup"><span data-stu-id="be0d8-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="be0d8-141">W takim przypadku element członkowski `Sum` ma inne ograniczenie dotyczące `'T` (`static member get_Zero` i `static member (+)`) niż zdefiniowane przez rozszerzenie typu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="be0d8-142">Modyfikowanie rozszerzenia typu tak samo, jak `Sum` nie będzie już zgodne ze zdefiniowanymi ograniczeniami `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="be0d8-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="be0d8-143">Zmiana `member this.Sum` na `member inline this.Sum` spowoduje wystąpienie błędu, że ograniczenia typu są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="be0d8-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="be0d8-144">Wymagane są metody statyczne, które "zmiennoprzecinkowe miejsce" i mogą być prezentowane tak, jakby rozszerzali typ.</span><span class="sxs-lookup"><span data-stu-id="be0d8-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="be0d8-145">Jest to miejsce, w którym metody rozszerzające stają się niezbędne.</span><span class="sxs-lookup"><span data-stu-id="be0d8-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="be0d8-146">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="be0d8-146">Extension methods</span></span>

<span data-ttu-id="be0d8-147">Wreszcie metody rozszerzające (nazywane czasami "C# elementami członkowskimi rozszerzenia stylu") mogą być F# deklarowane jako statyczna metoda członkowska klasy.</span><span class="sxs-lookup"><span data-stu-id="be0d8-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="be0d8-148">Metody rozszerzające są przydatne w przypadku definiowania rozszerzeń dla typu ogólnego, który będzie ograniczać zmienną typu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="be0d8-149">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="be0d8-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="be0d8-150">Gdy jest używany, ten kod będzie wyglądać tak, jakby `Sum` jest zdefiniowany w <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak `Extensions` został otwarty lub znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="be0d8-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="be0d8-151">Aby rozszerzenie było dostępne dla kodu VB.NET, wymagany jest dodatkowy `ExtensionAttribute` na poziomie zestawu:</span><span class="sxs-lookup"><span data-stu-id="be0d8-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="be0d8-152">Inne uwagi</span><span class="sxs-lookup"><span data-stu-id="be0d8-152">Other remarks</span></span>

<span data-ttu-id="be0d8-153">Rozszerzenia typu mają również następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="be0d8-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="be0d8-154">Dowolny typ, do którego można uzyskać dostęp, może zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="be0d8-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="be0d8-155">Rozszerzenia typu wewnętrznego i opcjonalnego mogą definiować _dowolny_ typ elementu członkowskiego, a nie tylko metody.</span><span class="sxs-lookup"><span data-stu-id="be0d8-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="be0d8-156">Możliwe jest również, że właściwości rozszerzenia są na przykład.</span><span class="sxs-lookup"><span data-stu-id="be0d8-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="be0d8-157">Token `self-identifier` w [składni](type-extensions.md#syntax) reprezentuje wystąpienie wywoływanego typu, podobnie jak zwykłe elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="be0d8-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="be0d8-158">Rozszerzone elementy członkowskie mogą być statyczne lub składowe wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="be0d8-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="be0d8-159">Zmienne typu w rozszerzeniu typu muszą być zgodne z ograniczeniami zadeklarowanego typu.</span><span class="sxs-lookup"><span data-stu-id="be0d8-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="be0d8-160">Istnieją również następujące ograniczenia dotyczące rozszerzeń typów:</span><span class="sxs-lookup"><span data-stu-id="be0d8-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="be0d8-161">Rozszerzenia typu nie obsługują metod wirtualnych ani abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="be0d8-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="be0d8-162">Rozszerzenia typu nie obsługują metod zastępowania jako rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="be0d8-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="be0d8-163">Rozszerzenia typu nie obsługują [statycznie rozpoznanych parametrów typu](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="be0d8-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="be0d8-164">Opcjonalne rozszerzenia typu nie obsługują konstruktorów jako rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="be0d8-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="be0d8-165">Nie można definiować rozszerzeń typu w [skrótach typu](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="be0d8-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="be0d8-166">Rozszerzenia typów nie są prawidłowe dla `byref<'T>` (chociaż można je zadeklarować).</span><span class="sxs-lookup"><span data-stu-id="be0d8-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="be0d8-167">Rozszerzenia typów nie są prawidłowe dla atrybutów (chociaż mogą być deklarowane).</span><span class="sxs-lookup"><span data-stu-id="be0d8-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="be0d8-168">Można zdefiniować rozszerzenia, które przeciążą inne metody o tej samej nazwie, F# ale kompilator daje preferencjom metody niewywołujące, jeśli istnieje niejednoznaczne wywołanie.</span><span class="sxs-lookup"><span data-stu-id="be0d8-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="be0d8-169">Jeśli istnieje wiele rozszerzeń typu wewnętrznego dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="be0d8-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="be0d8-170">W przypadku opcjonalnych rozszerzeń typu elementy członkowskie w różnych rozszerzeniach typu tego samego typu mogą mieć takie same nazwy.</span><span class="sxs-lookup"><span data-stu-id="be0d8-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="be0d8-171">Błędy niejednoznaczne występują tylko wtedy, gdy kod klienta otwiera dwa różne zakresy, które definiują te same nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="be0d8-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="be0d8-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be0d8-172">See also</span></span>

- [<span data-ttu-id="be0d8-173">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="be0d8-173">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="be0d8-174">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="be0d8-174">Members</span></span>](./members/index.md)
