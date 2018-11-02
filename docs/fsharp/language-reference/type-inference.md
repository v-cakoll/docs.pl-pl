---
title: Wnioskowanie o typie (F#)
description: 'Dowiedz się, jak kompilator F # wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.'
ms.date: 05/16/2016
ms.openlocfilehash: fd826ac48fb9a70aa6f4ff746599c11b7e21a02e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865699"
---
# <a name="type-inference"></a>Wnioskowanie o typie

W tym temacie opisano, jak kompilator F # wnioskuje typów wartości, zmiennych, parametrów i zwracanych wartości.

## <a name="type-inference-in-general"></a>Wnioskowanie o typie ogólnie rzecz biorąc

Koncepcja wnioskowanie o typie jest, czy jest konieczne określanie typów konstrukcje F #, z wyjątkiem sytuacji, gdy kompilator ostatecznie nie można wywnioskować typu. Pomijanie informacji o typie jawne nie oznacza, że F # to język o typach określanych dynamicznie lub że wartości w F # jest słabo z kontrolą typów. Język F # jest statycznie typizowanym językiem, co oznacza, że kompilator wywnioskowuje, że typem dokładne dla każdego konstrukcji podczas kompilacji. Jeśli nie jest wystarczająco dużo informacji dla kompilatora wywnioskowanie typów każdego konstrukcji, dodatkowy typ informacji, musisz podać zwykle przez dodawanie adnotacji typu jawnego gdzieś w kodzie.

## <a name="inference-of-parameter-and-return-types"></a>Wnioskowanie parametrów i zwracanych typów

Na liście parametrów nie należy określić typ każdego parametru. I jeszcze, F # to język statycznie wpisane, a w związku z tym każdy wartość i wyrażenie ma określony typ w czasie kompilacji. Dla tych typów, które nie są jawnie określone kompilator wnioskuje typ na podstawie kontekstu. Jeśli typ nie jest w przeciwnym razie określone, wynika to ogólny. Jeśli kod używa wartości niespójnie, w taki sposób, to nie pojedynczy wywnioskować typ, który spełnia wszystkie przypadki użycia wartości, kompilator zgłosi błąd.

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

Wnioskowanie o typie jest opisany bardziej szczegółowo w specyfikacji języka F #.

## <a name="see-also"></a>Zobacz także

- [Automatyczna generalizacja](generics/automatic-generalization.md)
