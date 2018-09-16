---
title: Funkcje śródwierszowe (F#)
description: 'Dowiedz się, jak używać języka F # funkcji śródwierszowych wbudowane bezpośrednio w kodzie.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685676"
---
# <a name="inline-functions"></a>Funkcje śródwierszowe

*Funkcje śródwierszowe* funkcji, które są zintegrowane bezpośrednio w kodzie wywołującym.

## <a name="using-inline-functions"></a>Za pomocą funkcji śródwierszowych

Gdy używasz statycznych parametrów typu, wszystkie funkcje, które są parametryzowane przez parametry typu musi być wbudowany. Gwarantuje to, że kompilator może rozpoznać te parametry typu. Korzystając z parametrami typu generycznego zwykłych istnieje nie tego ograniczenia.

Inne niż umożliwiające korzystanie z ograniczeniami elementu członkowskiego, wbudowane funkcje może być pomocne w optymalizacji kodu. Jednak nadużyciami wbudowanych funkcji może spowodować kodu jako mniej odporne na zmiany w optymalizacji kompilatora i stosowania funkcji biblioteki. Z tego powodu należy unikać używania wbudowane funkcje optymalizacji, chyba że Wypróbowano innych technik optymalizacji. Co wbudowanej funkcji lub metody czasami może poprawić wydajność, ale nie zawsze jest wymagane. W związku z tym aby sprawdzić, dzięki czemu wszystkie wbudowane daną funkcję w rzeczywistości ma pozytywny wpływ należy również użyć pomiarów wydajności.

`inline` Modyfikator może odnosić się do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody w klasie.

Poniższy przykład kodu ilustruje funkcja śródwierszowa najwyższego poziomu, metoda wystąpienia wbudowane i wbudowane metody statycznej.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>Funkcje śródwierszowe i wnioskowanie o typie

Obecność `inline` wpływa na wnioskowanie o typie. Jest to spowodowane wbudowane funkcje mogą mieć parametry typu statycznie rozpoznanych, natomiast nie funkcji innych niż inline. Poniższy przykład kodu pokazuje przypadek gdzie `inline` jest przydatne, ponieważ korzysta z funkcji, która ma parametr typu statycznie rozpoznanych `float` operatora konwersji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Bez `inline` modyfikator, wnioskowanie o typie wymusza funkcji w celu określonego typu, w tym przypadku `int`. Ale `inline` modyfikator, funkcja również wywnioskowana ma parametr typu statycznie rozpoznanych. Za pomocą `inline` modyfikator, typ jest wnioskowany być następujące:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Oznacza to, że funkcja ta akceptuje dowolny typ, który obsługuje konwersję **float**.

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
- [Ograniczenia](../generics/constraints.md)
- [Statycznie rozwiązywane parametry typu](../generics/statically-resolved-type-parameters.md)
