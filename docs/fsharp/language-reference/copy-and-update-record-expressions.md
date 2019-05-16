---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak napisać "Kopiuj i Aktualizuj rekordu wyrażenia" istniejących aktualizacji rekordu, kopiuje określone pola i zwraca zaktualizowanym rekordem.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 7657b0295c9437890baea258295f9e9ab10073dd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645579"
---
# <a name="copy-and-update-record-expressions"></a>Kopiowanie i aktualizacja wyrażeń rekordów

A *kopiowanie i aktualizacja wyrażeń rekordów* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowanym rekordem.

## <a name="syntax"></a>Składnia

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Uwagi

Rekordy są niezmienne domyślnie, tak aby była możliwa ma aktualizacji istniejącego rekordu. Aby utworzyć rekord zaktualizowano wszystkie pola rekordu musi można określić ponownie. Aby ułatwić to zadanie *kopiowanie i aktualizacja wyrażeń rekordów* mogą być używane. To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określone pola z wyrażenia i brakujące pole określona przez wyrażenie.
Może to być przydatne, gdy trzeba skopiować istniejący rekord, a być może zmienić niektóre wartości pól.

Na przykład potrwać nowo utworzony rekord.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Gdyby można zaktualizować tylko na pole tego rekordu można użyć *kopiowanie i aktualizacja wyrażeń rekordów* podobnie do następującego:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Zobacz także

- [Rekordy](records.md)
- [Dokumentacja języka F#](index.md)
