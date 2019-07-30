---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak napisać "Copy and Update Expression", który kopiuje istniejący rekord lub rekord anonimowy, aktualizuje określone pola i zwraca zaktualizowany rekord lub rekord anonimowy.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630380"
---
# <a name="copy-and-update-record-expressions"></a>Kopiowanie i aktualizacja wyrażeń rekordów

*Wyrażenie Copy and Update Record* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowany rekord.

## <a name="syntax"></a>Składnia

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Uwagi

Rekordy i rekordy anonimowe są domyślnie niezmienne, dlatego nie ma możliwości aktualizacji istniejącego rekordu. Aby utworzyć zaktualizowany rekord, należy ponownie określić wszystkie pola rekordu. Aby uprościć to zadanie, można użyć *wyrażenia kopiowania i aktualizowania* . To wyrażenie przyjmuje istniejący rekord, tworzy nowy jeden z tego samego typu przy użyciu określonych pól z wyrażenia i brakującego pola określonego przez wyrażenie.

Może to być przydatne, gdy konieczne jest skopiowanie istniejącego rekordu i prawdopodobnie zmiana niektórych wartości pól.

Zrób wystąpienie nowo utworzonego rekordu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Jeśli aktualizacja dotyczy tylko pola tego rekordu, można użyć *wyrażenia Kopiuj i Aktualizuj rekord* w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Zobacz także

- [Rekordy](records.md)
- [Rekordy anonimowe](anonymous-records.md)
- [Dokumentacja języka F#](index.md)
