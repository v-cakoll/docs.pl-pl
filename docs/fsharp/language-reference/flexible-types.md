---
title: Typy elastyczne (F#)
description: "Dowiedz się, jak używać F # elastycznym typem adnotacji, co oznacza, że parametr, zmiennej lub wartość ma typ, który jest zgodny z określonym typem."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a>Typy elastyczne

A *adnotacji typu elastyczne* oznacza, że parametr, zmiennej lub wartość ma typ, który jest zgodny z określonym typem, których zgodność jest określany przez położenie w hierarchii zorientowane obiektowo interfejsów lub klas. Typy elastyczne przydają się szczególnie, gdy automatycznej konwersji do typów wyżej w hierarchii typów nie występuje, ale nadal chcesz włączyć funkcjonalność programu do pracy z dowolnego typu w hierarchii lub dowolnego typu, który implementuje interfejs.

## <a name="syntax"></a>Składnia

```fsharp
#type
```

## <a name="remarks"></a>Uwagi

W poprzednich składni *typu* reprezentuje typu podstawowego lub interfejs.

Elastyczne typu jest odpowiednikiem typu ogólnego, który ma ograniczenie, która ogranicza dozwolonymi typami do typów, które są zgodne z typem base lub interface. Oznacza to, że następujące dwa wiersze kodu są równoważne.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Typy elastyczne są przydatne w kilku sytuacjach. Na przykład jeśli masz wyższej funkcji order (funkcja przyjmuje jako argument funkcji), warto często elastyczne typ zwracany funkcji. W poniższym przykładzie użycie elastyczne typu z argumentem sekwencji w `iterate2` umożliwia wyższej funkcji order do pracy z funkcjami, które generują sekwencji, tablic, list i innego typu wyliczenia.

Należy wziąć pod uwagę następujące dwie funkcje, jeden z których zwraca sekwencji, drugi z nich zwraca typ elastyczne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Inny przykład wziąć pod uwagę [SEQ.concat —](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkcja biblioteki:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Żadnego z następujących wyliczalny sekwencji można przekazać do tej funkcji:

- Listę list
- Lista tablic
- Tablica list
- Tablica sekwencji
- Dowolną kombinację wyliczalny sekwencji

Poniższy kod używa `Seq.concat` aby zademonstrować scenariusze, które można obsługiwać przy użyciu typy elastyczne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Dane wyjściowe są następujące:

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

W języku F # jak w innych językach zorientowane obiektowo istnieją kontekstów, w których typy pochodne lub typów, które implementują interfejsy są automatycznie konwertowane na typ podstawowy lub typ interfejsu. Te automatycznej konwersji wystąpić w argumentach bezpośrednio, ale nie w przypadku, gdy typem jest w stanie podrzędny, jako część typu bardziej złożonych, takie jak typ zwracany typ funkcji lub jako argument typu. W związku z tym notacji elastycznym typem jest szczególnie przydatna, jeśli typ, który chcesz zastosować go do jest częścią typu bardziej złożonych.

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka F #](index.md)

[Typy ogólne](generics/index.md)
