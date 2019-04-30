---
title: Moduły
description: Dowiedz się, jak F# moduł to grupa F# możesz pisać kod, takie jak wartości, typy i wartości funkcji w F# program.
ms.date: 04/24/2017
ms.openlocfilehash: 9e5bef4ffe3301a69bbe32483625652d988f8a35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666321"
---
# <a name="modules"></a><span data-ttu-id="49242-103">Moduły</span><span class="sxs-lookup"><span data-stu-id="49242-103">Modules</span></span>

<span data-ttu-id="49242-104">W kontekście F# języka, *modułu* to grupa F# możesz pisać kod, takie jak wartości, typy i wartości funkcji w F# program.</span><span class="sxs-lookup"><span data-stu-id="49242-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="49242-105">Grupowanie kodu w modułach pomaga zachować kod pokrewny ze sobą oraz uniknąć konfliktów nazw w programie.</span><span class="sxs-lookup"><span data-stu-id="49242-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="49242-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="49242-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="49242-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49242-107">Remarks</span></span>

<span data-ttu-id="49242-108">F# Moduł to grupa F# konstrukcje kodu, takich jak typy wartości, wartości funkcji i kodu w `do` powiązania.</span><span class="sxs-lookup"><span data-stu-id="49242-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="49242-109">Są one zaimplementowane jako wspólnej klasy środowiska uruchomieniowego (języka wspólnego CLR) języka, która ma tylko statyczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="49242-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="49242-110">Istnieją dwa typy deklaracje modułów, w zależności od tego, czy cały plik znajduje się w module: deklaracji najwyższego poziomu modułu i deklaracja modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="49242-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="49242-111">Deklaracji najwyższego poziomu modułu obejmuje cały plik w module.</span><span class="sxs-lookup"><span data-stu-id="49242-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="49242-112">Deklaracji najwyższego poziomu modułu może znajdować się tylko jako pierwszej deklaracji w pliku.</span><span class="sxs-lookup"><span data-stu-id="49242-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="49242-113">W składni deklaracji najwyższego poziomu modułu opcjonalnego *kwalifikowaną przestrzeń nazw* jest sekwencji nazwy zagnieżdżone przestrzenie nazw, która zawiera moduł.</span><span class="sxs-lookup"><span data-stu-id="49242-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="49242-114">Kwalifikowanych przestrzeni nazw ma być uprzednio zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="49242-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="49242-115">Nie masz Wcięcie Deklaracje w module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="49242-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="49242-116">Masz wcięcie wszystkie deklaracje modułów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="49242-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="49242-117">W module lokalnym deklaracji deklaracje, które tworzone jest wcięcie w obszarze deklaracja modułu są częścią tego modułu.</span><span class="sxs-lookup"><span data-stu-id="49242-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="49242-118">Plik kodu nie zaczyna się od deklaracji najwyższego poziomu modułu lub deklaracja przestrzeni nazw, całą zawartość pliku, w tym wszystkie moduły lokalne staje się częścią stworzonego modułu najwyższego poziomu, który ma taką samą nazwę jak plik, bez rozszerzenia i przy użyciu pierwszej litery na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="49242-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="49242-119">Na przykład rozważmy następujący plik.</span><span class="sxs-lookup"><span data-stu-id="49242-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="49242-120">Ten plik będzie można skompilować tak, jakby zostały napisane w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="49242-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="49242-121">Jeśli masz wiele modułów w pliku dla każdego modułu, należy użyć deklaracji modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="49242-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="49242-122">Jeśli zadeklarowano otaczającej przestrzeni nazw, moduły są częścią otaczającej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="49242-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="49242-123">Jeśli otaczającej przestrzeni nazw nie jest zadeklarowana, moduły stają się częścią stworzonego najwyższego poziomu modułu.</span><span class="sxs-lookup"><span data-stu-id="49242-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="49242-124">Poniższy przykład kodu pokazuje pliku z kodem, który zawiera wiele modułów.</span><span class="sxs-lookup"><span data-stu-id="49242-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="49242-125">Kompilator niejawnie tworzy moduł najwyższego poziomu o nazwie `Multiplemodules`, i `MyModule1` i `MyModule2` są zagnieżdżone w module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="49242-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="49242-126">Jeśli masz wiele plików w projekcie lub w pojedynczej kompilacji lub jeśli tworzysz biblioteki, musi zawierać deklaracji przestrzeni nazw lub module deklaracji w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="49242-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="49242-127">F# Kompilator określa tylko nazwy modułu niejawnie istnieje tylko jeden plik w wierszu polecenia kompilacji lub projektu, gdy tworzysz aplikację.</span><span class="sxs-lookup"><span data-stu-id="49242-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="49242-128">*Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="49242-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="49242-129">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="49242-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="49242-130">Wartość domyślna jest publiczny.</span><span class="sxs-lookup"><span data-stu-id="49242-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="49242-131">Odwoływanie się do kodu w modułach</span><span class="sxs-lookup"><span data-stu-id="49242-131">Referencing Code in Modules</span></span>

<span data-ttu-id="49242-132">Gdy odwołujesz się funkcje, typy i wartości z innego modułu, należy użyć kwalifikowanej nazwy lub otworzyć modułu.</span><span class="sxs-lookup"><span data-stu-id="49242-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="49242-133">Jeśli używasz nazwy kwalifikowanej, należy określić przestrzenie nazw, moduł i identyfikator elementu programu, który ma.</span><span class="sxs-lookup"><span data-stu-id="49242-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="49242-134">Możesz oddzielić każda część kwalifikowana ścieżka pojedynczego znaku kropki (.), w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="49242-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="49242-135">Można otworzyć moduł lub przynajmniej jednej przestrzeni nazw w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="49242-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="49242-136">Aby uzyskać więcej informacji na temat modułów i przestrzeni nazw otwierania zobacz [deklaracje importowania: `open` — Słowo kluczowe](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="49242-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="49242-137">Poniższy przykład kodu pokazuje najwyższego poziomu modułu, który zawiera kod, aż do końca pliku.</span><span class="sxs-lookup"><span data-stu-id="49242-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="49242-138">Aby użyć tego kodu z innego pliku, w tym samym projekcie, możesz użyć kwalifikowane nazwy lub możesz otworzyć modułu przed użyciem funkcji, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="49242-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="49242-139">Zagnieżdżone modułów</span><span class="sxs-lookup"><span data-stu-id="49242-139">Nested Modules</span></span>

<span data-ttu-id="49242-140">Moduły mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="49242-140">Modules can be nested.</span></span> <span data-ttu-id="49242-141">Wewnętrzne moduły muszą wcięty zakresu deklaracje zewnętrznego modułu, aby wskazać, że są one wewnętrzne moduły, nie nowych modułów.</span><span class="sxs-lookup"><span data-stu-id="49242-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="49242-142">Na przykład Porównaj poniższe dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="49242-142">For example, compare the following two examples.</span></span> <span data-ttu-id="49242-143">Moduł `Z` jest wewnętrzny moduł, w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="49242-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="49242-144">Jednak moduł `Z` jest elementem równorzędnym modułu `Y` w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="49242-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="49242-145">Moduł `Z` jest również moduł element równorzędny w poniższym kodzie, ponieważ nie jest wcięty zakresu innych deklaracji w module `Y`.</span><span class="sxs-lookup"><span data-stu-id="49242-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="49242-146">Na koniec zewnętrznego modułu ma nie deklaracji i od razu następuje inny moduł deklaracji, nowe oświadczenie modułu zakłada, że moduł wewnętrzny, ale kompilator wyświetli ostrzeżenie, jeśli drugi definicji modułu nie będą wcięte farther niż pierwszy.</span><span class="sxs-lookup"><span data-stu-id="49242-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="49242-147">Aby wyeliminować ostrzeżenia, należy utworzyć wcięcie moduł wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="49242-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="49242-148">Jeśli chcesz, aby cały kod w pliku w pojedynczym module zewnętrzne i wewnętrzne moduły należy zewnętrznego modułu nie wymaga znaku równości, i nie trzeba być wcięty deklaracji, łącznie z wszelkimi deklaracjami moduł wewnętrzny, które zostanie umieszczona w module zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="49242-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="49242-149">Deklaracje wewnątrz deklaracji wewnętrzny moduł musi być z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="49242-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="49242-150">Poniższy kod przedstawia tę sprawę.</span><span class="sxs-lookup"><span data-stu-id="49242-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="49242-151">Moduły cykliczne</span><span class="sxs-lookup"><span data-stu-id="49242-151">Recursive modules</span></span>

<span data-ttu-id="49242-152">F#4.1 wprowadzono pojęcie modułów, które umożliwia wzajemnie się być typem rekursywnym wszystkie zawarte kodu.</span><span class="sxs-lookup"><span data-stu-id="49242-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="49242-153">Odbywa się za pośrednictwem `module rec`.</span><span class="sxs-lookup"><span data-stu-id="49242-153">This is done via `module rec`.</span></span>  <span data-ttu-id="49242-154">Korzystanie z `module rec` mogą złagodzić ich niektóre problemy, które nie jest możliwość pisania kodu wzajemnie referencyjne typy i moduły.</span><span class="sxs-lookup"><span data-stu-id="49242-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="49242-155">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="49242-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
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

<span data-ttu-id="49242-156">Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="49242-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="49242-157">Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.</span><span class="sxs-lookup"><span data-stu-id="49242-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="49242-158">To nie jest możliwe do wyrażenia w F# usunięto `rec` słowo kluczowe z `RecursiveModule` modułu.</span><span class="sxs-lookup"><span data-stu-id="49242-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="49242-159">Ta funkcja jest również możliwe w [przestrzenie nazw](namespaces.md) z F# 4.1.</span><span class="sxs-lookup"><span data-stu-id="49242-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="49242-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49242-160">See also</span></span>

- [<span data-ttu-id="49242-161">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="49242-161">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="49242-162">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="49242-162">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="49242-163">F#RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły za pośrednictwem szerszego zakresu w plikach</span><span class="sxs-lookup"><span data-stu-id="49242-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)