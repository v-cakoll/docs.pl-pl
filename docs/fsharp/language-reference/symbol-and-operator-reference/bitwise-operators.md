---
title: Operatory bitowe (F#)
description: 'Więcej informacji na temat operatory bitowe, które są dostępne w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: bc653ae7ff6dd6bc2c269aaba344f073df1fb708
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bitwise-operators"></a>Operatory bitowe

W tym temacie opisano operatory bitowe, które są dostępne w języku F #.

## <a name="summary-of-bitwise-operators"></a>Podsumowanie operatory bitowe
W poniższej tabeli opisano operatory bitowe, które są obsługiwane w przypadku rozpakowany typy całkowite w języku F #.

|Operator|Uwagi|
|--------|-----|
|`&&&`|Bitowy operator AND. Usługa BITS w wyniku ma wartość 1, tylko wtedy, gdy odpowiednich bitów w obu źródłowe argumenty operacji są 1.|
|<code>&#124;&#124;&#124;</code>|Bitowy operator OR. Usługi BITS w wyniku ma wartość 1, jeśli dowolny z odpowiednich bitów w źródle argumenty operacji są 1.|
|`^^^`|Operator wyłączny operator OR. Usługi BITS w wyniku ma wartość 1, tylko wtedy, gdy w źródłowe argumenty operacji mają nierówne wartości.|
|`~~~`|Operator negacji bitowej. To jest operatora jednoargumentowego i zwraca wynik, w którym wszystkie bity 0 w operandu źródła są konwertowane na bitów 1 i wszystkie bity 1 są konwertowane na bitów 0.|
|`<<<`|Bitowy operator przesunięcia w lewo. Wynik jest pierwszy argument operacji z bitami przesunięte liczbę bitów w drugi argument operacji po lewej. Bity przesunąć poza najbardziej znaczących pozycji nie są obracane do najmniej znaczący pozycji. Najmniej znaczących bitów jest uzupełniana zerami z. Typ drugiego argumentu jest `int32`.|
|`>>>`|Bitowy operator przesunięcia w prawo. Wynik jest pierwszym argumentem z bitami przesunięte liczbę bitów w drugi argument operacji po prawej. Bity przesunąć poza najmniej znaczący pozycji nie są obracane do najważniejszych pozycji. Typy bez znaku, aby uzyskać najbardziej znaczących bitów jest uzupełniana zerami z. Typy ze znakiem, aby uzyskać najbardziej znaczących bitów są dopełniane przy tych. Typ drugiego argumentu jest `int32`.|

Następujące typy mogą być używane z bitowego operatory: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, i `unativeint`.

## <a name="see-also"></a>Zobacz też
[Odwołanie do symboli i operatorów](index.md)

[Operatory arytmetyczne](arithmetic-operators.md)

[Operatory logiczne](boolean-operators.md)

