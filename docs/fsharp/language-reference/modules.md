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
# <a name="modules"></a>Moduły

W kontekście języka F # *moduł* jest grupą kodu f #, takich jak wartości, typy i wartości funkcji, w programie f #. Grupowanie kodu w modułach ułatwia zachowanie powiązanego kodu i pozwala uniknąć konfliktów nazw w programie.

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

Moduł języka F # jest grupą konstrukcji kodu F #, takich jak typy, wartości, wartości funkcji i kod w `do` powiązaniach. Jest zaimplementowana jako Klasa środowiska uruchomieniowego języka wspólnego (CLR), która ma tylko statyczne składowe. Istnieją dwa typy deklaracji modułu, w zależności od tego, czy cały plik jest zawarty w module: Deklaracja modułu najwyższego poziomu i Deklaracja modułu lokalnego. Deklaracja modułu najwyższego poziomu zawiera cały plik w module. Deklaracja modułu najwyższego poziomu może być wyświetlana tylko jako pierwsza deklaracja w pliku.

W składni dla deklaracji modułu najwyższego poziomu opcjonalna *kwalifikowana przestrzeń nazw* jest sekwencją nazw zagnieżdżonej przestrzeni nazw zawierającej moduł. Kwalifikowana przestrzeń nazw nie musi być wcześniej zadeklarowana.

Nie ma potrzeby wcięcia deklaracji w module najwyższego poziomu. Musisz wciąć wszystkie deklaracje w modułach lokalnych. W deklaracji modułu lokalnego tylko deklaracje, które są wcięte w deklaracji modułu, są częścią modułu.

Jeśli plik kodu nie zaczyna się od deklaracji modułu najwyższego poziomu lub deklaracji przestrzeni nazw, cała zawartość tego pliku, łącznie z modułami lokalnym, jest częścią niejawnie utworzonego modułu najwyższego poziomu, która ma taką samą nazwę jak plik, bez rozszerzenia, z pierwszą literą przekonwertowaną na wielkie litery. Rozważmy na przykład następujący plik.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

Ten plik zostanie skompilowany tak, jakby został zapisany w ten sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

Jeśli masz wiele modułów w pliku, musisz użyć lokalnej deklaracji modułu dla każdego modułu. W przypadku zadeklarowania otaczającej przestrzeni nazw te moduły są częścią otaczającej przestrzeni nazw. Jeśli otaczająca przestrzeń nazw nie jest zadeklarowana, moduły stają się częścią niejawnie utworzonego modułu najwyższego poziomu. Poniższy przykład kodu przedstawia plik kodu, który zawiera wiele modułów. Kompilator niejawnie tworzy moduł najwyższego poziomu o `Multiplemodules`nazwie i `MyModule1` i `MyModule2` jest zagnieżdżony w tym module najwyższego poziomu.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

Jeśli masz wiele plików w projekcie lub w pojedynczej kompilacji lub w przypadku kompilowania biblioteki, musisz dołączyć deklarację przestrzeni nazw lub deklarację modułu w górnej części pliku. Kompilator F # określa tylko nazwę modułu niejawnie, gdy istnieje tylko jeden plik w wierszu polecenia projektu lub kompilacji i tworzysz aplikację.

*Modyfikator dostępności* może mieć jedną z następujących wartości: `public`, `private`,. `internal` Aby uzyskać więcej informacji, zobacz [Kontrola dostępu](access-control.md). Wartość domyślna to Public.

## <a name="referencing-code-in-modules"></a>Wywoływanie kodu w modułach

Podczas odwoływania się do funkcji, typów i wartości z innego modułu należy użyć kwalifikowanej nazwy lub otworzyć moduł. Jeśli używasz kwalifikowanej nazwy, musisz określić przestrzenie nazw, moduł i identyfikator dla elementu programu, który chcesz. Każdą część kwalifikowanej ścieżki należy oddzielić kropką (.) w następujący sposób.

`Namespace1.Namespace2.ModuleName.Identifier`

Aby uprościć kod, możesz otworzyć moduł lub co najmniej jedną przestrzeń nazw. Aby uzyskać więcej informacji na temat otwierania obszarów nazw i modułów, zobacz [Importowanie `open` deklaracji: słowo kluczowe](import-declarations-the-open-keyword.md).

Poniższy przykład kodu pokazuje moduł najwyższego poziomu, który zawiera cały kod, do końca pliku.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

Aby użyć tego kodu z innego pliku w tym samym projekcie, użyj kwalifikowanych nazw lub Otwórz moduł przed użyciem funkcji, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Moduły zagnieżdżone

Moduły mogą być zagnieżdżane. W przypadku modułów wewnętrznych należy zastosować wcięcie w postaci deklaracji modułu zewnętrznego, aby wskazać, że są one modułami wewnętrznymi, a nie nowymi modułami. Na przykład Porównaj poniższe dwa przykłady. Moduł `Z` jest modułem wewnętrznym w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

Ale moduł `Z` jest elementem równorzędnym do `Y` modułu w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
Moduł `Z` jest również modułem równorzędnym w poniższym kodzie, ponieważ nie jest wcięty do innych deklaracji w module `Y`.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
Na koniec, jeśli moduł zewnętrzny nie ma deklaracji i następuje bezpośrednio przez inną deklarację modułu, przyjmuje się, że deklaracja modułu jest modułem wewnętrznym, ale kompilator wyświetli ostrzeżenie, jeśli druga definicja modułu nie ma wcięcia od pierwszego.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
Aby wyeliminować ostrzeżenie, Zwiększ wcięcie modułu wewnętrznego.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
Jeśli chcesz, aby cały kod w pliku znajdował się w jednym module zewnętrznym i chcesz, aby moduły wewnętrzne, Moduł zewnętrzny nie wymagał znaku równości, a deklaracje, w tym wszelkie wewnętrzne deklaracje modułu, które przechodzą w module zewnętrznym, nie muszą mieć wcięcia. Dla deklaracji wewnątrz wewnętrznych deklaracji modułu należy zastosować wcięcia. W poniższym kodzie przedstawiono ten przypadek.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Moduły cykliczne

F # 4,1 wprowadza koncepcję modułów, które zezwalają na wzajemną rekursywnie wszystkie zawarte w nim kod.  Jest to realizowane za `module rec`pośrednictwem.  Użycie `module rec` może wyeliminować pewne problemy, ponieważ nie można napisać wzajemnie referencyjnego kodu między typami i modułami.  Poniżej znajduje się przykład:

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

Należy zauważyć, że `DontSqueezeTheBananaException` wyjątek i Klasa `Banana` odnoszą się do siebie nawzajem.  Ponadto moduł `BananaHelpers` i Klasa `Banana` odnoszą się do siebie nawzajem.  W przypadku usunięcia `rec` słowa kluczowego z `RecursiveModule` modułu nie będzie można wyrazić w języku F #.

Ta możliwość jest również dostępna w [przestrzeniach nazw](namespaces.md) przy użyciu języka F # 4,1.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F #](index.md)
- [Namespaces](namespaces.md)
- [F # RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły dla większych zakresów w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
