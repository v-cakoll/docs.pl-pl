---
title: "Skróty typów (F#)"
description: "Więcej informacji na temat skróty typów F # umożliwiają typu bardziej zrozumiałej nazwy w celu ułatwienia kodu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a>Skróty typów

A *— skrót typu* jest alias lub alternatywną nazwę typu.

## <a name="syntax"></a>Składnia

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a>Uwagi
Skróty typów umożliwia zapewniają bardziej zrozumiałej nazwy, aby poprawić czytelność kodu typu. Ponadto można użyć do utworzenia łatwy w użyciu nazwy typu, który jest skomplikowane, aby zapisać. Ponadto można użyć skróty typów ułatwiające zmienić typu podstawowego bez zmieniania kodu, który używa typu. Poniżej znajduje się skrót typu prostego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Skróty typów mogą zawierać parametrów ogólnych, zgodnie z poniższym kodem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

W poprzednim kodzie `Transform` jest skrót typu, który reprezentuje funkcję, która pobiera jeden argument typu i która zwraca pojedynczą wartość tego samego typu.

Skróty typów nie są zachowywane w kodzie programu .NET Framework MSIL. W związku z tym gdy używasz zestawu F # z innego języka .NET Framework, należy użyć podstawowej nazwy typu dla skrót typu.

Skróty typów można również na jednostki miary. Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

