---
title: 'Kopiowanie i aktualizację wyrażenia rekordów (F #)'
description: Dowiedz się, jak napisać określone pola "Kopiuj i Aktualizuj rekordu wyrażenia" który kopiuje istniejących rekordów, aktualizacji i zwraca zaktualizowany rekord.
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 98a515b5f053e9339588157185848e8315a580f4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="copy-and-update-record-expressions"></a>Kopiowanie i aktualizację wyrażenia rekordów

A *kopiowanie i aktualizację wyrażenia rekordu* jest wyrażenie, które kopiuje istniejącego rekordu, aktualizuje określone pola i zwraca zaktualizowany rekord.


## <a name="syntax"></a>Składnia

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Uwagi
Rekordy są niezmienne domyślnie, dzięki czemu możliwe jest Brak aktualizacji do istniejącego rekordu. Aby utworzyć rekord zaktualizowane wszystkie pola rekordu musi mieścić się ponownie. Aby uprościć zadanie *kopiowanie i aktualizację wyrażenia rekordu* mogą być używane. To wyrażenie ma istniejącego rekordu, tworzy nową tego samego typu przy użyciu określonego pola z wyrażenia i brakujące pole określona przez wyrażenie.
Może to być przydatne, gdy trzeba skopiować istniejącego rekordu i prawdopodobnie zmieniają niektóre wartości pól.

Na przykład zająć nowo utworzony rekord.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Jeśli masz zamiar aktualizacji tylko na pola rekordu można użyć *kopiowanie i aktualizację wyrażenia rekordu* podobnie do następującego:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Zobacz też
[Rekordy](records.md)

[Dokumentacja języka F#](index.md)
