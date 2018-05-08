---
title: 'Wyjątki: raise — Funkcja (F#)'
description: 'Dowiedz się, jak F # "raise" funkcja służy do wskazują, że wystąpił błąd lub wyjątkowych warunku.'
ms.date: 05/16/2016
ms.openlocfilehash: bad18bfbccd738a12e16a0e026ade22e96d4cfcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-raise-function"></a>Wyjątki: raise — Funkcja

`raise` Funkcja służy do wskazują, że wystąpił błąd lub wyjątkowych warunku. Obiekt wyjątku jest przechwytywane informacje o tym błędzie.


## <a name="syntax"></a>Składnia

```fsharp
raise (expression)
```

## <a name="remarks"></a>Uwagi
`raise` Funkcji generuje obiekt wyjątku i inicjuje proces odwijanie stosu. Proces odwijaniem stosu jest zarządzana przez środowisko uruchomieniowe języka wspólnego (CLR), dlatego działanie tego procesu jest taka sama jak w dowolnym języku .NET. Proces odwijaniem stosu jest wyszukiwania dla obsługi wyjątków odpowiadający wygenerowany wyjątek. Wyszukiwanie rozpoczyna się w bieżącym `try...with` wyrażenia, jeśli istnieje. W każdym wzorca `with` bloku zaznaczono w kolejności. W przypadku odnalezienia pasującego obsługi wyjątków wyjątek jest uznawany za obsługiwany; w przeciwnym razie stos jest oddzielić i `with` bloki zapasowej łańcuch wywołań są zaznaczone, aż do znalezienia zgodnego programu obsługi. Wszelkie `finally` bloków, które występują w łańcuchu wywołań także są wykonywane w kolejności jako cofa stosu.

`raise` Funkcji jest odpowiednikiem `throw` w języku C# lub języka C++. Użyj `reraise` w procedurze obsługi catch propagację ten sam wyjątek zapasowej łańcuch wywołań.

Następujący przykładowy kod, przedstawiający zastosowanie `raise` funkcji do generowania wyjątku.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` Funkcji można również zgłaszać wyjątki .NET, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>Zobacz też
[Obsługa wyjątków](index.md)

[Typy wyjątków](exception-types.md)

[Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)

[Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)

[Wyjątki: `failwith` — funkcja](the-failwith-function.md)

[Wyjątki: `invalidArg` — funkcja](the-invalidArg-function.md)
