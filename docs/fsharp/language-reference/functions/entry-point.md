---
title: "Punkt wejścia (F#)"
description: "Dowiedz się, jak ustawić punkt wejścia do programu F # jest skompilowany, ponieważ plik wykonywalny, gdzie wykonywanie formalnie uruchamiana."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a>Punkt wejścia

W tym temacie opisano metody, która służy do ustawiania punktu wejścia do programu F #.


## <a name="syntax"></a>Składnia

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Uwagi
W poprzednich składni *let funkcji wiązania* znajduje się definicja funkcji w `let` powiązania.

Punkt wejścia do programu, który ma być kompilowana jako plik wykonywalny jest, gdzie formalnie rozpoczyna się wykonywanie. Określ punkt wejścia do aplikacji F #, stosując `EntryPoint` atrybutu z programem `main` funkcji. Tej funkcji (utworzone za pomocą `let` powiązanie) musi być ostatnim funkcją ostatniego pliku skompilowany. Ostatni skompilowanego pliku jest ostatni plik projektu lub ostatni plik, który jest przekazywany do wiersza polecenia.

Funkcja punktu wejścia ma typ `string array -> int`. Podanych argumentów wiersza polecenia są przekazywane do `main` funkcji w tablicy ciągów. Pierwszy element tablicy jest pierwszy argument; Nazwa pliku wykonywalnego nie jest uwzględniony w tablicy, jak w przypadku niektórych innych języków. Wartość zwracana jest używany jako kod zakończenia procesu. Zero zwykle wskazuje Powodzenie; podano niezerowe wartości oznaczać błąd. Brak Brak Konwencji szczególne znaczenie niezerową kodów powrotnych; znaczenie kody powrotu są specyficzne dla aplikacji.

Poniższy przykład przedstawia prostą `main` funkcji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Gdy ten kod jest wykonywane przy użyciu wiersza polecenia `EntryPoint.exe 1 2 3`, dane wyjściowe ma następującą składnię.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Niejawne punktu wejścia
Jeśli program nie ma **punktu wejścia** atrybut określający, jawnie punktu wejścia, powiązania najwyższego poziomu w ostatnim pliku do kompilacji są używane jako punkt wejścia.


## <a name="see-also"></a>Zobacz też
[Funkcje](index.md)

[Let — powiązania](let-bindings.md)
