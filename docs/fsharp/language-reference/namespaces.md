---
title: Przestrzenie nazw (F#)
description: 'Dowiedz się, jak przestrzeń nazw F # umożliwia organizowanie kodu w obszarach powiązane funkcje, dzięki któremu można dołączyć nazwę do grupowania elementów programu.'
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881892"
---
# <a name="namespaces"></a><span data-ttu-id="1c675-103">Namespaces</span><span class="sxs-lookup"><span data-stu-id="1c675-103">Namespaces</span></span>

<span data-ttu-id="1c675-104">Przestrzeń nazw umożliwia organizowanie kodu w obszarach powiązane funkcje, dzięki któremu można dołączyć nazwę do grupowania elementów programu.</span><span class="sxs-lookup"><span data-stu-id="1c675-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c675-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c675-105">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="1c675-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c675-106">Remarks</span></span>

<span data-ttu-id="1c675-107">Jeśli chcesz umieścić kod w przestrzeni nazw, w pierwszej deklaracji w pliku musi deklarować przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-107">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="1c675-108">Zawartość cały plik stanie się częścią przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-108">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="1c675-109">Przestrzenie nazw nie może bezpośrednio zawierać wartości i funkcje.</span><span class="sxs-lookup"><span data-stu-id="1c675-109">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="1c675-110">Zamiast tego wartości i funkcje, które muszą być zawarte w modułach i moduły są uwzględnione w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-110">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="1c675-111">Przestrzenie nazw może zawierać typy i moduły.</span><span class="sxs-lookup"><span data-stu-id="1c675-111">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="1c675-112">Przestrzenie nazw mogą być deklarowane jawnie za pomocą słowa kluczowego przestrzeni nazw lub niejawnie podczas deklarowania modułu.</span><span class="sxs-lookup"><span data-stu-id="1c675-112">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="1c675-113">Aby jawnie deklarować przestrzeń nazw, należy użyć słowo kluczowe przestrzeni nazw, a następnie według nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-113">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="1c675-114">Poniższy przykład pokazuje plik kodu, który deklaruje przestrzeni nazw elementów widget o typie i moduł zawarty w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-114">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="1c675-115">Jeśli jeden moduł całą zawartość pliku, można również zadeklarować przestrzeni nazw niejawnie przy użyciu `module` — słowo kluczowe i podanie nowej nazwy przestrzeni nazw w module w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="1c675-115">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="1c675-116">W poniższym przykładzie pokazano plik kodu, który deklaruje przestrzeni nazw `Widgets` i modułu `WidgetsModule`, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="1c675-116">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="1c675-117">Poniższy kod jest odpowiednikiem poprzedniego kodu, ale moduł jest deklaracją modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="1c675-117">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="1c675-118">W takim przypadku przestrzeni nazw musi znajdować się w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="1c675-118">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="1c675-119">Jeśli więcej niż jeden moduł jest wymagane w tym samym pliku, w jeden lub kilka przestrzeni nazw, należy użyć deklaracje modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1c675-119">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="1c675-120">Gdy używasz deklaracje modułów lokalnych, nie można używać kwalifikowanych przestrzeni nazw w deklaracjach modułów.</span><span class="sxs-lookup"><span data-stu-id="1c675-120">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="1c675-121">Poniższy kod przedstawia plik, który zawiera deklarację przestrzeni nazw i dwie deklaracje modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1c675-121">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="1c675-122">W tym przypadku moduły znajdują się bezpośrednio w przestrzeni nazw; nie ma żadnych stworzonego moduł, który ma taką samą nazwę jak plik.</span><span class="sxs-lookup"><span data-stu-id="1c675-122">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="1c675-123">Każdy inny kod w pliku, takie jak `do` powiązanie, jest w przestrzeni nazw, ale nie w przypadku wewnętrznych modułów, więc musi kwalifikuj element członkowski modułu `widgetFunction` przy użyciu nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="1c675-123">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="1c675-124">W tym przykładzie dane wyjściowe wyglądają następująco.</span><span class="sxs-lookup"><span data-stu-id="1c675-124">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="1c675-125">Aby uzyskać więcej informacji, zobacz [modułów](modules.md).</span><span class="sxs-lookup"><span data-stu-id="1c675-125">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="1c675-126">Zagnieżdżone przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="1c675-126">Nested Namespaces</span></span>

<span data-ttu-id="1c675-127">Kiedy tworzysz zagnieżdżone przestrzenie nazw, możesz je pełnej kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="1c675-127">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="1c675-128">W przeciwnym razie możesz utworzyć nową przestrzeń nazw najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="1c675-128">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="1c675-129">Wcięcie jest ignorowany w deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-129">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="1c675-130">Poniższy przykład pokazuje sposób deklarowania zagnieżdżone przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-130">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="1c675-131">Przestrzenie nazw plików i zestawów</span><span class="sxs-lookup"><span data-stu-id="1c675-131">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="1c675-132">Przestrzenie nazw może obejmować wiele plików w jednym projekcie lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1c675-132">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="1c675-133">Termin *przestrzeni nazw fragmentu* opisuje część przestrzeni nazw, który znajduje się w jednym pliku.</span><span class="sxs-lookup"><span data-stu-id="1c675-133">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="1c675-134">Przestrzenie nazw mogą obejmować wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="1c675-134">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="1c675-135">Na przykład `System` przestrzeń nazw zawiera całe .NET Framework, który obejmuje wiele zestawów i zawiera wiele zagnieżdżone przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-135">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="1c675-136">Globalne Namespace</span><span class="sxs-lookup"><span data-stu-id="1c675-136">Global Namespace</span></span>

<span data-ttu-id="1c675-137">Użyj wstępnie zdefiniowanych nazw `global` umieszczenie nazwy w przestrzeni nazw .NET najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="1c675-137">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="1c675-138">Umożliwia także globalne k odkazu .NET przestrzeń nazw najwyższego poziomu, na przykład, aby rozwiązać konflikty nazw z innych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-138">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="1c675-139">Przestrzenie nazw cykliczne</span><span class="sxs-lookup"><span data-stu-id="1c675-139">Recursive namespaces</span></span>

<span data-ttu-id="1c675-140">F # 4.1 wprowadzono pojęcie przestrzenie nazw, która zezwala na wszystkie zawarte kodu wzajemnie się być typem rekursywnym.</span><span class="sxs-lookup"><span data-stu-id="1c675-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="1c675-141">Odbywa się za pośrednictwem `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="1c675-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="1c675-142">Korzystanie z `namespace rec` mogą złagodzić ich niektóre problemy, które nie jest możliwość pisania kodu wzajemnie referencyjne typy i moduły.</span><span class="sxs-lookup"><span data-stu-id="1c675-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="1c675-143">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="1c675-143">The following is an example of this:</span></span>

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

<span data-ttu-id="1c675-144">Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="1c675-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="1c675-145">Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.</span><span class="sxs-lookup"><span data-stu-id="1c675-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="1c675-146">To nie jest możliwe do wyrażenia w języku F #, jeśli usunięto `rec` słowo kluczowe z `MutualReferences` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c675-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="1c675-147">Ta funkcja jest również dostępna dla najwyższego poziomu [modułów](modules.md) w F # 4.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="1c675-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c675-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c675-148">See also</span></span>

- [<span data-ttu-id="1c675-149">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="1c675-149">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1c675-150">Moduły</span><span class="sxs-lookup"><span data-stu-id="1c675-150">Modules</span></span>](modules.md)
- [<span data-ttu-id="1c675-151">F # RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły za pośrednictwem szerszego zakresu w plikach</span><span class="sxs-lookup"><span data-stu-id="1c675-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
