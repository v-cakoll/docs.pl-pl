---
title: Operatory bitowe (F#)
description: 'Więcej informacji na temat operatory bitowe, które są dostępne w F # języka programowania.'
ms.date: 07/20/2018
ms.openlocfilehash: ed76fcf5f9c569a2f288cf260e99dc29fd65ef3b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205242"
---
# <a name="bitwise-operators"></a>Operatory bitowe

W tym temacie opisano operatory bitowe, które są dostępne w języku F #.

## <a name="summary-of-bitwise-operators"></a>Podsumowanie operatory bitowe

W poniższej tabeli opisano operatory bitowe, które są obsługiwane w przypadku rozpakowany typów całkowitych w języku F #.

|Operator|Uwagi|
|--------|-----|
|`&&&`|Bitowy operator AND. Usługi BITS w wyniku ma wartość 1, tylko wtedy, gdy odpowiednich bitów w oba operandy źródło to 1.|
|<code>&#124;&#124;&#124;</code>|Bitowy operator OR. Usługa BITS w wyniku ma wartość 1, jeśli odpowiednich bitów w źródle operandy są 1.|
|`^^^`|Bitowe or wyłączny operator OR. Usługa BITS w wyniku ma wartość 1, tylko wtedy, gdy usługi bits w źródłowe argumenty operacji mają różne wartości.|
|`~~~`|Operator negacji bitowej. Jest operator jednoargumentowy i daje wynik, w którym wszystkie bity 0 w operandu źródła są konwertowane na bitów 1, a wszystkie bity 1 są konwertowane na bitów 0.|
|`<<<`|Bitowy operator przesunięcia w lewo. Wynik jest pierwszy operand z bitami przesunięte liczbę bitów w drugim argumencie operacji po lewej stronie. Przesunięte poza pozycji najbardziej znaczące bity nie są obracane do najmniej znaczących określonej pozycji. Co najmniej znaczące bity są dopełniane zerami. Typ drugiego argumentu jest `int32`.|
|`>>>`|Bitowy operator przesunięcia w prawo. Wynik jest pierwszym operandem z bitami przesunięte w prawo o liczbę bitów w drugim argumencie operacji. Bity przesunięte poza najmniej znaczący pozycji nie są obracane do najważniejszych pozycji. Typy bez znaku, aby uzyskać najbardziej znaczące bity są dopełniane zerami. Na typy ze znakiem z wartości ujemnych najbardziej znaczące bity są dopełniane przy użyciu tych. Typ drugiego argumentu jest `int32`.|

Następujące typy mogą być używane z operatorów bitowe: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, i `unativeint`.

## <a name="see-also"></a>Zobacz także

- [Odwołanie do symboli i operatorów](index.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Operatory logiczne](boolean-operators.md)
