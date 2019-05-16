---
title: Namespaces
description: Dowiedz się, jak F# przestrzeń nazw umożliwia organizowanie kodu w obszarach powiązane funkcje, dzięki któremu można dołączyć nazwę do grupowania elementów programu.
ms.date: 12/08/2018
ms.openlocfilehash: b315d654dad0d36e3584564ad027c68fb3c94cce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645272"
---
# <a name="namespaces"></a><span data-ttu-id="56044-103">Namespaces</span><span class="sxs-lookup"><span data-stu-id="56044-103">Namespaces</span></span>

<span data-ttu-id="56044-104">Przestrzeń nazw umożliwia organizowanie kodu w obszarach powiązane funkcje, dzięki któremu można dołączyć nazwę grupie F# program elementów.</span><span class="sxs-lookup"><span data-stu-id="56044-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="56044-105">Przestrzenie nazw są zazwyczaj najwyższego poziomu elementów w F# plików.</span><span class="sxs-lookup"><span data-stu-id="56044-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="56044-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="56044-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="56044-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56044-107">Remarks</span></span>

<span data-ttu-id="56044-108">Jeśli chcesz umieścić kod w przestrzeni nazw, w pierwszej deklaracji w pliku musi deklarować przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="56044-109">Zawartość cały plik stają się częścią przestrzeni nazw, pod warunkiem istnieje żadna deklaracja przestrzeni nazw bardziej szczegółowo w pliku.</span><span class="sxs-lookup"><span data-stu-id="56044-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="56044-110">Jeśli tak jest rzeczywiście, cały kod, aż do następnego deklaracji przestrzeni nazw jest traktowany jako mieścić się w pierwszej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="56044-111">Przestrzenie nazw nie może bezpośrednio zawierać wartości i funkcje.</span><span class="sxs-lookup"><span data-stu-id="56044-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="56044-112">Zamiast tego wartości i funkcje, które muszą być zawarte w modułach i moduły są uwzględnione w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="56044-113">Przestrzenie nazw może zawierać typy i moduły.</span><span class="sxs-lookup"><span data-stu-id="56044-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="56044-114">Komentarze dokumentacji XML mogą być deklarowane powyżej przestrzeni nazw, ale są one ignorowane.</span><span class="sxs-lookup"><span data-stu-id="56044-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="56044-115">Dyrektywy kompilatora mogą być także zadeklarowane powyżej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="56044-116">Przestrzenie nazw mogą być deklarowane jawnie za pomocą słowa kluczowego przestrzeni nazw lub niejawnie podczas deklarowania modułu.</span><span class="sxs-lookup"><span data-stu-id="56044-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="56044-117">Aby jawnie deklarować przestrzeń nazw, należy użyć słowo kluczowe przestrzeni nazw, a następnie według nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="56044-118">W poniższym przykładzie pokazano plik kodu, który deklaruje przestrzeni nazw `Widgets` o typie i moduł zawarty w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="56044-119">Jeśli jeden moduł całą zawartość pliku, można również zadeklarować przestrzeni nazw niejawnie przy użyciu `module` — słowo kluczowe i podanie nowej nazwy przestrzeni nazw w module w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="56044-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="56044-120">W poniższym przykładzie pokazano plik kodu, który deklaruje przestrzeni nazw `Widgets` i modułu `WidgetsModule`, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="56044-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="56044-121">Poniższy kod jest odpowiednikiem poprzedniego kodu, ale moduł jest deklaracją modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="56044-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="56044-122">W takim przypadku przestrzeni nazw musi znajdować się w osobnym wierszu.</span><span class="sxs-lookup"><span data-stu-id="56044-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="56044-123">Jeśli więcej niż jeden moduł jest wymagane w tym samym pliku, w jeden lub kilka przestrzeni nazw, należy użyć deklaracje modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="56044-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="56044-124">Gdy używasz deklaracje modułów lokalnych, nie można używać kwalifikowanych przestrzeni nazw w deklaracjach modułów.</span><span class="sxs-lookup"><span data-stu-id="56044-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="56044-125">Poniższy kod przedstawia plik, który zawiera deklarację przestrzeni nazw i dwie deklaracje modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="56044-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="56044-126">W tym przypadku moduły znajdują się bezpośrednio w przestrzeni nazw; nie ma żadnych stworzonego moduł, który ma taką samą nazwę jak plik.</span><span class="sxs-lookup"><span data-stu-id="56044-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="56044-127">Każdy inny kod w pliku, takie jak `do` powiązanie, jest w przestrzeni nazw, ale nie w przypadku wewnętrznych modułów, więc musi kwalifikuj element członkowski modułu `widgetFunction` przy użyciu nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="56044-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="56044-128">W tym przykładzie dane wyjściowe wyglądają następująco.</span><span class="sxs-lookup"><span data-stu-id="56044-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="56044-129">Aby uzyskać więcej informacji, zobacz [modułów](modules.md).</span><span class="sxs-lookup"><span data-stu-id="56044-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="56044-130">Zagnieżdżone przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="56044-130">Nested Namespaces</span></span>

<span data-ttu-id="56044-131">Kiedy tworzysz zagnieżdżone przestrzenie nazw, możesz je pełnej kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="56044-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="56044-132">W przeciwnym razie możesz utworzyć nową przestrzeń nazw najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="56044-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="56044-133">Wcięcie jest ignorowany w deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="56044-134">Poniższy przykład pokazuje sposób deklarowania zagnieżdżone przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="56044-135">Przestrzenie nazw plików i zestawów</span><span class="sxs-lookup"><span data-stu-id="56044-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="56044-136">Przestrzenie nazw może obejmować wiele plików w jednym projekcie lub kompilacji.</span><span class="sxs-lookup"><span data-stu-id="56044-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="56044-137">Termin *przestrzeni nazw fragmentu* opisuje część przestrzeni nazw, który znajduje się w jednym pliku.</span><span class="sxs-lookup"><span data-stu-id="56044-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="56044-138">Przestrzenie nazw mogą obejmować wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="56044-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="56044-139">Na przykład `System` przestrzeń nazw zawiera całe .NET Framework, który obejmuje wiele zestawów i zawiera wiele zagnieżdżone przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="56044-140">Globalne Namespace</span><span class="sxs-lookup"><span data-stu-id="56044-140">Global Namespace</span></span>

<span data-ttu-id="56044-141">Użyj wstępnie zdefiniowanych nazw `global` umieszczenie nazwy w przestrzeni nazw .NET najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="56044-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="56044-142">Umożliwia także globalne k odkazu .NET przestrzeń nazw najwyższego poziomu, na przykład, aby rozwiązać konflikty nazw z innych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="56044-143">Przestrzenie nazw cykliczne</span><span class="sxs-lookup"><span data-stu-id="56044-143">Recursive namespaces</span></span>

<span data-ttu-id="56044-144">Przestrzenie nazw mogą być także zadeklarowane jako cykliczne do obsługi całego kodu zawarte jako wzajemnie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="56044-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="56044-145">Odbywa się za pośrednictwem `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="56044-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="56044-146">Korzystanie z `namespace rec` mogą złagodzić ich niektóre problemy, które nie jest możliwość pisania kodu wzajemnie referencyjne typy i moduły.</span><span class="sxs-lookup"><span data-stu-id="56044-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="56044-147">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="56044-147">The following is an example of this:</span></span>

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

<span data-ttu-id="56044-148">Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="56044-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="56044-149">Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.</span><span class="sxs-lookup"><span data-stu-id="56044-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="56044-150">W takich sytuacjach przydałaby to wyrazić w F# usunięto `rec` słowo kluczowe z `MutualReferences` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56044-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="56044-151">Ta funkcja jest również dostępna dla najwyższego poziomu [modułów](modules.md).</span><span class="sxs-lookup"><span data-stu-id="56044-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56044-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56044-152">See also</span></span>

- [<span data-ttu-id="56044-153">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="56044-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="56044-154">Moduły</span><span class="sxs-lookup"><span data-stu-id="56044-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="56044-155">F#RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły za pośrednictwem szerszego zakresu w plikach</span><span class="sxs-lookup"><span data-stu-id="56044-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
