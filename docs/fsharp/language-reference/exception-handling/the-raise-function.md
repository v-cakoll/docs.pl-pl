---
title: 'Wyjątki: raise — Funkcja'
description: Dowiedz się F# , jak funkcja "podnoszenie" służy do wskazywania, że wystąpił błąd lub wyjątkowy warunek.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630289"
---
# <a name="exceptions-the-raise-function"></a>Wyjątki: raise — Funkcja

`raise` Funkcja służy do wskazywania, że wystąpił błąd lub wyjątkowy warunek. Informacje o błędzie są przechwytywane w obiekcie wyjątku.

## <a name="syntax"></a>Składnia

```fsharp
raise (expression)
```

## <a name="remarks"></a>Uwagi

`raise` Funkcja generuje obiekt wyjątku i inicjuje proces odwinięcia stosu. Proces odwinięcia stosu jest zarządzany przez środowisko uruchomieniowe języka wspólnego (CLR), dzięki czemu zachowanie tego procesu jest takie samo, jak w przypadku dowolnego innego języka .NET. Proces odwinięcia stosu jest wyszukiwaniem programu obsługi wyjątków, który pasuje do wygenerowanego wyjątku. Wyszukiwanie rozpocznie się w bieżącym `try...with` wyrażeniu, jeśli istnieje. Każdy wzorzec w `with` bloku jest zaznaczony w kolejności. Po znalezieniu pasującej obsługi wyjątków wyjątek jest uznawany za obsłużony; w przeciwnym razie stos zostanie odtworzony i `with` zablokuje łańcuch wywołań, dopóki nie zostanie znaleziona zgodna procedura obsługi. Wszystkie `finally` bloki, które są napotkane w łańcuchu wywołań są również wykonywane sekwencyjnie jako rozwinięcia stosu.

Funkcja jest odpowiednikiem C# w lub C++ `throw` `raise` Użyj `reraise` w procedurze obsługi catch, aby propagować ten sam wyjątek w łańcuchu wywołań.

Poniższy przykład kodu ilustruje użycie `raise` funkcji do wygenerowania wyjątku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

`raise` Funkcja może również służyć do wywoływania wyjątków platformy .NET, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...with` Wyrażenie](the-try-with-expression.md)
- [Wyjątki: `try...finally` Wyrażenie](the-try-finally-expression.md)
- [Wyjątki: `failwith` Funkcja](the-failwith-function.md)
- [Wyjątki: `invalidArg` Funkcja](the-invalidArg-function.md)
