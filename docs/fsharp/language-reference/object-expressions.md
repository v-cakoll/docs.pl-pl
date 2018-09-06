---
title: Wyrażenia obiektów (F#)
description: 'Dowiedz się, jak używać obiektu wyrażeń języka F # uniknąć dodatkowego kodu i czynności wymagane do utworzenia nowego typu nazwanego.'
ms.date: 05/16/2016
ms.openlocfilehash: 1a971044d680d3bf5a6fff38affdaf001d5403b4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865465"
---
# <a name="object-expressions"></a>Wyrażenia obiektów

*Obiektu wyrażenie* to wyrażenie, które tworzy nowe wystąpienie typu utworzony dynamicznie, anonimowy obiekt, który jest oparty na istniejących typu podstawowego, interfejs lub zestawu interfejsów.

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

W poprzedniej składni *typename* reprezentuje istniejącego typu klasy lub typ interfejsu. *Parametry typu* opisano parametry opcjonalne typu ogólnego. *Argumenty* są używane tylko dla typów klasy, które wymagają parametry konstruktora. *Definicje elementów członkowskich* zastąpienia metody klasy bazowej lub implementacji metody abstrakcyjne klasy bazowej lub interfejsu.

W poniższym przykładzie pokazano kilka różnych typów obiektów wyrażeń.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Przy użyciu wyrażeń obiektów

Należy użyć wyrażeń obiektu, jeśli chcesz uniknąć dodatkowego kodu i obciążenie, które jest wymagane do utworzenia nowego typu nazwanego. Jeśli używasz wyrażeń obiektów do minimalizacji liczby typów, utworzone w programie, można zmniejszyć liczbę wierszy kodu i uniknąć niepotrzebnego mnożenia typów. Zamiast tworzyć wiele typów tylko w celu obsługi określonych sytuacjach, można użyć wyrażenie obiektu, który dostosowuje istniejącego typu lub zawiera prawidłową implementacją interfejsu dla określonych przypadków pod ręką.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
