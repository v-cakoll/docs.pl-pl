---
title: 'Kopiowanie i aktualizacja wyrażeń rekordów (F #)'
description: Dowiedz się, jak napisać "Kopiuj i Aktualizuj rekordu wyrażenia" istniejących aktualizacji rekordu, kopiuje określone pola i zwraca zaktualizowanym rekordem.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892272"
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
