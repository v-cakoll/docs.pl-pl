---
title: Namespaces
description: Dowiedz się F# , jak przestrzeń nazw umożliwia organizowanie kodu w obszary powiązanej funkcjonalności przez umożliwienie dołączenia nazwy do grupy elementów programu.
ms.date: 12/08/2018
ms.openlocfilehash: a55da1592b04c64576b4c66de61b5ca137289a6f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425044"
---
# <a name="namespaces"></a><span data-ttu-id="8cfeb-103">Namespaces</span><span class="sxs-lookup"><span data-stu-id="8cfeb-103">Namespaces</span></span>

<span data-ttu-id="8cfeb-104">Przestrzeń nazw umożliwia organizowanie kodu w obszary powiązanej funkcjonalności przez umożliwienie dołączenia nazwy do grupy elementów F# programu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="8cfeb-105">Przestrzenie nazw są zwykle elementami najwyższego poziomu w F# plikach.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cfeb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cfeb-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="8cfeb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cfeb-107">Remarks</span></span>

<span data-ttu-id="8cfeb-108">Jeśli chcesz umieścić kod w przestrzeni nazw, pierwsza deklaracja w pliku musi deklarować przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="8cfeb-109">Zawartość całego pliku staje się częścią przestrzeni nazw, pod warunkiem, że w pliku nie istnieją dalsze deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="8cfeb-110">Jeśli tak, to cały kod, aż do następnej deklaracji przestrzeni nazw jest uznawany za znajdujący się w obrębie pierwszej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="8cfeb-111">Przestrzenie nazw nie mogą bezpośrednio zawierać wartości i funkcji.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="8cfeb-112">Zamiast tego, wartości i funkcje muszą być zawarte w modułach, a moduły są zawarte w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="8cfeb-113">Przestrzenie nazw mogą zawierać typy, moduły.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="8cfeb-114">Komentarze dokumentacji XML można zadeklarować powyżej przestrzeni nazw, ale są one ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="8cfeb-115">Dyrektywy kompilatora można również deklarować powyżej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="8cfeb-116">Przestrzenie nazw można jawnie zadeklarować za pomocą słowa kluczowego Namespace lub niejawnie podczas deklarowania modułu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="8cfeb-117">Aby jawnie zadeklarować przestrzeń nazw, użyj słowa kluczowego Namespace, po którym następuje nazwa przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="8cfeb-118">W poniższym przykładzie przedstawiono plik kodu, który deklaruje przestrzeń nazw `Widgets` z typem i modułem zawartym w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="8cfeb-119">Jeśli cała zawartość pliku znajduje się w jednym module, można także zadeklarować przestrzenie nazw niejawnie za pomocą słowa kluczowego `module` i podać nową nazwę przestrzeni nazw w w pełni kwalifikowanej nazwie modułu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="8cfeb-120">W poniższym przykładzie przedstawiono plik kodu, który deklaruje przestrzeń nazw `Widgets` i `WidgetsModule`modułu, który zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="8cfeb-121">Poniższy kod jest równoważny poprzedzającemu kod, ale moduł jest deklaracją modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="8cfeb-122">W takim przypadku przestrzeń nazw musi znajdować się w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="8cfeb-123">Jeśli więcej niż jeden moduł jest wymagany w tym samym pliku w co najmniej jednym obszarze nazw, należy użyć lokalnych deklaracji modułu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="8cfeb-124">W przypadku korzystania z deklaracji modułu lokalnego nie można użyć kwalifikowanej przestrzeni nazw w deklaracjach modułów.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="8cfeb-125">Poniższy kod przedstawia plik, który zawiera deklarację przestrzeni nazw i dwie deklaracje modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="8cfeb-126">W takim przypadku moduły są zawarte bezpośrednio w przestrzeni nazw; nie utworzono niejawnie modułu, który ma taką samą nazwę jak plik.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="8cfeb-127">Każdy inny kod w pliku, taki jak powiązanie `do`, znajduje się w przestrzeni nazw, ale nie w modułach wewnętrznych, dlatego należy zakwalifikować element członkowski modułu `widgetFunction` przy użyciu nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="8cfeb-128">Dane wyjściowe tego przykładu są następujące.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="8cfeb-129">Aby uzyskać więcej informacji, zobacz [moduły](modules.md).</span><span class="sxs-lookup"><span data-stu-id="8cfeb-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="8cfeb-130">Zagnieżdżone przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="8cfeb-130">Nested Namespaces</span></span>

<span data-ttu-id="8cfeb-131">Gdy tworzysz zagnieżdżoną przestrzeń nazw, musisz ją w pełni zakwalifikować.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="8cfeb-132">W przeciwnym razie utworzysz nową przestrzeń nazw najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="8cfeb-133">Wcięcie jest ignorowane w deklaracjach przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="8cfeb-134">Poniższy przykład pokazuje, jak zadeklarować zagnieżdżoną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="8cfeb-135">Przestrzenie nazw w plikach i zestawach</span><span class="sxs-lookup"><span data-stu-id="8cfeb-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="8cfeb-136">Przestrzenie nazw mogą obejmować wiele plików w jednym projekcie lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="8cfeb-137">*Fragment przestrzeni nazw* zawiera opis części przestrzeni nazw, która jest uwzględniona w jednym pliku.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="8cfeb-138">Przestrzenie nazw mogą również obejmować wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="8cfeb-139">Na przykład przestrzeń nazw `System` zawiera cały .NET Framework, która obejmuje wiele zestawów i zawiera wiele zagnieżdżonych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="8cfeb-140">Globalna przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="8cfeb-140">Global Namespace</span></span>

<span data-ttu-id="8cfeb-141">Aby umieścić nazwy w przestrzeni nazw najwyższego poziomu platformy .NET, należy użyć wstępnie zdefiniowanej przestrzeni nazw `global`.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="8cfeb-142">Można również użyć globalnego do odwoływania się do przestrzeni nazw platformy .NET najwyższego poziomu, na przykład w celu rozwiązania konfliktów nazw z innymi przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="8cfeb-143">Cykliczne przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="8cfeb-143">Recursive namespaces</span></span>

<span data-ttu-id="8cfeb-144">Przestrzenie nazw można także zadeklarować jako cykliczne, aby umożliwić wzajemną rekursywnie wszystkie zawarte w nim kod.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="8cfeb-145">Odbywa się to za pośrednictwem `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="8cfeb-146">Użycie `namespace rec` może wyeliminować problemy, ponieważ nie można napisać wzajemnie referencyjnego kodu między typami i modułami.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="8cfeb-147">Poniżej znajduje się przykład:</span><span class="sxs-lookup"><span data-stu-id="8cfeb-147">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up ->
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="8cfeb-148">Należy zauważyć, że wyjątek `DontSqueezeTheBananaException` i Klasa `Banana` obie odwołują się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="8cfeb-149">Ponadto moduł `BananaHelpers` i Klasa `Banana` również odwołują się do siebie.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="8cfeb-150">Nie będzie można go wyrazić w F# przypadku usunięcia słowa kluczowego `rec` z przestrzeni nazw `MutualReferences`.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="8cfeb-151">Ta funkcja jest również dostępna dla [modułów](modules.md)najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8cfeb-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cfeb-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cfeb-152">See also</span></span>

- [<span data-ttu-id="8cfeb-153">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="8cfeb-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8cfeb-154">Moduły</span><span class="sxs-lookup"><span data-stu-id="8cfeb-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="8cfeb-155">F#RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły dla większych zakresów w plikach</span><span class="sxs-lookup"><span data-stu-id="8cfeb-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
