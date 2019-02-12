---
title: Rozszerzenia typu
description: Dowiedz się, jak F# rozszerzeń typu umożliwia dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej.
ms.date: 02/08/2019
ms.openlocfilehash: 69fb3b771b5334c5771f2ac75341b38c1dad5b90
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092478"
---
# <a name="type-extensions"></a><span data-ttu-id="24f15-103">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="24f15-103">Type extensions</span></span>

<span data-ttu-id="24f15-104">Rozszerzenia typu (nazywane również _rozszerzeniach_) to rodzina funkcji, które pozwalają na dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="24f15-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="24f15-105">Są trzy funkcje:</span><span class="sxs-lookup"><span data-stu-id="24f15-105">The three features are:</span></span>

* <span data-ttu-id="24f15-106">Rozszerzeń typu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="24f15-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="24f15-107">Opcjonalnych rozszerzeń typów</span><span class="sxs-lookup"><span data-stu-id="24f15-107">Optional type extensions</span></span>
* <span data-ttu-id="24f15-108">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="24f15-108">Extension methods</span></span>

<span data-ttu-id="24f15-109">Każda mogą być używane w różnych scenariuszach i zawiera różne kompromisy.</span><span class="sxs-lookup"><span data-stu-id="24f15-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="24f15-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="24f15-110">Syntax</span></span>

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
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="24f15-111">Rozszerzeń typu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="24f15-111">Intrinsic type extensions</span></span>

<span data-ttu-id="24f15-112">Rozszerzenie typu wewnętrznego jest rozszerzeniem typu, która rozszerza typ zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24f15-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="24f15-113">Rozszerzeń typu wewnętrznego musi być zdefiniowany w tym samym pliku **i** w tej samej przestrzeni nazw lub module jako typ, są one rozszerzanie.</span><span class="sxs-lookup"><span data-stu-id="24f15-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="24f15-114">Inne definicji spowoduje ich trwa [opcjonalnych rozszerzeń typów](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="24f15-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="24f15-115">Rozszerzeń typu wewnętrznego są czasami bardziej przejrzysty sposób oddzielić funkcje od deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="24f15-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="24f15-116">Poniższy przykład pokazuje jak zdefiniować rozszerzenie typu wewnętrznego:</span><span class="sxs-lookup"><span data-stu-id="24f15-116">The following example shows how to define an intrinsic type extension:</span></span>

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

<span data-ttu-id="24f15-117">Przy użyciu rozszerzenia typu umożliwia rozdzielenie każdego z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="24f15-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="24f15-118">Deklaracja `Variant` typu</span><span class="sxs-lookup"><span data-stu-id="24f15-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="24f15-119">Funkcje, aby wydrukować `Variant` klasy, w zależności od jego "kształt"</span><span class="sxs-lookup"><span data-stu-id="24f15-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="24f15-120">Możliwość dostępu do funkcji drukowania stylem obiektu `.`— Notacja</span><span class="sxs-lookup"><span data-stu-id="24f15-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="24f15-121">Jest to alternatywa do definiowania wszystko jako członka na `Variant`.</span><span class="sxs-lookup"><span data-stu-id="24f15-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="24f15-122">Chociaż nie jest z natury lepszym rozwiązaniem, może być oczyszczarki reprezentacja tych funkcji w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="24f15-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="24f15-123">Rozszerzeń typu wewnętrznego są kompilowane jako elementy członkowskie typu rozszerzania i są wyświetlane w typie, gdy typ jest badany przez odbicie.</span><span class="sxs-lookup"><span data-stu-id="24f15-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="24f15-124">Opcjonalnych rozszerzeń typów</span><span class="sxs-lookup"><span data-stu-id="24f15-124">Optional type extensions</span></span>

<span data-ttu-id="24f15-125">Opcjonalne rozszerzenie typu to rozszerzenie, które pojawia się poza oryginalnym module, przestrzeni nazw lub zestawu typ zostanie przedłużony.</span><span class="sxs-lookup"><span data-stu-id="24f15-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="24f15-126">Opcjonalnych rozszerzeń typów są przydatne do rozszerzania typu, który nie został zdefiniowany samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="24f15-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="24f15-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="24f15-127">For example:</span></span>

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

<span data-ttu-id="24f15-128">Teraz uzyskiwać dostęp do `RepeatElements` tak, jakby jest członkiem <xref:System.Collections.Generic.IEnumerable%601> tak długo, jak `Extensions` modułu jest otwarty w zakresie, w którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="24f15-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="24f15-129">Opcjonalne rozszerzenia nie są wyświetlane w typie rozszerzonym, gdy badany przez odbicie.</span><span class="sxs-lookup"><span data-stu-id="24f15-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="24f15-130">Opcjonalne rozszerzenia muszą być w modułach i są one w zakresie wyłącznie wtedy, gdy moduł, który zawiera rozszerzenie jest otwarty lub jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="24f15-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="24f15-131">Opcjonalne elementy członkowskie rozszerzeń są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazywane niejawnie jako pierwszy parametr.</span><span class="sxs-lookup"><span data-stu-id="24f15-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="24f15-132">Jednak działają one tak, jakby były elementami członkowskimi wystąpień lub elementami statycznymi według tego jak są one zdeklarowane.</span><span class="sxs-lookup"><span data-stu-id="24f15-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="24f15-133">Również opcjonalne elementy członkowskie rozszerzeń nie są widoczne dla C# , czy dla konsumentów VB.</span><span class="sxs-lookup"><span data-stu-id="24f15-133">Optional extension members are also not visible to C# or VB consumers.</span></span> <span data-ttu-id="24f15-134">Mogą być używane tylko w innych F# kodu.</span><span class="sxs-lookup"><span data-stu-id="24f15-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="24f15-135">Ogólne ograniczenia rozszerzeń typu wewnętrzne i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="24f15-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="24f15-136">Istnieje możliwość zadeklarować rozszerzenie typu dla typu ogólnego, gdy zmienna typu jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="24f15-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="24f15-137">Wymagane jest, że ograniczenie deklaracji rozszerzenia pasuje do ograniczenia zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="24f15-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="24f15-138">Jednak nawet wtedy, gdy ograniczenia są dopasowywane między zadeklarowanym typem i rozszerzenie typu, jest możliwe ograniczenie był wywnioskowany przez jednostkę rozszerzonej elementu członkowskiego, która nakłada różnych wymagań dla parametru typu niż zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="24f15-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="24f15-139">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="24f15-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="24f15-140">Nie istnieje sposób, aby otrzymać ten kod, aby pracować z opcjonalne rozszerzenie typu:</span><span class="sxs-lookup"><span data-stu-id="24f15-140">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="24f15-141">Podobnie jak, `Sum` składowa ma różne ograniczenia `'T` (`static member get_Zero` i `static member (+)`) niż określa rozszerzenie typu.</span><span class="sxs-lookup"><span data-stu-id="24f15-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="24f15-142">Modyfikowanie rozszerzenie typu mają ten sam ograniczenie jako `Sum` nie będzie już zgodny zdefiniowane ograniczenia na `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="24f15-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="24f15-143">Zmiana `member this.Sum` do `member inline this.Sum` zapewni błąd niezgodność typu ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="24f15-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="24f15-144">Co to jest pożądane to metody statyczne, "float w miejscu", które może być prezentowana tak, jakby ich one rozszerzanie typu.</span><span class="sxs-lookup"><span data-stu-id="24f15-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="24f15-145">Jest to, gdzie metody rozszerzenia stają się niezbędne.</span><span class="sxs-lookup"><span data-stu-id="24f15-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="24f15-146">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="24f15-146">Extension methods</span></span>

<span data-ttu-id="24f15-147">Na koniec metody rozszerzenia (nazywane czasem "C# stylu elementy członkowskie rozszerzeń") może być zadeklarowana w F# jako metodę statyczną składową klasy.</span><span class="sxs-lookup"><span data-stu-id="24f15-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="24f15-148">Metody rozszerzenia są przydatne w przypadku gdy chcesz zdefiniować rozszerzenia dla typu ogólnego, który będzie ograniczać zmienna typu.</span><span class="sxs-lookup"><span data-stu-id="24f15-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="24f15-149">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="24f15-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="24f15-150">W przypadku tego kodu spowoduje, że będzie wyglądała, jakby `Sum` jest zdefiniowany w <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak `Extensions` został otwarty lub znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="24f15-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="24f15-151">Inne uwagi</span><span class="sxs-lookup"><span data-stu-id="24f15-151">Other remarks</span></span>

<span data-ttu-id="24f15-152">Rozszerzenia typu dostępne są także następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="24f15-152">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="24f15-153">Można rozszerzyć dowolny typ, który jest możliwy.</span><span class="sxs-lookup"><span data-stu-id="24f15-153">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="24f15-154">Rozszerzenia typu wewnętrzne i opcjonalnych można zdefiniować _wszelkie_ typ elementu członkowskiego, nie tylko metody.</span><span class="sxs-lookup"><span data-stu-id="24f15-154">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="24f15-155">Dlatego właściwości rozszerzenia są również możliwe, na przykład.</span><span class="sxs-lookup"><span data-stu-id="24f15-155">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="24f15-156">`self-identifier` Tokenu w [składni](type-extensions.md#syntax) reprezentuje wystąpienie tego typu wywoływany, podobnie jak zwykłych członków.</span><span class="sxs-lookup"><span data-stu-id="24f15-156">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="24f15-157">Rozszerzone członkowie mogą być statyczne lub wystąpieniami elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="24f15-157">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="24f15-158">Zmienne typu rozszerzenia typu musi być zgodna ograniczenia zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="24f15-158">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="24f15-159">Dla typu rozszerzenia dostępne są także następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="24f15-159">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="24f15-160">Typ rozszerzenia nie obsługują wirtualne ani abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="24f15-160">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="24f15-161">Rozszerzenia typu nie obsługują zastąpienie metody jako rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="24f15-161">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="24f15-162">Typ rozszerzenia nie obsługują [statycznie rozwiązywanych parametrach typu](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="24f15-162">Type extensions do not support [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="24f15-163">Opcjonalne rozszerzenia typu nie obsługują konstruktory jako rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="24f15-163">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="24f15-164">Rozszerzenia typu nie może być zdefiniowana w [skróty typów](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="24f15-164">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="24f15-165">Rozszerzenia typu nie są prawidłowe dla `byref<'T>` (chociaż może być deklarowane).</span><span class="sxs-lookup"><span data-stu-id="24f15-165">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="24f15-166">Rozszerzenia typu jest nieprawidłowa dla atrybutów (chociaż może być deklarowane).</span><span class="sxs-lookup"><span data-stu-id="24f15-166">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="24f15-167">Można zdefiniować rozszerzenia, które przeciążać inne metody o tej samej nazwie, ale F# kompilator preferuje metod bez rozszerzeń w przypadku wywołania niejednoznacznego.</span><span class="sxs-lookup"><span data-stu-id="24f15-167">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="24f15-168">Na koniec Jeśli istnieje wiele rozszerzeń typu wewnętrznego dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="24f15-168">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="24f15-169">Dla opcjonalnych rozszerzeń typów elementy członkowskie w innych rozszerzeniach typów tego samego typu mogą mieć tej samej nazwy.</span><span class="sxs-lookup"><span data-stu-id="24f15-169">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="24f15-170">Dwuznaczne błędy występują tylko wtedy, gdy kod klienta otwiera dwa różne zakresy definiujące te same nazwy składników.</span><span class="sxs-lookup"><span data-stu-id="24f15-170">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="24f15-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24f15-171">See also</span></span>

- [<span data-ttu-id="24f15-172">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="24f15-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="24f15-173">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="24f15-173">Members</span></span>](members/index.md)
