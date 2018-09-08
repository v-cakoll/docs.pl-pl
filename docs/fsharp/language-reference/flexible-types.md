---
title: Typy elastyczne (F#)
description: 'Dowiedz się, jak używać języka F # elastycznym typem adnotacji, co oznacza, że parametr, zmienna lub wartość ma typ, który jest zgodny z określonym typem.'
ms.date: 05/16/2016
ms.openlocfilehash: b6c97c3cc19f15b2c8db74b2c55660a16b2858f7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179650"
---
# <a name="flexible-types"></a>Typy elastyczne

A *adnotacji typu elastyczne* oznacza, że parametr, zmienna lub wartość ma typ, który jest zgodny z określonego typu, w którym zgodność jest określana przez pozycji w hierarchii zorientowane obiektowo, klas lub interfejsów. Typy elastyczne przydają się szczególnie, gdy automatycznej konwersji do typów wyżej w hierarchii typów nie występuje, ale nadal chcesz włączyć własne funkcje do pracy z dowolnego typu w hierarchii lub dowolny typ, który implementuje interfejs.

## <a name="syntax"></a>Składnia

```fsharp
#type
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *typu* reprezentuje typem bazowym lub interfejsem.

Typ ogólny, który ma ograniczenie, które ogranicza dozwolonymi typami na typy, które są zgodne z typem base lub interface odpowiada elastycznym typem. Oznacza to, że następujące dwa wiersze kodu są równoważne.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Typy elastyczne są przydatne w kilku sytuacjach. Na przykład w przypadku wyższych funkcji order (funkcji, która przyjmuje funkcję jako argument) jest często przydatne do funkcji elastyczne typ zwracany. W poniższym przykładzie użycie elastycznym typem z argumentem sekwencji w `iterate2` umożliwia wyższe funkcji kolejność pracy z funkcjami, które generują sekwencje, tablic, list i innego typu wyliczalny.

Należy wziąć pod uwagę następujące dwie funkcje, jeden z zwraca ona sekwencji innych, które zwraca elastycznym typem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Inny przykład należy wziąć pod uwagę [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkcja biblioteki:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Można przekazać dowolny poniższe sekwencje wyliczalny dotyczących wyłącznie tej funkcji:

- Listę list
- Listy tablic
- Array, list
- Tablica sekwencji
- Dowolną kombinację wyliczalny sekwencji

Poniższy kod używa `Seq.concat` aby zademonstrować scenariusze, które mogą być obsługiwane za pomocą typy elastyczne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Dane wyjściowe są następujące:

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

W języku F # tak jak w innych językach obiektowych istnieją kontekstów, w których typy pochodne lub typy, które implementują interfejsy są automatycznie konwertowane na typ podstawowy lub typ interfejsu. Automatycznej konwersji występują w argumentach bezpośredni, ale nie wtedy, gdy typ jest w stanie podrzędny, jako część bardziej złożonych typów, takich jak typ zwracany typ funkcji lub jako argument typu. W związku z tym notacji elastycznym typem jest szczególnie przydatna, gdy typ, który chcesz zastosować go do jest częścią typu bardziej złożone.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy ogólne](generics/index.md)
