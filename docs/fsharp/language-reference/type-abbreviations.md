---
title: Skróty typów (F#)
description: 'Więcej informacji na temat skróty typów F # umożliwiają typu bardziej zrozumiałej nazwy w celu ułatwienia kodu.'
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="type-abbreviations"></a>Skróty typów

A *— skrót typu* jest alias lub alternatywną nazwę typu.

## <a name="syntax"></a>Składnia

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Uwagi
Skróty typów umożliwia zapewniają bardziej zrozumiałej nazwy, aby poprawić czytelność kodu typu. Ponadto można użyć do utworzenia łatwy w użyciu nazwy typu, który jest skomplikowane, aby zapisać. Ponadto można użyć skróty typów ułatwiające zmienić typu podstawowego bez zmieniania kodu, który używa typu. Poniżej znajduje się skrót typu prostego.

Domyślnie dostępności skróty typów `public`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Skróty typów mogą zawierać parametrów ogólnych, zgodnie z poniższym kodem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

W poprzednim kodzie `Transform` jest skrót typu, który reprezentuje funkcję, która pobiera jeden argument typu i która zwraca pojedynczą wartość tego samego typu.

Skróty typów nie są zachowywane w kodzie programu .NET Framework MSIL. W związku z tym gdy używasz zestawu F # z innego języka .NET Framework, należy użyć podstawowej nazwy typu dla skrót typu.

Skróty typów można również na jednostki miary. Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

