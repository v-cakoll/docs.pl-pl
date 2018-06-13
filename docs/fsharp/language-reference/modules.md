---
title: Moduły (F#)
description: 'Dowiedz się, jak to grupa kodzie języka F #, takie jak wartości, typu i wartości funkcji w programie F # w module języka F #.'
ms.date: 04/24/2017
ms.openlocfilehash: 9a1416321e392f7a06551b4a7e3429e3a2d023bd
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483525"
---
# <a name="modules"></a>Moduły

W kontekście języka F # *modułu* to grupa kodzie języka F #, takie jak wartości, typu i wartości funkcji w programie F #. Grupowanie kodu w modułach pomaga zachować kodu powiązanego ze sobą oraz uniknąć konfliktów nazw w programie.

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
Moduł F # to grupa F # konstrukcji kodu typów, wartości, wartości funkcji i kodu w `do` powiązania. Są one zaimplementowane jako wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) klasy z tylko statyczne elementy członkowskie. Istnieją dwa typy deklaracji modułu, w zależności od tego, czy cały plik znajduje się w module: deklaracji najwyższego poziomu modułu i deklaracji modułu lokalnego. Deklaracji najwyższego poziomu modułu obejmuje cały plik w module. Deklaracji najwyższego poziomu modułu może występować tylko jako pierwszej deklaracji w pliku.

W składni dla deklaracji najwyższego poziomu modułu opcjonalny *kwalifikowanych nazw* sekwencję nazwy zagnieżdżonych w przestrzeni nazw, które zawiera moduł. Kwalifikowana przestrzeni nazw ma zostać poprzednio zadeklarowana.

Nie masz wcięcie deklaracji najwyższego poziomu modułu. Masz wcięcie wszystkimi deklaracjami w modułach lokalnych. W deklaracji lokalnej modułu deklaracji, które wcięta w tej deklaracji modułu są częścią tego modułu.

Plik kodu nie zaczyna się od deklaracji najwyższego poziomu modułu lub deklaracja przestrzeni nazw, całą zawartość pliku, w tym wszystkie moduły lokalne staje się częścią modułu najwyższego poziomu niejawnie tworzonych, który ma taką samą nazwę jak pliku bez rozszerzenia, z pierwszej litery przekonwertowany na wielkie litery. Rozważmy na przykład następujący plik.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

Ten plik będzie można skompilować tak, jakby zostały zapisane w ten sposób:

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

Jeśli masz wiele modułów w pliku, należy użyć deklaracji modułu lokalnego dla każdego modułu. Zadeklarowana otaczającej przestrzeni nazw te moduły są częścią otaczającej przestrzeni nazw. Jeśli otaczającej przestrzeni nazw nie jest zadeklarowana, moduły stać się częścią tego modułu najwyższego poziomu niejawnie tworzonych. Poniższy przykładowy kod przedstawia plik kodu, który zawiera wiele modułów. Kompilator niejawnie tworzy moduł najwyższego poziomu o nazwie `Multiplemodules`, i `MyModule1` i `MyModule2` są zagnieżdżone w module najwyższego poziomu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

Jeśli masz wiele plików w projekcie lub w jednej kompilacji lub jeśli tworzysz biblioteki, musi zawierać deklaracji przestrzeni nazw lub modułu deklaracji w górnej części pliku. Kompilator języka F # tylko Określa nazwę modułu niejawnie gdy istnieje tylko jeden plik w projekcie lub kompilacji wiersza polecenia, w przypadku tworzenia aplikacji.

*Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](access-control.md). Wartość domyślna jest publiczny.


## <a name="referencing-code-in-modules"></a>Odwołanie do kodu w modułach
Podając odniesienie funkcje, typy i wartości z innego modułu, możesz za pomocą nazwy kwalifikowanej lub otworzyć modułu. Użycie nazwy kwalifikowanej, należy określić przestrzenie nazw, modułu oraz identyfikatora elementu programu, który ma. W następujący sposób oddzielić każdej części kwalifikowana ścieżka się kropką (.).

`Namespace1.Namespace2.ModuleName.Identifier`

Można otworzyć modułu lub co najmniej jeden z przestrzeni nazw w celu uproszczenia kodu. Aby uzyskać więcej informacji na temat otwierania przestrzeni nazw i modułów, zobacz [deklaracje importowania: `open` — słowo kluczowe](import-declarations-the-open-keyword.md).

Poniższy przykład kodu pokazuje najwyższego poziomu modułu zawierającego wszystkie kod do końca pliku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

Aby użyć tego kodu z innego pliku w tym samym projekcie, albo użyć nazwy kwalifikowane lub można otworzyć modułu przed użyciem funkcji, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Zagnieżdżone modułów
Moduły mogą być zagnieżdżone. Wewnętrzne moduły muszą wcięty miarę deklaracje zewnętrzne modułu wskazuje, że są wewnętrzne moduły nie nowych modułów. Na przykład porównać dwa poniższe przykłady. Moduł `Z` jest wewnętrzny moduł w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

Moduł `Z` jest elementem równorzędnym do modułu `Y` w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
Moduł `Z` jest również moduł równorzędne w poniższym kodzie, ponieważ nie jest wcięty zależnie od innych deklaracji w module `Y`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
Na koniec zewnętrznego modułu ma nie deklaracje i od razu następuje innej deklaracji modułu, nowe oświadczenie modułu zakłada, że moduł wewnętrzny, ale kompilator wyświetli ostrzeżenie, jeśli drugi definicji modułu nie jest wcięty farther niż pierwszy.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
Aby usunąć to ostrzeżenie, wcięcie wewnętrzny moduł.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
Jeśli mają cały kod w pliku w jednym modułu zewnętrznego, a wewnętrzny modułów, zewnętrznego modułu nie wymaga znaku równości i deklaracje, łącznie z wszelkimi deklaracjami wewnętrzny moduł, które przechodzą w module zewnętrznym bez wcięcia. Deklaracje wewnątrz deklaracji wewnętrzny moduł musi być wcięta. Poniższy kod przedstawia przypadek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Moduły cykliczne

F # 4.1 wprowadzono pojęcie modułów, które umożliwia się wzajemnie rekursywne wszystkich zawartych w niej kodu.  Odbywa się za pośrednictwem `module rec`.  Użycie `module rec` można zlikwidować niektóre problemy, które nie jest możliwość napisać kod wzajemnie referencyjnej między typami i modułów.  Oto przykład:

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

Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie.  Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.  To nie jest możliwe do wyrażenia w języku F #, jeśli usunięto `rec` — słowo kluczowe z `RecursiveModule` modułu.

Ta funkcja jest również możliwe w [przestrzeni nazw](namespaces.md) z 4.1 F #.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka F#](index.md)  
[Przestrzenie nazw](namespaces.md)  
[1009-F # RFC FS - Zezwalaj modułów i typy referencyjne wzajemnie przez szerszego zakresu w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
