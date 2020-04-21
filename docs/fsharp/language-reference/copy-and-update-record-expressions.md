---
title: Kopiowanie i aktualizacja wyrażeń rekordów
description: Dowiedz się, jak napisać wyrażenie "kopiuj i aktualizuj" kopiuje istniejący rekord lub rekord anonimowy, aktualizuje określone pola i zwraca zaktualizowany rekord lub rekord anonimowy.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739286"
---
# <a name="copy-and-update-record-expressions"></a>Kopiowanie i aktualizacja wyrażeń rekordów

*Wyrażenie kopiowania i aktualizowania rekordu* jest wyrażeniem, które kopiuje istniejący rekord, aktualizuje określone pola i zwraca zaktualizowany rekord.

## <a name="syntax"></a>Składnia

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Uwagi

Rekordy i rekordy anonimowe są domyślnie niezmienne, więc nie można zaktualizować istniejącego rekordu. Aby utworzyć zaktualizowany rekord, wszystkie pola rekordu musiałyby zostać ponownie określone. Aby uprościć to zadanie, można użyć *wyrażenia kopiowania i aktualizacji.* To wyrażenie przyjmuje istniejący rekord, tworzy nowy tego samego typu przy użyciu określonych pól z wyrażenia i brakujące pole określone przez wyrażenie.

Może to być przydatne, gdy trzeba skopiować istniejący rekord i ewentualnie zmienić niektóre wartości pól.

Weźmy na przykład nowo utworzony rekord.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Aby zaktualizować tylko dwa pola w tym rekordzie, można użyć *wyrażenia rekordu kopiowania i aktualizowania:*

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Zobacz też

- [Rekordy](records.md)
- [Rekordy anonimowe](anonymous-records.md)
- [Odwołanie do języka F#](index.md)
