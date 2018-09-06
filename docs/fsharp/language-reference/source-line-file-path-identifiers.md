---
title: Identyfikatory wiersza źródłowego, pliku i ścieżki (F#)
description: 'Dowiedz się, jak używać wbudowanych F # wartości identyfikatorów, które umożliwiają dostęp do numeru wiersza źródłowego, katalogu i nazwa pliku w kodzie.'
ms.date: 05/16/2016
ms.openlocfilehash: 14f710d1412c3420ec627dc30216ba2e89f16bcd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865130"
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

W poniższej tabeli podsumowano wiersza źródłowego, pliku i identyfikatory ścieżki, które są dostępne w języku F #. Te identyfikatory nie są makra preprocesora; są one wbudowane wartości, które są rozpoznawane przez kompilator.

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
