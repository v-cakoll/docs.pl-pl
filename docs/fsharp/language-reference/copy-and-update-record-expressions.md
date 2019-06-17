---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak pisać "Kopiuj i Aktualizuj wyrażenia" kopiuje istniejącego rekordu lub rekordów anonimowe, aktualizacje określone pola i zwraca zaktualizowanym rekordem lub anonimowe rekordu.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041730"
---
# <a name="copy-and-update-record-expressions"></a>Kopiowanie i aktualizacja wyrażeń rekordów

A *kopiowanie i aktualizacja wyrażeń rekordów* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowanym rekordem.

## <a name="syntax"></a>Składnia

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Uwagi

Rekordów i rekordów anonimowe są niezmienne domyślnie, dzięki czemu możliwe nie ma aktualizacji istniejącego rekordu. Aby utworzyć rekord zaktualizowano wszystkie pola rekordu musi można określić ponownie. Aby ułatwić to zadanie *Kopiuj i Aktualizuj wyrażenie* mogą być używane. To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określone pola z wyrażenia i brakujące pole określona przez wyrażenie.

Może to być przydatne, gdy trzeba skopiować istniejący rekord, a być może zmienić niektóre wartości pól.

Na przykład potrwać nowo utworzony rekord.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Gdyby można zaktualizować tylko na pole tego rekordu można użyć *kopiowanie i aktualizacja wyrażeń rekordów* podobnie do następującego:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Zobacz także

- [Rekordy](records.md)
- [Rekordy anonimowe](anonymous-records.md)
- [Dokumentacja języka F#](index.md)
