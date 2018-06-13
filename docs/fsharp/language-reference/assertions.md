---
title: Potwierdzenia (F#)
description: 'Dowiedz się, jak użyć wyrażenia "assert" jako funkcja debugowania do testowania wyrażenia w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 83e6cd77bbbb2c32e9b778e5bf6dd9d2e9c8fe32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563149"
---
# <a name="assertions"></a>Potwierdzenia

`assert` Wyrażenie jest funkcja debugowania, którego można używać do testowania wyrażenia. W przypadku awarii w trybie debugowania potwierdzenia generuje okno dialogowe błędu systemu.

## <a name="syntax"></a>Składnia

```fsharp
assert condition
```

## <a name="remarks"></a>Uwagi

`assert` Wyrażenie zawiera typ `bool -> unit`.

W poprzednich składni *warunku* reprezentuje wyrażenie logiczne, która ma zostać przetestowana. Jeśli wyrażenie ma `true`, wykonywanie będzie kontynuowane bez zmian. Jeśli daje w wyniku `false`, generowany jest okno dialogowe błędu systemu. Okno dialogowe błąd ma podpis zawierający ciąg **nie powiodła się Asercja**. Okno dialogowe zawiera ślad stosu, który wskazuje, w którym wystąpił błąd potwierdzenia.

Sprawdzanie potwierdzenia jest włączone tylko wtedy, gdy kompilacja w trybie debugowania; oznacza to, że jeśli stała `DEBUG` jest zdefiniowany. W systemie projektu, domyślnie `DEBUG` stała jest zdefiniowany w konfiguracji debugowania, ale nie w konfiguracji wydanie.

Błąd Błąd potwierdzenia nie można przechwycić przy użyciu obsługi wyjątków F #.

>[!NOTE]
`assert` Rozpoznawany jako funkcja <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono użycie `assert` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a>Zobacz też

[Dokumentacja języka F#](index.md)
