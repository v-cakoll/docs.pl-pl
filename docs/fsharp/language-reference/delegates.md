---
title: Delegaty
description: Dowiedz się, jak korzystać z F#delegatów w programie.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630370"
---
# <a name="delegates"></a>Delegaty

Delegat reprezentuje wywołanie funkcji jako obiekt. W F#programie zazwyczaj należy używać wartości funkcji do reprezentowania funkcji jako wartości pierwszej klasy; Jednakże Delegaty są używane w .NET Framework i dlatego są potrzebne podczas współpracy z interfejsami API, które oczekują. Mogą być również używane podczas tworzenia bibliotek przeznaczonych do użycia w innych językach .NET Framework.

## <a name="syntax"></a>Składnia

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni, `type1` reprezentuje typ argumentu lub typy i `type2` reprezentuje zwracany typ. Typy argumentów, które są reprezentowane przez `type1` są automatycznie rozwinięte. Sugeruje to, że dla tego typu używasz formularza spójnego, jeśli argumenty funkcji docelowej to rozwinięte, a krotka w nawiasach dla argumentów, które znajdują się już w formularzu krotki. Automatyczna currying usuwa zestaw nawiasów, pozostawiając argument krotki pasujący do metody docelowej. Zapoznaj się z przykładem kodu dla składni, która powinna być używana w każdym przypadku.

Delegaty mogą być dołączane do F# wartości funkcji i statycznych lub wystąpień metod. F#wartości funkcji można przekazać bezpośrednio jako argumenty do delegatów konstruktorów. Dla metody statycznej można skonstruować delegata przy użyciu nazwy klasy i metody. Dla metody wystąpienia, należy podać wystąpienie obiektu i metodę w jednym argumencie. W obu przypadkach używany jest operator dostępu do elementu`.`członkowskiego ().

`Invoke` Metoda w typie delegata wywołuje funkcję hermetyzowaną. Ponadto Delegaty mogą być przesyłane jako wartości funkcji przez odwołanie się do nazwy metody Invoke bez nawiasów.

Poniższy kod przedstawia składnię tworzenia delegatów reprezentujących różne metody w klasie. W zależności od tego, czy metoda jest metodą statyczną czy metodą wystąpienia i czy ma argumenty w formularzu krotki lub formularzu rozwinięte, składnia do deklarowania i przypisywania delegata jest nieco inna.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Poniższy kod przedstawia niektóre różne sposoby pracy z delegatami.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Poniżej przedstawiono dane wyjściowe poprzedniego kodu.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Parametry i argumenty](parameters-and-arguments.md)
- [Zdarzenia](./members/events.md)
