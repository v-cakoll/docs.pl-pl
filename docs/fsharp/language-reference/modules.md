---
title: Moduły (F#)
description: 'Dowiedz się, jak moduł F # to grupa kodzie języka F #, takie jak wartości, typy i wartości funkcji, w programie F #.'
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "45528529"
---
# <a name="modules"></a>Moduły

W kontekście języka F # *modułu* to grupa kodzie języka F #, takie jak wartości, typy i wartości funkcji, w programie F #. Grupowanie kodu w modułach pomaga zachować kod pokrewny ze sobą oraz uniknąć konfliktów nazw w programie.

## <a name="syntax"></a>Składnia

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>Uwagi

Moduł F # to grupa kodu konstrukcji F #, takie jak typy wartości, wartości funkcji i kodu w `do` powiązania. Są one zaimplementowane jako wspólnej klasy środowiska uruchomieniowego (języka wspólnego CLR) języka, która ma tylko statyczne elementy członkowskie. Istnieją dwa typy deklaracje modułów, w zależności od tego, czy cały plik znajduje się w module: deklaracji najwyższego poziomu modułu i deklaracja modułu lokalnego. Deklaracji najwyższego poziomu modułu obejmuje cały plik w module. Deklaracji najwyższego poziomu modułu może znajdować się tylko jako pierwszej deklaracji w pliku.

W składni deklaracji najwyższego poziomu modułu opcjonalnego *kwalifikowaną przestrzeń nazw* jest sekwencji nazwy zagnieżdżone przestrzenie nazw, która zawiera moduł. Kwalifikowanych przestrzeni nazw ma być uprzednio zadeklarowany.

Nie masz Wcięcie Deklaracje w module najwyższego poziomu. Masz wcięcie wszystkie deklaracje modułów lokalnych. W module lokalnym deklaracji deklaracje, które tworzone jest wcięcie w obszarze deklaracja modułu są częścią tego modułu.

Plik kodu nie zaczyna się od deklaracji najwyższego poziomu modułu lub deklaracja przestrzeni nazw, całą zawartość pliku, w tym wszystkie moduły lokalne staje się częścią stworzonego modułu najwyższego poziomu, który ma taką samą nazwę jak plik, bez rozszerzenia i przy użyciu pierwszej litery na wielkie litery. Na przykład rozważmy następujący plik.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Ten plik będzie można skompilować tak, jakby zostały napisane w ten sposób:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Jeśli masz wiele modułów w pliku dla każdego modułu, należy użyć deklaracji modułu lokalnego. Jeśli zadeklarowano otaczającej przestrzeni nazw, moduły są częścią otaczającej przestrzeni nazw. Jeśli otaczającej przestrzeni nazw nie jest zadeklarowana, moduły stają się częścią stworzonego najwyższego poziomu modułu. Poniższy przykład kodu pokazuje pliku z kodem, który zawiera wiele modułów. Kompilator niejawnie tworzy moduł najwyższego poziomu o nazwie `Multiplemodules`, i `MyModule1` i `MyModule2` są zagnieżdżone w module najwyższego poziomu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Jeśli masz wiele plików w projekcie lub w pojedynczej kompilacji lub jeśli tworzysz biblioteki, musi zawierać deklaracji przestrzeni nazw lub module deklaracji w górnej części pliku. Kompilator F # Określa tylko nazwy modułu niejawnie, gdy istnieje tylko jeden plik w wierszu polecenia kompilacji lub projektu, w przypadku tworzenia aplikacji.

*Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](access-control.md). Wartość domyślna jest publiczny.

## <a name="referencing-code-in-modules"></a>Odwoływanie się do kodu w modułach

Gdy odwołujesz się funkcje, typy i wartości z innego modułu, należy użyć kwalifikowanej nazwy lub otworzyć modułu. Jeśli używasz nazwy kwalifikowanej, należy określić przestrzenie nazw, moduł i identyfikator elementu programu, który ma. Możesz oddzielić każda część kwalifikowana ścieżka pojedynczego znaku kropki (.), w następujący sposób.

`Namespace1.Namespace2.ModuleName.Identifier`

Można otworzyć moduł lub przynajmniej jednej przestrzeni nazw w celu uproszczenia kodu. Aby uzyskać więcej informacji na temat modułów i przestrzeni nazw otwierania zobacz [deklaracje importowania: `open` — słowo kluczowe](import-declarations-the-open-keyword.md).

Poniższy przykład kodu pokazuje najwyższego poziomu modułu, który zawiera kod, aż do końca pliku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Aby użyć tego kodu z innego pliku, w tym samym projekcie, możesz użyć kwalifikowane nazwy lub możesz otworzyć modułu przed użyciem funkcji, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Zagnieżdżone modułów

Moduły mogą być zagnieżdżone. Wewnętrzne moduły muszą wcięty zakresu deklaracje zewnętrznego modułu, aby wskazać, że są one wewnętrzne moduły, nie nowych modułów. Na przykład Porównaj poniższe dwa przykłady. Moduł `Z` jest wewnętrzny moduł, w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Jednak moduł `Z` jest elementem równorzędnym modułu `Y` w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Moduł `Z` jest również moduł element równorzędny w poniższym kodzie, ponieważ nie jest wcięty zakresu innych deklaracji w module `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Na koniec zewnętrznego modułu ma nie deklaracji i od razu następuje inny moduł deklaracji, nowe oświadczenie modułu zakłada, że moduł wewnętrzny, ale kompilator wyświetli ostrzeżenie, jeśli drugi definicji modułu nie będą wcięte farther niż pierwszy.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Aby wyeliminować ostrzeżenia, należy utworzyć wcięcie moduł wewnętrzny.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Jeśli chcesz, aby cały kod w pliku w pojedynczym module zewnętrzne i wewnętrzne moduły należy zewnętrznego modułu nie wymaga znaku równości, i nie trzeba być wcięty deklaracji, łącznie z wszelkimi deklaracjami moduł wewnętrzny, które zostanie umieszczona w module zewnętrznym. Deklaracje wewnątrz deklaracji wewnętrzny moduł musi być z wcięciem. Poniższy kod przedstawia tę sprawę.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Moduły cykliczne

F # 4.1 wprowadzono pojęcie modułów, które umożliwia wzajemnie się być typem rekursywnym wszystkie zawarte kodu.  Odbywa się za pośrednictwem `module rec`.  Korzystanie z `module rec` mogą złagodzić ich niektóre problemy, które nie jest możliwość pisania kodu wzajemnie referencyjne typy i moduły.  Oto przykład:

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

Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie nawzajem.  Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.  To nie jest możliwe do wyrażenia w języku F #, jeśli usunięto `rec` słowo kluczowe z `RecursiveModule` modułu.

Ta funkcja jest również możliwe w [przestrzenie nazw](namespaces.md) z F # 4.1.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)  
- [Przestrzenie nazw](namespaces.md)  
- [F # RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły za pośrednictwem szerszego zakresu w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
