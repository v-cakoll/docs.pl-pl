---
title: Punkt wejścia
description: Dowiedz się, jak ustawić punkt wejścia do F# programu, który jest kompilowany jako plik wykonywalny, gdzie wykonywanie zostanie rozpoczęte.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630522"
---
# <a name="entry-point"></a>Punkt wejścia

W tym temacie opisano metodę, która służy do ustawiania punktu wejścia do F# programu.

## <a name="syntax"></a>Składnia

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni, *Let-Function-Binding* jest definicją funkcji w `let` powiązaniu.

Punkt wejścia do programu, który jest kompilowany jako plik wykonywalny, to miejsce, w którym wykonywanie jest uruchamiane od początku. Należy określić punkt wejścia do F# aplikacji przez zastosowanie `EntryPoint` atrybutu `main` do funkcji programu. Ta funkcja (utworzona przy użyciu `let` powiązania) musi być ostatnią funkcją w ostatnim skompilowanym pliku. Ostatni skompilowany plik to ostatni plik w projekcie lub ostatni plik, który jest przesyłany do wiersza polecenia.

Funkcja punktu wejścia ma typ `string array -> int`. Argumenty podane w wierszu polecenia są przekazywane do `main` funkcji w tablicy ciągów. Pierwszy element tablicy jest pierwszym argumentem; Nazwa pliku wykonywalnego nie jest uwzględniona w tablicy, ponieważ znajduje się w innych językach. Wartość zwracana jest używana jako kod zakończenia procesu. Wartość zerowa zazwyczaj oznacza sukces; wartości niezerowe wskazują na błąd. Nie ma Konwencji dla określonego znaczenia niezerowych kodów powrotu; znaczenie kodów powrotu jest specyficzne dla aplikacji.

Poniższy przykład ilustruje prostą `main` funkcję.

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

Gdy ten kod jest wykonywany z wierszem `EntryPoint.exe 1 2 3`polecenia, dane wyjściowe są następujące.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Niejawny punkt wejścia

Gdy program nie ma atrybutu **EntryPoint** , który jawnie wskazuje punkt wejścia, powiązania najwyższego poziomu w ostatnim pliku do skompilowania są używane jako punkt wejścia.

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
- [Powiązania „let”](let-bindings.md)
