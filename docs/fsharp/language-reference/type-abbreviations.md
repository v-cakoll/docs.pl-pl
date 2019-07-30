---
title: Skróty typów
description: Dowiedz F# się więcej na temat skrótów typów, aby nadać typ bardziej zrozumiałej nazwy, aby ułatwić odczytywanie kodu.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630211"
---
# <a name="type-abbreviations"></a>Skróty typów

*Skrót typu* jest aliasem lub alternatywną nazwą typu.

## <a name="syntax"></a>Składnia

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Uwagi

Można użyć skrótów typu, aby nadać typ bardziej zrozumiałą nazwę, aby ułatwić odczytywanie kodu. Można ich również użyć do utworzenia łatwej do użycia nazwy dla typu, który w przeciwnym razie jest nieskomplikowany. Ponadto można użyć skrótów typu, aby ułatwić zmianę typu podstawowego bez zmiany całego kodu, który używa tego typu. Poniżej znajduje się prosty skrót typu.

Dostępność nazw skrótów typu jest domyślnie ustawiana na `public`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

Skróty typów mogą zawierać parametry ogólne, jak w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

W poprzednim kodzie, `Transform` jest skrótem typu, który reprezentuje funkcję, która przyjmuje pojedynczy argument dowolnego typu, która zwraca pojedynczą wartość tego samego typu.

Skróty typów nie są zachowywane w kodzie MSIL .NET Framework. W związku z tym, jeśli F# używasz zestawu z innego języka .NET Framework, musisz użyć podstawowej nazwy typu dla skrótu typu.

Skróty typów mogą być również używane w jednostkach miary. Aby uzyskać więcej informacji, zobacz [jednostki miary](units-of-measure.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
