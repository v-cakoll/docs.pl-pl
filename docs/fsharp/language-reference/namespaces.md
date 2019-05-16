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
# <a name="namespaces"></a>Namespaces

Przestrzeń nazw umożliwia organizowanie kodu w obszarach powiązane funkcje, dzięki któremu można dołączyć nazwę grupie F# program elementów. Przestrzenie nazw są zazwyczaj najwyższego poziomu elementów w F# plików.

## <a name="syntax"></a>Składnia

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a>Uwagi

Jeśli chcesz umieścić kod w przestrzeni nazw, w pierwszej deklaracji w pliku musi deklarować przestrzeń nazw. Zawartość cały plik stają się częścią przestrzeni nazw, pod warunkiem istnieje żadna deklaracja przestrzeni nazw bardziej szczegółowo w pliku. Jeśli tak jest rzeczywiście, cały kod, aż do następnego deklaracji przestrzeni nazw jest traktowany jako mieścić się w pierwszej przestrzeni nazw.

Przestrzenie nazw nie może bezpośrednio zawierać wartości i funkcje. Zamiast tego wartości i funkcje, które muszą być zawarte w modułach i moduły są uwzględnione w przestrzeni nazw. Przestrzenie nazw może zawierać typy i moduły.

Komentarze dokumentacji XML mogą być deklarowane powyżej przestrzeni nazw, ale są one ignorowane. Dyrektywy kompilatora mogą być także zadeklarowane powyżej przestrzeni nazw.

Przestrzenie nazw mogą być deklarowane jawnie za pomocą słowa kluczowego przestrzeni nazw lub niejawnie podczas deklarowania modułu. Aby jawnie deklarować przestrzeń nazw, należy użyć słowo kluczowe przestrzeni nazw, a następnie według nazwy przestrzeni nazw. W poniższym przykładzie pokazano plik kodu, który deklaruje przestrzeni nazw `Widgets` o typie i moduł zawarty w tej przestrzeni nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Jeśli jeden moduł całą zawartość pliku, można również zadeklarować przestrzeni nazw niejawnie przy użyciu `module` — słowo kluczowe i podanie nowej nazwy przestrzeni nazw w module w pełni kwalifikowana nazwa. W poniższym przykładzie pokazano plik kodu, który deklaruje przestrzeni nazw `Widgets` i modułu `WidgetsModule`, która zawiera funkcję.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Poniższy kod jest odpowiednikiem poprzedniego kodu, ale moduł jest deklaracją modułu lokalnego. W takim przypadku przestrzeni nazw musi znajdować się w osobnym wierszu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Jeśli więcej niż jeden moduł jest wymagane w tym samym pliku, w jeden lub kilka przestrzeni nazw, należy użyć deklaracje modułów lokalnych. Gdy używasz deklaracje modułów lokalnych, nie można używać kwalifikowanych przestrzeni nazw w deklaracjach modułów. Poniższy kod przedstawia plik, który zawiera deklarację przestrzeni nazw i dwie deklaracje modułów lokalnych. W tym przypadku moduły znajdują się bezpośrednio w przestrzeni nazw; nie ma żadnych stworzonego moduł, który ma taką samą nazwę jak plik. Każdy inny kod w pliku, takie jak `do` powiązanie, jest w przestrzeni nazw, ale nie w przypadku wewnętrznych modułów, więc musi kwalifikuj element członkowski modułu `widgetFunction` przy użyciu nazwy modułu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

W tym przykładzie dane wyjściowe wyglądają następująco.

```fsharp
Module1 10 20
Module2 5 6
```

Aby uzyskać więcej informacji, zobacz [modułów](modules.md).

## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw

Kiedy tworzysz zagnieżdżone przestrzenie nazw, możesz je pełnej kwalifikacji. W przeciwnym razie możesz utworzyć nową przestrzeń nazw najwyższego poziomu. Wcięcie jest ignorowany w deklaracji przestrzeni nazw.

Poniższy przykład pokazuje sposób deklarowania zagnieżdżone przestrzenie nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Przestrzenie nazw plików i zestawów

Przestrzenie nazw może obejmować wiele plików w jednym projekcie lub kompilacji. Termin *przestrzeni nazw fragmentu* opisuje część przestrzeni nazw, który znajduje się w jednym pliku. Przestrzenie nazw mogą obejmować wiele zestawów. Na przykład `System` przestrzeń nazw zawiera całe .NET Framework, który obejmuje wiele zestawów i zawiera wiele zagnieżdżone przestrzenie nazw.

## <a name="global-namespace"></a>Globalne Namespace

Użyj wstępnie zdefiniowanych nazw `global` umieszczenie nazwy w przestrzeni nazw .NET najwyższego poziomu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Umożliwia także globalne k odkazu .NET przestrzeń nazw najwyższego poziomu, na przykład, aby rozwiązać konflikty nazw z innych obszarów nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Przestrzenie nazw cykliczne

Przestrzenie nazw mogą być także zadeklarowane jako cykliczne do obsługi całego kodu zawarte jako wzajemnie cykliczne.  Odbywa się za pośrednictwem `namespace rec`. Korzystanie z `namespace rec` mogą złagodzić ich niektóre problemy, które nie jest możliwość pisania kodu wzajemnie referencyjne typy i moduły. Oto przykład:

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

Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie nawzajem.  Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie. W takich sytuacjach przydałaby to wyrazić w F# usunięto `rec` słowo kluczowe z `MutualReferences` przestrzeni nazw.

Ta funkcja jest również dostępna dla najwyższego poziomu [modułów](modules.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Moduły](modules.md)
- [F#RFC FS-1009 — Zezwalaj na wzajemnie referencyjne typy i moduły za pośrednictwem szerszego zakresu w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
