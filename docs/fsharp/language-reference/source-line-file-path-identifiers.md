---
title: Identyfikatory wiersza źródłowego, pliku i ścieżki (F#)
description: 'Dowiedz się, jak używać wbudowanych F # identyfikator wartości, które umożliwiają dostęp do numeru wiersza źródłowego, katalogu i nazwa pliku w kodzie.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 18a26f0aa0a0c1f9c0b448ec46eaebd540391324
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="source-line-file-and-path-identifiers"></a>Identyfikatory wiersza źródłowego, pliku i ścieżki

Identyfikatory `__LINE__`, `__SOURCE_DIRECTORY__` i `__SOURCE_FILE__` są wbudowane wartości, które umożliwiają dostęp do źródła wiersza numer, katalogu i nazwa pliku w kodzie.


## <a name="syntax"></a>Składnia

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Uwagi
Każda z tych wartości ma typ `string`.

W poniższej tabeli przedstawiono wiersza źródłowego, pliku i ścieżki identyfikatorów, które są dostępne w języku F #. Te identyfikatory nie są makra preprocesora; są one wbudowane wartości, które są rozpoznawane przez kompilator.

|Identyfikator wstępnie zdefiniowane|Opis|
|---------------------|-----------|
|`__LINE__`|Zwraca bieżący numer wiersza, biorąc pod uwagę `#line` dyrektywy.|
|`__SOURCE_DIRECTORY__`|Daje w wyniku bieżącej pełną ścieżkę katalogu źródłowego uwzględnieniu `#line` dyrektywy.|
|`__SOURCE_FILE__`|Daje w wyniku bieżącej nazwy pliku źródłowego i jego ścieżki, biorąc pod uwagę `#line` dyrektywy.|
Aby uzyskać więcej informacji na temat `#line` dyrektywy, zobacz [dyrektywy kompilatora](compiler-directives.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje użycie tych wartości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Dane wyjściowe:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Zobacz też
[Dyrektywy kompilatora](compiler-directives.md)

[Dokumentacja języka F#](index.md)
