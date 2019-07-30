---
title: Potwierdzenia
description: Dowiedz się, jak używać wyrażenia "Assert" jako funkcji debugowania do testowania wyrażeń w języku F# programowania.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630025"
---
# <a name="assertions"></a>Potwierdzenia

`assert` Wyrażenie jest funkcją debugowania, której można użyć do przetestowania wyrażenia. W przypadku niepowodzenia w trybie debugowania potwierdzenie generuje okno dialogowe błędu systemu.

## <a name="syntax"></a>Składnia

```fsharp
assert condition
```

## <a name="remarks"></a>Uwagi

Wyrażenie ma typ `bool -> unit`. `assert`

W poprzedniej składni *warunek* reprezentuje wyrażenie logiczne, które ma zostać przetestowane. Jeśli wyrażenie zwróci wartość `true`, wykonanie nie będzie miało żadnych zmian. Jeśli zostanie obliczona `false`wartość, zostanie wygenerowane okno dialogowe błędu systemu. Okno dialogowe błędu zawiera podpis zawierający **potwierdzenie ciągu nie powiodło się**. Okno dialogowe zawiera ślad stosu, który wskazuje, gdzie wystąpił błąd potwierdzenia.

Sprawdzanie potwierdzenia jest włączone tylko w przypadku kompilowania w trybie debugowania. oznacza to, że jeśli stała `DEBUG` jest zdefiniowana. Domyślnie w systemie projektu `DEBUG` stała jest definiowana w konfiguracji debugowania, ale nie w konfiguracji wydania.

Błąd potwierdzenia nie może zostać przechwycony przy użyciu F# obsługi wyjątków.

> [!NOTE]
> Funkcja `assert` jest<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>rozpoznawana jako.

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje użycie `assert` wyrażenia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
