---
title: 'Wyjątki: raise — Funkcja (F#)'
description: Dowiedz się, jak funkcja języka F# "raise" jest używany do wskazania, że wystąpił błąd lub wyjątkowy warunek.
ms.date: 05/16/2016
ms.openlocfilehash: 537d274659d29404380bfdd56310ac267372bb98
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43778262"
---
# <a name="exceptions-the-raise-function"></a>Wyjątki: raise — Funkcja

`raise` Funkcji jest używany do wskazania, że wystąpił błąd lub wyjątkowy warunek. Informacje o błędzie są przechwytywane w obiekt wyjątku.

## <a name="syntax"></a>Składnia

```fsharp
raise (expression)
```

## <a name="remarks"></a>Uwagi

`raise` Funkcja generuje obiekt wyjątku i inicjuje proces odwijanie stosu. Proces odwijania stosu jest zarządzany przez środowisko uruchomieniowe języka wspólnego (CLR), więc zachowanie tego procesu jest taka sama jak w dowolnym języku .NET. Proces odwijania stosu jest wyszukiwanie do obsługi wyjątku, który odpowiada wygenerowany wyjątek. Wyszukiwanie rozpoczyna się w bieżącym `try...with` wyrażenia, jeśli taka istnieje. Każdy wzorzec w `with` bloku jest zaznaczone, w kolejności. W przypadku odnalezienia pasującego obsługi wyjątków wyjątek jest uznawany za obsługiwany; w przeciwnym razie stos jest odwijany, i `with` bloki łańcuch wywołań są sprawdzane, dopóki nie znaleziono pasującej klauzuli obsługi. Wszelkie `finally` bloki, które wystąpią w łańcuchu wywołań także są wykonywane w kolejności, jak rozwija stos.

`raise` Funkcji jest odpowiednikiem `throw` w języku C# lub C++. Użyj `reraise` w obsługi catch do propagowania ten sam wyjątek łańcuch wywołań.

Poniższe przykłady kodu ilustrują używanie `raise` funkcję, aby wygenerować wyjątek.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` Funkcji można również zgłaszać wyjątki .NET, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)
- [Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)
- [Wyjątki: `failwith` — funkcja](the-failwith-function.md)
- [Wyjątki: `invalidArg` — funkcja](the-invalidArg-function.md)
