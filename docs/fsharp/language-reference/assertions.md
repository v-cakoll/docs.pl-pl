---
title: Potwierdzenia
description: Dowiedz się, jak używać wyrażenia "Assert" jako funkcji debugowania do testowania wyrażeń w języku F# programowania.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799065"
---
# <a name="assertions"></a>Potwierdzenia

Wyrażenie `assert` jest funkcją debugowania, której można użyć do przetestowania wyrażenia. W przypadku niepowodzenia w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.

## <a name="syntax"></a>Składnia

```fsharp
assert condition
```

## <a name="remarks"></a>Uwagi

Wyrażenie `assert` ma `bool -> unit`typu.

Funkcja `assert` jest rozpoznawana jako <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>. Oznacza to, że jego zachowanie jest takie samo jak wywołanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> bezpośrednio.

Sprawdzanie potwierdzenia jest włączone tylko w przypadku kompilowania w trybie debugowania. oznacza to, że jeśli stała `DEBUG` jest zdefiniowana. Domyślnie w systemie projektu stała `DEBUG` jest definiowana w konfiguracji debugowania, ale nie w konfiguracji wydania.

Błąd potwierdzenia nie może zostać przechwycony przy użyciu F# obsługi wyjątków.

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje użycie wyrażenia `assert`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
