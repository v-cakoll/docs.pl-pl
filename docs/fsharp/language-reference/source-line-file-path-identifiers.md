---
title: Identyfikatory wiersza źródłowego, pliku i ścieżki
description: Dowiedz się, jak używać wbudowanych F# wartości identyfikatorów, które umożliwiają uzyskiwanie dostępu do źródła wierszy numer, katalogu i nazwa pliku w kodzie.
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656014"
---
# <a name="source-line-file-and-path-identifiers"></a>Identyfikatory wiersza źródłowego, pliku i ścieżki

Identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__` są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogów i plików nazwy w kodzie.

## <a name="syntax"></a>Składnia

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Uwagi

Każda z tych wartości ma typ `string`.

W poniższej tabeli przedstawiono źródła wiersza, pliku i ścieżkę identyfikatorów, które są dostępne w F#. Te identyfikatory nie są makra preprocesora; są one wbudowane wartości, które są rozpoznawane przez kompilator.

|Predefiniowany identyfikator|Opis|
|---------------------|-----------|
|`__LINE__`|Daje w wyniku bieżący numer wiersza, biorąc pod uwagę `#line` dyrektywy.|
|`__SOURCE_DIRECTORY__`|Daje w wyniku pełną ścieżkę bieżącego katalogu źródłowym, biorąc pod uwagę `#line` dyrektywy.|
|`__SOURCE_FILE__`|Ocenia nazwę bieżącego pliku źródłowego i jego ścieżki, biorąc pod uwagę `#line` dyrektywy.|

Aby uzyskać więcej informacji na temat `#line` dyrektywy, zobacz [dyrektywy kompilatora](compiler-directives.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu demonstruje użycie tych wartości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Dane wyjściowe:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Zobacz także

- [Dyrektywy kompilatora](compiler-directives.md)
- [Dokumentacja języka F#](index.md)
