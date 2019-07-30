---
title: Funkcje śródwierszowe
description: Dowiedz się, F# jak używać funkcji wbudowanych, które są zintegrowane bezpośrednio z wywoływanym kodem.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630680"
---
# <a name="inline-functions"></a>Funkcje śródwierszowe

*Funkcje wbudowane* to funkcje, które są zintegrowane bezpośrednio z wywoływanym kodem.

## <a name="using-inline-functions"></a>Korzystanie z funkcji wbudowanych

W przypadku używania parametrów typu statycznego wszystkie funkcje, które są sparametryzowane przez parametry typu, muszą być wbudowane. Gwarantuje to, że kompilator może rozpoznać te parametry typu. W przypadku używania zwykłych parametrów typu ogólnego nie ma takich ograniczeń.

Oprócz włączania ograniczeń elementu członkowskiego funkcje wbudowane mogą być pomocne podczas optymalizowania kodu. Jednak użycie funkcji wbudowanych może spowodować, że kod będzie mniej odporny na zmiany optymalizacji kompilatora i implementację funkcji biblioteki. Z tego powodu należy unikać używania funkcji wbudowanych do optymalizacji, chyba że ponowią wszystkie inne techniki optymalizacji. Wprowadzenie funkcji lub metody w tekście może czasami zwiększyć wydajność, ale nie zawsze jest to przypadek. W związku z tym należy również użyć pomiarów wydajności, aby upewnić się, że udostępnianie każdej funkcji wbudowanej w rzeczywistości ma pozytywny wpływ.

`inline` Modyfikator można zastosować do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody klasy.

Poniższy przykład kodu ilustruje funkcję wbudowaną na najwyższym poziomie, wbudowaną metodę wystąpienia i wbudowaną metodę statyczną.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Funkcje śródwierszowe i wnioskowanie o typie

Obecność `inline` ma wpływ na wnioskowanie o typie. Wynika to z faktu, że funkcje wbudowane mogą mieć statycznie rozpoznane parametry typu, podczas gdy nie można korzystać z funkcji wbudowanych. Poniższy przykład kodu pokazuje przypadek, gdzie `inline` jest przydatne, ponieważ używana jest funkcja, która ma parametr typu statycznie rozpoznany `float` , Operator konwersji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Bez modyfikatora, wnioskowanie typu wymusza, aby funkcja przejęcia określonego typu w tym przypadku `int`. `inline` Ale z `inline` modyfikatorem, funkcja jest również wnioskowana, aby miał statycznie rozpoznany parametr typu. `inline` Z modyfikatorem, typ jest wywnioskowany jako następujący:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Oznacza to, że funkcja akceptuje dowolny typ, który obsługuje konwersjęna wartość zmiennoprzecinkową.

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
- [Ograniczenia](../generics/constraints.md)
- [Statycznie rozwiązywane parametry typu](../generics/statically-resolved-type-parameters.md)
