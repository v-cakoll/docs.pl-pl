---
title: "Kopiowanie i aktualizację wyrażenia rekordów (F #)"
description: "Dowiedz się, jak napisać określone pola \"Kopiuj i Aktualizuj rekordu wyrażenia\" który kopiuje istniejących rekordów, aktualizacji i zwraca zaktualizowany rekord."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

[Dokumentacja języka F #](index.md)
