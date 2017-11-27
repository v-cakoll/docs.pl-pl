---
title: Potwierdzenia (F#)
description: "Dowiedz się, jak użyć wyrażenia \"assert\" jako funkcja debugowania do testowania wyrażenia w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

[Dokumentacja języka F #](index.md)
