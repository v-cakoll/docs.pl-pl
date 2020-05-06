---
title: Moduły
description: 'Dowiedz się, jak moduł języka F # jest grupą kodów języka F #, takich jak wartości, typy i wartości funkcji, w programie F #.'
ms.date: 04/24/2017
ms.openlocfilehash: 5f99bbd8069478bf0c7db2800ae545f31926728a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794367"
---
# <a name="modules"></a><span data-ttu-id="34df4-103">Moduły</span><span class="sxs-lookup"><span data-stu-id="34df4-103">Modules</span></span>

<span data-ttu-id="34df4-104">W kontekście języka F # *moduł* jest grupą kodu f #, takich jak wartości, typy i wartości funkcji, w programie f #.</span><span class="sxs-lookup"><span data-stu-id="34df4-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="34df4-105">Grupowanie kodu w modułach ułatwia zachowanie powiązanego kodu i pozwala uniknąć konfliktów nazw w programie.</span><span class="sxs-lookup"><span data-stu-id="34df4-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="34df4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="34df4-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="34df4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34df4-107">Remarks</span></span>

<span data-ttu-id="34df4-108">Moduł języka F # jest grupą konstrukcji kodu F #, takich jak typy, wartości, wartości funkcji i kod w `do` powiązaniach.</span><span class="sxs-lookup"><span data-stu-id="34df4-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="34df4-109">Jest zaimplementowana jako Klasa środowiska uruchomieniowego języka wspólnego (CLR), która ma tylko statyczne składowe.</span><span class="sxs-lookup"><span data-stu-id="34df4-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="34df4-110">Istnieją dwa typy deklaracji modułu, w zależności od tego, czy cały plik jest zawarty w module: Deklaracja modułu najwyższego poziomu i Deklaracja modułu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="34df4-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="34df4-111">Deklaracja modułu najwyższego poziomu zawiera cały plik w module.</span><span class="sxs-lookup"><span data-stu-id="34df4-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="34df4-112">Deklaracja modułu najwyższego poziomu może być wyświetlana tylko jako pierwsza deklaracja w pliku.</span><span class="sxs-lookup"><span data-stu-id="34df4-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="34df4-113">W składni dla deklaracji modułu najwyższego poziomu opcjonalna *kwalifikowana przestrzeń nazw* jest sekwencją nazw zagnieżdżonej przestrzeni nazw zawierającej moduł.</span><span class="sxs-lookup"><span data-stu-id="34df4-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="34df4-114">Kwalifikowana przestrzeń nazw nie musi być wcześniej zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="34df4-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="34df4-115">Nie ma potrzeby wcięcia deklaracji w module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="34df4-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="34df4-116">Musisz wciąć wszystkie deklaracje w modułach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="34df4-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="34df4-117">W deklaracji modułu lokalnego tylko deklaracje, które są wcięte w deklaracji modułu, są częścią modułu.</span><span class="sxs-lookup"><span data-stu-id="34df4-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="34df4-118">Jeśli plik kodu nie zaczyna się od deklaracji modułu najwyższego poziomu lub deklaracji przestrzeni nazw, cała zawartość tego pliku, łącznie z modułami lokalnym, jest częścią niejawnie utworzonego modułu najwyższego poziomu, która ma taką samą nazwę jak plik, bez rozszerzenia, z pierwszą literą przekonwertowaną na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="34df4-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="34df4-119">Rozważmy na przykład następujący plik.</span><span class="sxs-lookup"><span data-stu-id="34df4-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="34df4-120">Ten plik zostanie skompilowany tak, jakby został zapisany w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="34df4-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="34df4-121">Jeśli masz wiele modułów w pliku, musisz użyć lokalnej deklaracji modułu dla każdego modułu.</span><span class="sxs-lookup"><span data-stu-id="34df4-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="34df4-122">W przypadku zadeklarowania otaczającej przestrzeni nazw te moduły są częścią otaczającej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="34df4-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="34df4-123">Jeśli otaczająca przestrzeń nazw nie jest zadeklarowana, moduły stają się częścią niejawnie utworzonego modułu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="34df4-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="34df4-124">Poniższy przykład kodu przedstawia plik kodu, który zawiera wiele modułów.</span><span class="sxs-lookup"><span data-stu-id="34df4-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="34df4-125">Kompilator niejawnie tworzy moduł najwyższego poziomu o `Multiplemodules`nazwie i `MyModule1` i `MyModule2` jest zagnieżdżony w tym module najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="34df4-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="34df4-126">Jeśli masz wiele plików w projekcie lub w pojedynczej kompilacji lub w przypadku kompilowania biblioteki, musisz dołączyć deklarację przestrzeni nazw lub deklarację modułu w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="34df4-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="34df4-127">Kompilator F # określa tylko nazwę modułu niejawnie, gdy istnieje tylko jeden plik w wierszu polecenia projektu lub kompilacji i tworzysz aplikację.</span><span class="sxs-lookup"><span data-stu-id="34df4-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="34df4-128">*Modyfikator dostępności* może mieć jedną z następujących wartości: `public`, `private`,. `internal`</span><span class="sxs-lookup"><span data-stu-id="34df4-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="34df4-129">Aby uzyskać więcej informacji, zobacz [Kontrola dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="34df4-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="34df4-130">Wartość domyślna to Public.</span><span class="sxs-lookup"><span data-stu-id="34df4-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="34df4-131">Wywoływanie kodu w modułach</span><span class="sxs-lookup"><span data-stu-id="34df4-131">Referencing Code in Modules</span></span>

<span data-ttu-id="34df4-132">Podczas odwoływania się do funkcji, typów i wartości z innego modułu należy użyć kwalifikowanej nazwy lub otworzyć moduł.</span><span class="sxs-lookup"><span data-stu-id="34df4-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="34df4-133">Jeśli używasz kwalifikowanej nazwy, musisz określić przestrzenie nazw, moduł i identyfikator dla elementu programu, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="34df4-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="34df4-134">Każdą część kwalifikowanej ścieżki należy oddzielić kropką (.) w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="34df4-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="34df4-135">Aby uprościć kod, możesz otworzyć moduł lub co najmniej jedną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="34df4-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="34df4-136">Aby uzyskać więcej informacji na temat otwierania obszarów nazw i modułów, zobacz [Importowanie `open` deklaracji: słowo kluczowe](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="34df4-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="34df4-137">Poniższy przykład kodu pokazuje moduł najwyższego poziomu, który zawiera cały kod, do końca pliku.</span><span class="sxs-lookup"><span data-stu-id="34df4-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="34df4-138">Aby użyć tego kodu z innego pliku w tym samym projekcie, użyj kwalifikowanych nazw lub Otwórz moduł przed użyciem funkcji, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="34df4-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="34df4-139">Moduły zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="34df4-139">Nested Modules</span></span>

<span data-ttu-id="34df4-140">Moduły mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="34df4-140">Modules can be nested.</span></span> <span data-ttu-id="34df4-141">W przypadku modułów wewnętrznych należy zastosować wcięcie w postaci deklaracji modułu zewnętrznego, aby wskazać, że są one modułami wewnętrznymi, a nie nowymi modułami.</span><span class="sxs-lookup"><span data-stu-id="34df4-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="34df4-142">Na przykład Porównaj poniższe dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="34df4-142">For example, compare the following two examples.</span></span> <span data-ttu-id="34df4-143">Moduł `Z` jest modułem wewnętrznym w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34df4-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="34df4-144">Ale moduł `Z` jest elementem równorzędnym do `Y` modułu w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34df4-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="34df4-145">Moduł `Z` jest również modułem równorzędnym w poniższym kodzie, ponieważ nie jest wcięty do innych deklaracji w module `Y`.</span><span class="sxs-lookup"><span data-stu-id="34df4-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="34df4-146">Na koniec, jeśli moduł zewnętrzny nie ma deklaracji i następuje bezpośrednio przez inną deklarację modułu, przyjmuje się, że deklaracja modułu jest modułem wewnętrznym, ale kompilator wyświetli ostrzeżenie, jeśli druga definicja modułu nie ma wcięcia od pierwszego.</span><span class="sxs-lookup"><span data-stu-id="34df4-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="34df4-147">Aby wyeliminować ostrzeżenie, Zwiększ wcięcie modułu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="34df4-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="34df4-148">Jeśli chcesz, aby cały kod w pliku znajdował się w jednym module zewnętrznym i chcesz, aby moduły wewnętrzne, Moduł zewnętrzny nie wymagał znaku równości, a deklaracje, w tym wszelkie wewnętrzne deklaracje modułu, które przechodzą w module zewnętrznym, nie muszą mieć wcięcia.</span><span class="sxs-lookup"><span data-stu-id="34df4-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="34df4-149">Dla deklaracji wewnątrz wewnętrznych deklaracji modułu należy zastosować wcięcia.</span><span class="sxs-lookup"><span data-stu-id="34df4-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="34df4-150">W poniższym kodzie przedstawiono ten przypadek.</span><span class="sxs-lookup"><span data-stu-id="34df4-150">The following code shows this case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="34df4-151">Moduły cykliczne</span><span class="sxs-lookup"><span data-stu-id="34df4-151">Recursive modules</span></span>

<span data-ttu-id="34df4-152">F # 4,1 wprowadza koncepcję modułów, które zezwalają na wzajemną rekursywnie wszystkie zawarte w nim kod.</span><span class="sxs-lookup"><span data-stu-id="34df4-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="34df4-153">Jest to realizowane za `module rec`pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="34df4-153">This is done via `module rec`.</span></span>  <span data-ttu-id="34df4-154">Użycie `module rec` może wyeliminować pewne problemy, ponieważ nie można napisać wzajemnie referencyjnego kodu między typami i modułami.</span><span class="sxs-lookup"><span data-stu-id="34df4-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="34df4-155">Poniżej znajduje się przykład:</span><span class="sxs-lookup"><span data-stu-id="34df4-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
    type Orientation = Up | Down
    type PeelState = Peeled | Unpeeled

    // This exception depends on the type below.
    exception DontSqueezeTheBananaException of Banana

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

<span data-ttu-id="34df4-156">Należy zauważyć, że `DontSqueezeTheBananaException` wyjątek i Klasa `Banana` odnoszą się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="34df4-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="34df4-157">Ponadto moduł `BananaHelpers` i Klasa `Banana` odnoszą się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="34df4-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="34df4-158">W przypadku usunięcia `rec` słowa kluczowego z `RecursiveModule` modułu nie będzie można wyrazić w języku F #.</span><span class="sxs-lookup"><span data-stu-id="34df4-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="34df4-159">Ta możliwość jest również dostępna w [przestrzeniach nazw](namespaces.md) przy użyciu języka F # 4,1.</span><span class="sxs-lookup"><span data-stu-id="34df4-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="34df4-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34df4-160">See also</span></span>

- [<span data-ttu-id="34df4-161">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="34df4-161">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="34df4-162">Namespaces</span><span class="sxs-lookup"><span data-stu-id="34df4-162">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="34df4-163">F # RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły dla większych zakresów w plikach</span><span class="sxs-lookup"><span data-stu-id="34df4-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
