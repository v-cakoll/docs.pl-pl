---
title: Delegaty (F#)
description: 'Dowiedz się, jak pracować z delegatów w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 56520cc631d889f390a7d4300be1cb3185306be9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="delegates"></a>Delegaty

Delegat reprezentuje wywołanie funkcji jako obiekt. W języku F # zazwyczaj należy użyć wartości funkcji do reprezentowania funkcje jako wartości pierwszej klasy; jednak delegatów są używane w programie .NET Framework i dlatego są wymagane, gdy współdziałać z interfejsów API, który będzie je. Może również być używane tworzenia bibliotek przeznaczony do użycia z innych języków .NET Framework.


## <a name="syntax"></a>Składnia

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Uwagi
W poprzednich składni `type1` reprezentuje typ argumentu lub typów i `type2` reprezentuje typ zwracany. Typy argumentów, które są reprezentowane przez `type1` są automatycznie curried. Sugeruje to, że dla tego typu formularz krotki Jeśli argumentów funkcji docelowej są curried i krotka ujętego w nawiasy dla argumentów, które znajdują się już w postaci spójnej kolekcji. Automatyczne currying usuwa zestaw nawiasów, pozostawiając argumentu spójnej kolekcji, który pasuje do metody docelowej. Zapoznaj się przykładowy kod składni, które powinny być używane w każdym przypadku.

Obiekty delegowane może zostać dołączony do F # funkcja wartości i statyczne lub wystąpienie metody. Bezpośrednio jako argumenty do delegowania Konstruktory mogą być przekazywane wartości funkcji języka F #. Dla metody statycznej utworzymy przy użyciu nazwy klasy i metody obiektu delegowanego. Dla metody wystąpienia musisz podać wystąpienie obiektu i metody w jeden argument. W obu przypadkach dostęp do elementu członkowskiego operatora (`.`) jest używany.

`Invoke` Metody w typie delegata wywołuje funkcję hermetyzowany. Ponadto delegatów mogą być przekazywane jako wartości funkcji, odwołując nazwę metody Invoke bez nawiasów.

Poniższy kod przedstawia składnię służący do tworzenia delegatów, które reprezentują różne metody w klasie. W zależności od tego, czy metoda jest metodą statyczną lub metodą wystąpienia oraz czy ma argumentów w postaci spójnej kolekcji lub w formularzu rozwinięte składnia deklarowanie i przypisywanie delegat jest nieco inne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Poniższy kod przedstawia niektóre różne sposoby, którymi można pracować z obiektów delegowanych.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Poniżej przedstawiono dane wyjściowe w poprzednim przykładzie kodu.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Parametry i argumenty](parameters-and-arguments.md)

[Zdarzenia](members/events.md)
