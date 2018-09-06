---
title: Rozszerzenia typu (F#)
description: 'Dowiedz się, jak rozszerzeń typu F # zezwala na dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej.'
ms.date: 07/20/2018
ms.openlocfilehash: 27238db1fd0803f62c32755fbc4ab7688f5c107e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874982"
---
# <a name="type-extensions"></a><span data-ttu-id="e5406-103">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="e5406-103">Type extensions</span></span>

<span data-ttu-id="e5406-104">Rozszerzenia typu (nazywane również _rozszerzeniach_) to rodzina funkcji, które pozwalają na dodawanie nowych członków do typu obiektu zdefiniowanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e5406-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="e5406-105">Są trzy funkcje:</span><span class="sxs-lookup"><span data-stu-id="e5406-105">The three features are:</span></span>

* <span data-ttu-id="e5406-106">Rozszerzeń typu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="e5406-106">Intrinsic type extensions</span></span>
* <span data-ttu-id="e5406-107">Opcjonalnych rozszerzeń typów</span><span class="sxs-lookup"><span data-stu-id="e5406-107">Optional type extensions</span></span>
* <span data-ttu-id="e5406-108">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="e5406-108">Extension methods</span></span>

<span data-ttu-id="e5406-109">Każda mogą być używane w różnych scenariuszach i zawiera różne kompromisy.</span><span class="sxs-lookup"><span data-stu-id="e5406-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5406-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5406-110">Syntax</span></span>

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

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="e5406-111">Rozszerzeń typu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="e5406-111">Intrinsic type extensions</span></span>

<span data-ttu-id="e5406-112">Rozszerzenie typu wewnętrznego jest rozszerzeniem typu, która rozszerza typ zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5406-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="e5406-113">Rozszerzeń typu wewnętrznego musi być zdefiniowany w tym samym pliku **i** w tej samej przestrzeni nazw lub module jako typ, są one rozszerzanie.</span><span class="sxs-lookup"><span data-stu-id="e5406-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="e5406-114">Inne definicji spowoduje ich trwa [opcjonalnych rozszerzeń typów](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="e5406-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="e5406-115">Rozszerzeń typu wewnętrznego są czasami bardziej przejrzysty sposób oddzielić funkcje od deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="e5406-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="e5406-116">Poniższy przykład pokazuje jak zdefiniować rozszerzenie typu wewnętrznego:</span><span class="sxs-lookup"><span data-stu-id="e5406-116">The following example shows how to define an intrinsic type extension:</span></span>

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

<span data-ttu-id="e5406-117">Przy użyciu rozszerzenia typu umożliwia rozdzielenie każdego z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e5406-117">Using a type extension allows you to separate each of the following:</span></span>

* <span data-ttu-id="e5406-118">Deklaracja `Variant` typu</span><span class="sxs-lookup"><span data-stu-id="e5406-118">The declaration of a `Variant` type</span></span>
* <span data-ttu-id="e5406-119">Funkcje, aby wydrukować `Variant` klasy, w zależności od jego "kształt"</span><span class="sxs-lookup"><span data-stu-id="e5406-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
* <span data-ttu-id="e5406-120">Możliwość dostępu do funkcji drukowania stylem obiektu `.`— Notacja</span><span class="sxs-lookup"><span data-stu-id="e5406-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="e5406-121">Jest to alternatywa do definiowania wszystko jako członka na `Variant`.</span><span class="sxs-lookup"><span data-stu-id="e5406-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="e5406-122">Chociaż nie jest z natury lepszym rozwiązaniem, może być oczyszczarki reprezentacja tych funkcji w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="e5406-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="e5406-123">Rozszerzeń typu wewnętrznego są kompilowane jako elementy członkowskie typu rozszerzania i są wyświetlane w typie, gdy typ jest badany przez odbicie.</span><span class="sxs-lookup"><span data-stu-id="e5406-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="e5406-124">Opcjonalnych rozszerzeń typów</span><span class="sxs-lookup"><span data-stu-id="e5406-124">Optional type extensions</span></span>

<span data-ttu-id="e5406-125">Opcjonalne rozszerzenie typu to rozszerzenie, które pojawia się poza oryginalnym module, przestrzeni nazw lub zestawu typ zostanie przedłużony.</span><span class="sxs-lookup"><span data-stu-id="e5406-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="e5406-126">Opcjonalnych rozszerzeń typów są przydatne do rozszerzania typu, który nie został zdefiniowany samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="e5406-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="e5406-127">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e5406-127">For example:</span></span>

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

<span data-ttu-id="e5406-128">Teraz uzyskiwać dostęp do `RepeatElements` tak, jakby jest członkiem <xref:System.Collections.Generic.IEnumerable%601> tak długo, jak `Extensions` modułu jest otwarty w zakresie, w którym pracujesz.</span><span class="sxs-lookup"><span data-stu-id="e5406-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="e5406-129">Opcjonalne rozszerzenia nie są wyświetlane w typie rozszerzonym, gdy badany przez odbicie.</span><span class="sxs-lookup"><span data-stu-id="e5406-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="e5406-130">Opcjonalne rozszerzenia muszą być w modułach i są one w zakresie wyłącznie wtedy, gdy moduł, który zawiera rozszerzenie jest otwarty lub jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="e5406-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="e5406-131">Opcjonalne elementy członkowskie rozszerzeń są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazywane niejawnie jako pierwszy parametr.</span><span class="sxs-lookup"><span data-stu-id="e5406-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="e5406-132">Jednak działają one tak, jakby były elementami członkowskimi wystąpień lub elementami statycznymi według tego jak są one zdeklarowane.</span><span class="sxs-lookup"><span data-stu-id="e5406-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="e5406-133">Ogólne ograniczenia rozszerzeń typu wewnętrzne i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e5406-133">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="e5406-134">Istnieje możliwość zadeklarować rozszerzenie typu dla typu ogólnego, gdy zmienna typu jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="e5406-134">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="e5406-135">Wymagane jest, że ograniczenie deklaracji rozszerzenia pasuje do ograniczenia zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="e5406-135">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="e5406-136">Jednak nawet wtedy, gdy ograniczenia są dopasowywane między zadeklarowanym typem i rozszerzenie typu, jest możliwe ograniczenie był wywnioskowany przez jednostkę rozszerzonej elementu członkowskiego, która nakłada różnych wymagań dla parametru typu niż zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="e5406-136">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="e5406-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e5406-137">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="e5406-138">Nie istnieje sposób, aby otrzymać ten kod, aby pracować z opcjonalne rozszerzenie typu:</span><span class="sxs-lookup"><span data-stu-id="e5406-138">There is no way to get this code to work with an optional type extension:</span></span>

* <span data-ttu-id="e5406-139">Podobnie jak, `Sum` składowa ma różne ograniczenia `'T` (`static member get_Zero` i `static member (+)`) niż określa rozszerzenie typu.</span><span class="sxs-lookup"><span data-stu-id="e5406-139">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
* <span data-ttu-id="e5406-140">Modyfikowanie rozszerzenie typu mają ten sam ograniczenie jako `Sum` nie będzie już zgodny zdefiniowane ograniczenia na `IEnumerable<'T>`.</span><span class="sxs-lookup"><span data-stu-id="e5406-140">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
* <span data-ttu-id="e5406-141">Tworzenie, zmienianie członka do `member inline Sum` zapewni błąd niezgodność ograniczenia typu</span><span class="sxs-lookup"><span data-stu-id="e5406-141">Making changing the member to `member inline Sum` will give an error that type constraints are mismatched</span></span>

<span data-ttu-id="e5406-142">Co to jest pożądane to metody statyczne, "float w miejscu", które może być prezentowana tak, jakby ich one rozszerzanie typu.</span><span class="sxs-lookup"><span data-stu-id="e5406-142">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="e5406-143">Jest to, gdzie metody rozszerzenia stają się niezbędne.</span><span class="sxs-lookup"><span data-stu-id="e5406-143">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="e5406-144">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="e5406-144">Extension methods</span></span>

<span data-ttu-id="e5406-145">Na koniec metody rozszerzenia (nazywane czasem "C# styl elementy członkowskie rozszerzeń") może być zadeklarowana w F # jako metodę statyczną składową klasy.</span><span class="sxs-lookup"><span data-stu-id="e5406-145">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="e5406-146">Metody rozszerzenia są przydatne w przypadku gdy chcesz zdefiniować rozszerzenia dla typu ogólnego, który będzie ograniczać zmienna typu.</span><span class="sxs-lookup"><span data-stu-id="e5406-146">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="e5406-147">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e5406-147">For example:</span></span>

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="e5406-148">W przypadku tego kodu spowoduje, że będzie wyglądała, jakby `Sum` jest zdefiniowany w <xref:System.Collections.Generic.IEnumerable%601>, tak długo, jak `Extensions` został otwarty lub znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="e5406-148">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

## <a name="other-remarks"></a><span data-ttu-id="e5406-149">Inne uwagi</span><span class="sxs-lookup"><span data-stu-id="e5406-149">Other remarks</span></span>

<span data-ttu-id="e5406-150">Rozszerzenia typu dostępne są także następujące atrybuty:</span><span class="sxs-lookup"><span data-stu-id="e5406-150">Type extensions also have the following attributes:</span></span>

* <span data-ttu-id="e5406-151">Można rozszerzyć dowolny typ, który jest możliwy.</span><span class="sxs-lookup"><span data-stu-id="e5406-151">Any type that can be accessed can be extended.</span></span>
* <span data-ttu-id="e5406-152">Rozszerzenia typu wewnętrzne i opcjonalnych można zdefiniować _wszelkie_ typ elementu członkowskiego, nie tylko metody.</span><span class="sxs-lookup"><span data-stu-id="e5406-152">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="e5406-153">Dlatego właściwości rozszerzenia są również możliwe, na przykład.</span><span class="sxs-lookup"><span data-stu-id="e5406-153">So extension properties are also possible, for example.</span></span>
* <span data-ttu-id="e5406-154">`self-identifier` Tokenu w [składni](type-extensions.md#syntax) reprezentuje wystąpienie tego typu wywoływany, podobnie jak zwykłych członków.</span><span class="sxs-lookup"><span data-stu-id="e5406-154">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
* <span data-ttu-id="e5406-155">Rozszerzone członkowie mogą być statyczne lub wystąpieniami elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="e5406-155">Extended members can be static or instance members.</span></span>
* <span data-ttu-id="e5406-156">Zmienne typu rozszerzenia typu musi być zgodna ograniczenia zadeklarowanym typem.</span><span class="sxs-lookup"><span data-stu-id="e5406-156">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="e5406-157">Dla typu rozszerzenia dostępne są także następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="e5406-157">The following limitations also exist for type extensions:</span></span>

* <span data-ttu-id="e5406-158">Typ rozszerzenia nie obsługują wirtualne ani abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="e5406-158">Type extensions do not support virtual or abstract methods.</span></span>
* <span data-ttu-id="e5406-159">Rozszerzenia typu nie obsługują zastąpienie metody jako rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e5406-159">Type extensions do not support override methods as augmentations.</span></span>
* <span data-ttu-id="e5406-160">Typ rozszerzenia nie obsługują [statycznie rozwiązywanych parametrach typu](generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5406-160">Type extensions do not support [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>
* <span data-ttu-id="e5406-161">Opcjonalne rozszerzenia typu nie obsługują konstruktory jako rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e5406-161">Optional Type extensions do not support constructors as augmentations.</span></span>
* <span data-ttu-id="e5406-162">Rozszerzenia typu nie może być zdefiniowana w [skróty typów](type-abbreviations.md).</span><span class="sxs-lookup"><span data-stu-id="e5406-162">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
* <span data-ttu-id="e5406-163">Rozszerzenia typu nie są prawidłowe dla `byref<'T>` (chociaż może być deklarowane).</span><span class="sxs-lookup"><span data-stu-id="e5406-163">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
* <span data-ttu-id="e5406-164">Rozszerzenia typu jest nieprawidłowa dla atrybutów (chociaż może być deklarowane).</span><span class="sxs-lookup"><span data-stu-id="e5406-164">Type extensions are not valid for attributes (though they can be declared).</span></span>
* <span data-ttu-id="e5406-165">Można zdefiniować rozszerzenia, które przeciążać inne metody o tej samej nazwie, ale kompilator F # preferuje metod bez rozszerzeń w przypadku wywołania niejednoznacznego.</span><span class="sxs-lookup"><span data-stu-id="e5406-165">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="e5406-166">Na koniec Jeśli istnieje wiele rozszerzeń typu wewnętrznego dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="e5406-166">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="e5406-167">Dla opcjonalnych rozszerzeń typów elementy członkowskie w innych rozszerzeniach typów tego samego typu mogą mieć tej samej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e5406-167">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="e5406-168">Dwuznaczne błędy występują tylko wtedy, gdy kod klienta otwiera dwa różne zakresy definiujące te same nazwy składników.</span><span class="sxs-lookup"><span data-stu-id="e5406-168">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5406-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5406-169">See also</span></span>

- [<span data-ttu-id="e5406-170">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e5406-170">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e5406-171">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e5406-171">Members</span></span>](members/index.md)
