---
title: Wyrażenia obiektów (F#)
description: 'Dowiedz się, jak używać wyrażeń obiektu F #, jeśli chcesz uniknąć dodatkowego kodu i dodatkowych czynności wymaganych do utworzenia nowej, o nazwie typu.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f5a728823e7abe18aeb604b3991087fd0252698e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="object-expressions"></a>Wyrażenia obiektów

*Obiekt wyrażenie* jest wyrażenie, które tworzy nowe wystąpienie typu obiektu utworzony dynamicznie, anonimowy, który jest oparty na istniejący typ podstawowy, interfejsu lub zestawu interfejsów.


## <a name="syntax"></a>Składnia

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Uwagi
W poprzednich składni *typename* reprezentuje istniejącego typu klasy lub interfejsu. *Parametry typu* opisano parametry opcjonalne typu ogólnego. *Argumenty* są używane tylko dla typu klasy, które wymagają parametrami konstruktora. *Definicji elementu członkowskiego* przesłonięcia metod klasy podstawowej lub implementacje metody abstrakcyjne klasy podstawowej lub interfejsu.

Poniższy przykład przedstawia różne rodzaje wyrażeń obiektów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Przy użyciu wyrażeń obiektów
Wyrażenia obiektów jest używane, gdy chce się uniknąć dodatkowego kodu i obciążenie, które jest wymagane do utworzenia nowej, o nazwie typu. Użycie wyrażenia obiektu do minimalizacji liczby typów utworzony w programie, można zmniejszyć liczbę wierszy kodu i uniknąć niepotrzebnego mnożenia typów. Zamiast tworzyć wiele typów tylko w celu obsługi określonych sytuacji, używając wyrażenie obiektu, który dostosowuje istniejącego typu lub zapewnia odpowiedniej implementacji interfejsu w przypadku określonych.


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)
