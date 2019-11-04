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
# <a name="namespaces"></a>Namespaces

Przestrzeń nazw umożliwia organizowanie kodu w obszary powiązanej funkcjonalności przez umożliwienie dołączenia nazwy do grupy elementów F# programu. Przestrzenie nazw są zwykle elementami najwyższego poziomu w F# plikach.

## <a name="syntax"></a>Składnia

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Uwagi

Jeśli chcesz umieścić kod w przestrzeni nazw, pierwsza deklaracja w pliku musi deklarować przestrzeń nazw. Zawartość całego pliku staje się częścią przestrzeni nazw, pod warunkiem, że w pliku nie istnieją dalsze deklaracje przestrzeni nazw. Jeśli tak, to cały kod, aż do następnej deklaracji przestrzeni nazw jest uznawany za znajdujący się w obrębie pierwszej przestrzeni nazw.

Przestrzenie nazw nie mogą bezpośrednio zawierać wartości i funkcji. Zamiast tego, wartości i funkcje muszą być zawarte w modułach, a moduły są zawarte w przestrzeni nazw. Przestrzenie nazw mogą zawierać typy, moduły.

Komentarze dokumentacji XML można zadeklarować powyżej przestrzeni nazw, ale są one ignorowane. Dyrektywy kompilatora można również deklarować powyżej przestrzeni nazw.

Przestrzenie nazw można jawnie zadeklarować za pomocą słowa kluczowego Namespace lub niejawnie podczas deklarowania modułu. Aby jawnie zadeklarować przestrzeń nazw, użyj słowa kluczowego Namespace, po którym następuje nazwa przestrzeni nazw. W poniższym przykładzie przedstawiono plik kodu, który deklaruje przestrzeń nazw `Widgets` z typem i modułem zawartym w tej przestrzeni nazw.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Jeśli cała zawartość pliku znajduje się w jednym module, można także zadeklarować przestrzenie nazw niejawnie za pomocą słowa kluczowego `module` i podać nową nazwę przestrzeni nazw w w pełni kwalifikowanej nazwie modułu. W poniższym przykładzie przedstawiono plik kodu, który deklaruje przestrzeń nazw `Widgets` i `WidgetsModule`modułu, który zawiera funkcję.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Poniższy kod jest równoważny poprzedzającemu kod, ale moduł jest deklaracją modułu lokalnego. W takim przypadku przestrzeń nazw musi znajdować się w osobnym wierszu.

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

Jeśli więcej niż jeden moduł jest wymagany w tym samym pliku w co najmniej jednym obszarze nazw, należy użyć lokalnych deklaracji modułu. W przypadku korzystania z deklaracji modułu lokalnego nie można użyć kwalifikowanej przestrzeni nazw w deklaracjach modułów. Poniższy kod przedstawia plik, który zawiera deklarację przestrzeni nazw i dwie deklaracje modułu lokalnego. W takim przypadku moduły są zawarte bezpośrednio w przestrzeni nazw; nie utworzono niejawnie modułu, który ma taką samą nazwę jak plik. Każdy inny kod w pliku, taki jak powiązanie `do`, znajduje się w przestrzeni nazw, ale nie w modułach wewnętrznych, dlatego należy zakwalifikować element członkowski modułu `widgetFunction` przy użyciu nazwy modułu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Dane wyjściowe tego przykładu są następujące.

```fsharp
Module1 10 20
Module2 5 6
```

Aby uzyskać więcej informacji, zobacz [moduły](modules.md).

## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw

Gdy tworzysz zagnieżdżoną przestrzeń nazw, musisz ją w pełni zakwalifikować. W przeciwnym razie utworzysz nową przestrzeń nazw najwyższego poziomu. Wcięcie jest ignorowane w deklaracjach przestrzeni nazw.

Poniższy przykład pokazuje, jak zadeklarować zagnieżdżoną przestrzeń nazw.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Przestrzenie nazw w plikach i zestawach

Przestrzenie nazw mogą obejmować wiele plików w jednym projekcie lub kompilacji. *Fragment przestrzeni nazw* zawiera opis części przestrzeni nazw, która jest uwzględniona w jednym pliku. Przestrzenie nazw mogą również obejmować wiele zestawów. Na przykład przestrzeń nazw `System` zawiera cały .NET Framework, która obejmuje wiele zestawów i zawiera wiele zagnieżdżonych przestrzeni nazw.

## <a name="global-namespace"></a>Globalna przestrzeń nazw

Aby umieścić nazwy w przestrzeni nazw najwyższego poziomu platformy .NET, należy użyć wstępnie zdefiniowanej przestrzeni nazw `global`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Można również użyć globalnego do odwoływania się do przestrzeni nazw platformy .NET najwyższego poziomu, na przykład w celu rozwiązania konfliktów nazw z innymi przestrzeniami nazw.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Cykliczne przestrzenie nazw

Przestrzenie nazw można także zadeklarować jako cykliczne, aby umożliwić wzajemną rekursywnie wszystkie zawarte w nim kod.  Odbywa się to za pośrednictwem `namespace rec`. Użycie `namespace rec` może wyeliminować problemy, ponieważ nie można napisać wzajemnie referencyjnego kodu między typami i modułami. Poniżej znajduje się przykład:

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

Należy zauważyć, że wyjątek `DontSqueezeTheBananaException` i Klasa `Banana` obie odwołują się do siebie nawzajem.  Ponadto moduł `BananaHelpers` i Klasa `Banana` również odwołują się do siebie. Nie będzie można go wyrazić w F# przypadku usunięcia słowa kluczowego `rec` z przestrzeni nazw `MutualReferences`.

Ta funkcja jest również dostępna dla [modułów](modules.md)najwyższego poziomu.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Moduły](modules.md)
- [F#RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły dla większych zakresów w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
