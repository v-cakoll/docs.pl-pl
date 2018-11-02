---
title: Potwierdzenia (F#)
description: 'Dowiedz się, jak używać wyrażeń "Potwierdź" jako funkcja debugowania do testowania wyrażenia w języku programowania F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "48842479"
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

Błąd potwierdzenia nie można przechwycić za pomocą obsługi wyjątków w języku F #.

>[!NOTE]
`assert` Funkcji jest rozpoznawane jako <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje użycie `assert` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
