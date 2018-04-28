---
title: Przestrzenie nazw (F#)
description: 'Dowiedz się, jak przestrzeń nazw F # umożliwia organizowanie kodu w obszarach związanych z nimi funkcji umożliwiając dołączyć nazwę do grupowania elementów programu.'
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 695de3b58b8567da60c8ef86900f8e78ea563e0e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="namespaces"></a>Namespaces

Przestrzeń nazw umożliwia organizowanie kodu w obszarach związanych z nimi funkcji umożliwiając dołączyć nazwę do grupowania elementów programu.


## <a name="syntax"></a>Składnia

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>Uwagi
Jeśli chcesz umieścić kodu w przestrzeni nazw, pierwszej deklaracji w pliku musi zadeklarować przestrzeni nazw. Zawartość cały plik stanie się część obszaru nazw.

Przestrzenie nazw nie może bezpośrednio zawierać wartości i funkcje. Zamiast tego funkcje i wartości muszą być uwzględnione w modułach i moduły znajdują się w przestrzeni nazw. Przestrzenie nazw może zawierać typów modułów.

Przestrzenie nazw mogą być deklarowane jawnie ze słowem kluczowym przestrzeni nazw lub niejawnie przy deklarowaniu modułu. Aby jawnie zadeklarować przestrzeni nazw, użyj słowa kluczowego przestrzeni nazw i nazwa przestrzeni nazw. Poniższy przykład przedstawia plik kodu, który deklaruje elementy widget typu i moduł zawarte w tej przestrzeni nazw z przestrzeni nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

Jeśli jeden moduł całą zawartość pliku, można również zadeklarować przestrzeni nazw niejawnie za pomocą `module` — słowo kluczowe i podanie nowej nazwy przestrzeni nazw w nazwie FQDN modułu. W poniższym przykładzie przedstawiono plik kodu, który deklaruje przestrzeni nazw `Widgets` i moduł `WidgetsModule`, który zawiera funkcję.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

Następujący kod jest odpowiednikiem poprzedniego kodu, ale modułem jest deklaracja modułu lokalnego. W takim przypadku przestrzeni nazw musi znajdować się w osobnym wierszu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

Jeśli wymagane jest więcej niż jeden moduł, w tym samym pliku, w jedną lub kilka przestrzeni nazw, należy użyć deklaracji modułów lokalnych. Użycie deklaracji lokalnej modułu, nie można użyć kwalifikowaną przestrzeni nazw w deklaracjach modułów. Poniższy kod przedstawia plik, który ma deklaracja przestrzeni nazw i dwa deklaracjach modułów lokalnych. W takim przypadku moduły znajdują się bezpośrednio w przestrzeni nazw; Brak nie niejawnie tworzonych moduł, który ma taką samą nazwę jak plik. Każdy inny kod w pliku, takich jak `do` powiązanie, jest w przestrzeni nazw, ale nie w wewnętrzne moduły, dlatego należy do elementu członkowskiego moduł kwalifikowania `widgetFunction` przy użyciu nazwy modułu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

Dane wyjściowe w tym przykładzie ma następującą składnię.

```fsharp
Module1 10 20
Module2 5 6
```

Aby uzyskać więcej informacji, zobacz [modułów](modules.md).

## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw
Podczas tworzenia zagnieżdżonych przestrzeni nazw, należy je pełnej kwalifikacji. W przeciwnym razie można utworzyć nowej przestrzeni nazw najwyższego poziomu. Wcięcie jest ignorowany w deklaracji przestrzeni nazw.

Poniższy przykład pokazuje, jak można zadeklarować zagnieżdżonych przestrzeni nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>Przestrzenie nazw w plikach i zestawy
Przestrzenie nazw może obejmować wiele plików z jednego projektu lub kompilacji. Termin *fragmentu przestrzeni nazw* opisuje część przestrzeni nazw, która znajduje się w jednym pliku. Przestrzenie nazw może obejmować wiele zestawów. Na przykład `System` przestrzeń nazw obejmuje całą .NET Framework, która obejmuje wiele zestawów i zawiera wiele zagnieżdżonych obszarów nazw.


## <a name="global-namespace"></a>Namespace globalne
Użyj wstępnie zdefiniowanych nazw `global` umieścić nazwy w przestrzeni nazw .NET najwyższego poziomu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

Umożliwia także globalny ma dotyczyć odwołanie obszaru nazw .NET najwyższego poziomu, na przykład, aby rozwiązać konflikty nazw z innych przestrzeniach nazw.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>Przestrzenie nazw cykliczne

F # 4.1 wprowadzono pojęcie przestrzeni nazw, który umożliwia się wzajemnie rekursywne wszystkich zawartych w niej kodu.  Odbywa się za pośrednictwem `namespace rec`.  Użycie `namespace rec` można zlikwidować niektóre problemy, które nie jest możliwość napisać kod wzajemnie referencyjnej między typami i modułów.  Oto przykład:

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
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

Należy pamiętać, że wyjątek `DontSqueezeTheBananaException` i klasa `Banana` odnoszą się do siebie.  Ponadto moduł `BananaHelpers` i klasa `Banana` także odwoływać się do siebie.  To nie jest możliwe do wyrażenia w języku F #, jeśli usunięto `rec` — słowo kluczowe z `MutualReferences` przestrzeni nazw.

Ta funkcja jest również dostępny do najwyższego poziomu [modułów](modules.md) w F # 4.1 lub nowszego.

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Moduły](modules.md)

[1009-F # RFC FS - Zezwalaj modułów i typy referencyjne wzajemnie przez szerszego zakresu w plikach](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
