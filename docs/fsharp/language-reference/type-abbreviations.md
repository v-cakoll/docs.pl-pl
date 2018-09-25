---
title: Skróty typów (F#)
description: 'Więcej informacji na temat typu skróty F #, aby zapewnić bardziej opisową nazwę typu w celu zwiększenia czytelności kodu.'
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710751"
---
# <a name="type-abbreviations"></a>Skróty typów

A *— typ skrótu* to alias lub alternatywną nazwę typu.

## <a name="syntax"></a>Składnia

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Uwagi

Skróty typów można użyć, aby zapewnić bardziej opisową nazwę typu w celu zwiększenia czytelności kodu. Umożliwia także je utworzyć łatwy w użyciu nazwy typu, który jest w przeciwnym razie kłopotliwe zapisać. Ponadto można użyć skróty typów ułatwiają zmianę typu podstawowego bez zmiany całego kodu, który używa typu. To jest skrótem typu prostego.

Wartością domyślną jest dostępność skróty typów `public`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Skróty typów mogą zawierać parametrów ogólnych, tak jak w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

W poprzednim kodzie `Transform` jest skrótem typu reprezentujący funkcja, która przyjmuje jeden argument dowolnego typu i który zwraca pojedynczą wartość tego samego typu.

Skróty typów nie są zachowywane w kodzie .NET Framework MSIL. W związku z tym gdy używasz zestawu F # w innym języku .NET Framework, należy użyć podstawowej nazwę typu skrótem typu.

Skróty typów można również w jednostkach miary. Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
