---
title: Potwierdzenia (F#)
description: Dowiedz się, jak użyć wyrażenia "Potwierdź" jako funkcja debugowania do testowania wyrażeń w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: fbaf038f08cfc74e6cb262c110322dc586813c0c
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2018
ms.locfileid: "52671925"
---
# <a name="assertions"></a>Potwierdzenia

`assert` Wyrażenie jest funkcją debugowania, można użyć w celu przetestowania wyrażenia. W przypadku awarii w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.

## <a name="syntax"></a>Składnia

```fsharp
assert condition
```

## <a name="remarks"></a>Uwagi

`assert` Wyrażenie zawiera typ `bool -> unit`.

W poprzedniej składni *warunek* reprezentuje wyrażenie logiczne, które ma zostać przetestowana. Jeśli wyrażenie ma `true`, wykonywanie jest kontynuowane bez zmian. Jeśli daje w wyniku `false`, generowany jest okno dialogowe błędu systemu. Okno dialogowe błędu ma podpis, który zawiera ciąg **potwierdzenie nie powiodło się**. Okno dialogowe zawiera ślad stosu, która wskazuje, gdzie wystąpił błąd asercji.

Sprawdzanie potwierdzenia jest włączone, tylko wtedy, gdy kompilujesz w trybie debugowania; oznacza to jeśli stała `DEBUG` jest zdefiniowana. W systemie projektu, domyślnie `DEBUG` stała jest zdefiniowany w konfiguracji debugowania, ale nie w konfiguracji wydania.

Błąd potwierdzenia nie można przechwycić za pomocą F# obsługi wyjątków.

> [!NOTE]
> `assert` Funkcji jest rozpoznawane jako <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje użycie `assert` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
