---
title: Moduły
description: Dowiedz się F# , jak moduł jest grupą F# kodów, takich jak wartości, typy i wartości funkcji, w F# programie.
ms.date: 04/24/2017
ms.openlocfilehash: fbde0c8b001d88614ba2de49c4aa7bfa098c6945
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425053"
---
# <a name="modules"></a>Moduły

W kontekście F# języka *moduł* jest grupą F# kodów, takich jak wartości, typy i wartości funkcji, w F# programie. Grupowanie kodu w modułach ułatwia zachowanie powiązanego kodu i pozwala uniknąć konfliktów nazw w programie.

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

F# Moduł jest grupą konstrukcji F# kodu, takich jak typy, wartości, wartości funkcji i kod w `do` powiązaniach. Jest zaimplementowana jako Klasa środowiska uruchomieniowego języka wspólnego (CLR), która ma tylko statyczne składowe. Istnieją dwa typy deklaracji modułu, w zależności od tego, czy cały plik jest zawarty w module: Deklaracja modułu najwyższego poziomu i Deklaracja modułu lokalnego. Deklaracja modułu najwyższego poziomu zawiera cały plik w module. Deklaracja modułu najwyższego poziomu może być wyświetlana tylko jako pierwsza deklaracja w pliku.

W składni dla deklaracji modułu najwyższego poziomu opcjonalna *kwalifikowana przestrzeń nazw* jest sekwencją nazw zagnieżdżonej przestrzeni nazw zawierającej moduł. Kwalifikowana przestrzeń nazw nie musi być wcześniej zadeklarowana.

Nie ma potrzeby wcięcia deklaracji w module najwyższego poziomu. Musisz wciąć wszystkie deklaracje w modułach lokalnych. W deklaracji modułu lokalnego tylko deklaracje, które są wcięte w deklaracji modułu, są częścią modułu.

Jeśli plik kodu nie zaczyna się od deklaracji modułu najwyższego poziomu lub deklaracji przestrzeni nazw, cała zawartość tego pliku, łącznie z modułami lokalnym, jest częścią niejawnie utworzonego modułu najwyższego poziomu, która ma taką samą nazwę jak plik, bez rozszerzenia z pierwszą literą przekonwertowaną na wielkie litery. Rozważmy na przykład następujący plik.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

Ten plik zostanie skompilowany tak, jakby został zapisany w ten sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

Jeśli masz wiele modułów w pliku, musisz użyć lokalnej deklaracji modułu dla każdego modułu. W przypadku zadeklarowania otaczającej przestrzeni nazw te moduły są częścią otaczającej przestrzeni nazw. Jeśli otaczająca przestrzeń nazw nie jest zadeklarowana, moduły stają się częścią niejawnie utworzonego modułu najwyższego poziomu. Poniższy przykład kodu przedstawia plik kodu, który zawiera wiele modułów. Kompilator niejawnie tworzy moduł najwyższego poziomu o nazwie `Multiplemodules`, a `MyModule1` i `MyModule2` są zagnieżdżone w tym module najwyższego poziomu.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

Jeśli masz wiele plików w projekcie lub w pojedynczej kompilacji lub w przypadku kompilowania biblioteki, musisz dołączyć deklarację przestrzeni nazw lub deklarację modułu w górnej części pliku. F# Kompilator określa tylko nazwę modułu niejawnie, gdy istnieje tylko jeden plik w wierszu polecenia projektu lub kompilacji i tworzysz aplikację.

*Modyfikator dostępności* może mieć jedną z następujących wartości: `public`, `private`, `internal`. Aby uzyskać więcej informacji, zobacz [Access Control](access-control.md). Wartość domyślna to Public.

## <a name="referencing-code-in-modules"></a>Wywoływanie kodu w modułach

Podczas odwoływania się do funkcji, typów i wartości z innego modułu należy użyć kwalifikowanej nazwy lub otworzyć moduł. Jeśli używasz kwalifikowanej nazwy, musisz określić przestrzenie nazw, moduł i identyfikator dla elementu programu, który chcesz. Każdą część kwalifikowanej ścieżki należy oddzielić kropką (.) w następujący sposób.

`Namespace1.Namespace2.ModuleName.Identifier`

Aby uprościć kod, możesz otworzyć moduł lub co najmniej jedną przestrzeń nazw. Aby uzyskać więcej informacji na temat otwierania obszarów nazw i modułów, zobacz [Importowanie deklaracji: słowo kluczowe `open`](import-declarations-the-open-keyword.md).

Poniższy przykład kodu pokazuje moduł najwyższego poziomu, który zawiera cały kod, do końca pliku.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

Aby użyć tego kodu z innego pliku w tym samym projekcie, użyj kwalifikowanych nazw lub Otwórz moduł przed użyciem funkcji, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>Moduły zagnieżdżone

Moduły mogą być zagnieżdżane. W przypadku modułów wewnętrznych należy zastosować wcięcie w postaci deklaracji modułu zewnętrznego, aby wskazać, że są one modułami wewnętrznymi, a nie nowymi modułami. Na przykład Porównaj poniższe dwa przykłady. Moduł `Z` jest modułem wewnętrznym w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

Ale moduł `Z` jest elementem równorzędnym do modułu `Y` w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
Moduł `Z` jest również modułem równorzędnym w poniższym kodzie, ponieważ nie jest wcięty do innych deklaracji w module `Y`.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
Na koniec, jeśli moduł zewnętrzny nie ma deklaracji i jest przyjmowana bezpośrednio przez inną deklarację modułu, przyjmuje się, że deklaracja nowego modułu jest modułem wewnętrznym, ale kompilator wyświetli ostrzeżenie, jeśli druga definicja modułu nie ma wcięcia od pierwszego.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
Aby wyeliminować ostrzeżenie, Zwiększ wcięcie modułu wewnętrznego.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
Jeśli chcesz, aby cały kod w pliku znajdował się w jednym module zewnętrznym i chcesz, aby moduły wewnętrzne, Moduł zewnętrzny nie wymagał znaku równości, a deklaracje, w tym wszelkie wewnętrzne deklaracje modułu, które przechodzą w module zewnętrznym, nie muszą mieć wcięcia. Dla deklaracji wewnątrz wewnętrznych deklaracji modułu należy zastosować wcięcia. W poniższym kodzie przedstawiono ten przypadek.

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>Moduły cykliczne

F#4,1 wprowadza koncepcję modułów, które zezwalają na wzajemną rekursywnie wszystkie zawarte w nim kod.  Odbywa się to za pośrednictwem `module rec`.  Użycie `module rec` może wyeliminować problemy, ponieważ nie można napisać wzajemnie referencyjnego kodu między typami i modułami.  Poniżej znajduje się przykład:

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

Należy zauważyć, że wyjątek `DontSqueezeTheBananaException` i Klasa `Banana` obie odwołują się do siebie nawzajem.  Ponadto moduł `BananaHelpers` i Klasa `Banana` również odwołują się do siebie.  Nie będzie to możliwe w F# przypadku usunięcia słowa kluczowego `rec` z modułu `RecursiveModule`.

Ta możliwość jest również możliwa w [przestrzeniach nazw](namespaces.md) z F# 4,1.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Przestrzenie nazw](namespaces.md)
- [F#RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły dla większych zakresów w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
