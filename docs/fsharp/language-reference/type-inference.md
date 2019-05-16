---
title: Wnioskowanie o typie
description: Dowiedz się, jak F# kompilator wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.
ms.date: 05/16/2016
ms.openlocfilehash: ab1a4aa8df4312287df749d5d6d0ea2858091152
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641677"
---
# <a name="type-inference"></a>Wnioskowanie o typie

W tym temacie opisano sposób, w jaki F# kompilator wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.

## <a name="type-inference-in-general"></a>Wnioskowanie o typie ogólnie rzecz biorąc

Koncepcja wnioskowanie o typie jest, że trzeba określić typy F# konstrukcji, z wyjątkiem sytuacji, gdy kompilator ostatecznie nie można wywnioskować typu. Pomijanie informacji o typie jawne nie oznacza to, że F# jest dynamicznie typizowanym językiem, lub że wartości w F# czy ze słabą kontrolą typów. F#jest statycznie typizowanym językiem, co oznacza, że kompilator wywnioskowuje, że typem dokładne dla każdego konstrukcji podczas kompilacji. Jeśli nie jest wystarczająco dużo informacji dla kompilatora wywnioskowanie typów każdego konstrukcji, dodatkowy typ informacji, musisz podać zwykle przez dodawanie adnotacji typu jawnego gdzieś w kodzie.

## <a name="inference-of-parameter-and-return-types"></a>Wnioskowanie parametrów i zwracanych typów

Na liście parametrów nie należy określić typ każdego parametru. I jeszcze F# jest statycznie typizowanym językiem, a w związku z tym każdy wartość i wyrażenie ma określony typ w czasie kompilacji. Dla tych typów, które nie są jawnie określone kompilator wnioskuje typ na podstawie kontekstu. Jeśli typ nie jest w przeciwnym razie określone, wynika to ogólny. Jeśli kod używa wartości niespójnie, w taki sposób, to nie pojedynczy wywnioskować typ, który spełnia wszystkie przypadki użycia wartości, kompilator zgłosi błąd.

Zwracany typ funkcji jest określana przez typ ostatniego wyrażenia w funkcji.

Na przykład w poniższym kodzie, typy parametrów `a` i `b` i zwracany typ jest wnioskowany jako `int` ponieważ literału `100` typu `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Może mieć wpływ na wnioskowanie o typie, zmieniając literały. Jeśli wprowadzisz `100` `uint32` , dodając sufiks `u`, typy `a`, `b`, i wartość zwracana jest wywnioskowana `uint32`.

Możesz również zmieniać wnioskowanie o typie przy użyciu innych konstrukcji, sugerujących ograniczenia dotyczące typu, na przykład funkcji i metod, które działają z określonego typu.

Ponadto można zastosować jawnego typu adnotacji do parametrów funkcji lub metody lub zmiennych w wyrażeniach, jak pokazano w poniższych przykładach. Błędy wyniku, jeśli występują konflikty między różnych ograniczeń.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Można również jawnie określić wartość zwracaną przez funkcję, udostępniając adnotacji typu po wszystkich parametrów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Często zdarza, gdzie adnotacji typu przydaje się w parametrze jest, gdy parametr jest typu obiektu, a użytkownik chce, należy użyć członka.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Automatyczna generalizacja

Jeśli kod funkcji nie jest zależny od typu parametru, kompilator traktuje parametr ogólny. Jest to nazywane *automatyczna Generalizacja*, i może być zaawansowanym pomocy do pisania kodu ogólny bez zwiększania stopnia złożoności.

Na przykład następująca funkcja łączy dwa parametry dowolnego typu w spójnej kolekcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Typ jest wnioskowany jako

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Dodatkowe informacje

Wnioskowanie o typie jest opisany bardziej szczegółowo w F# specyfikacji języka.

## <a name="see-also"></a>Zobacz także

- [Automatyczna generalizacja](generics/automatic-generalization.md)
