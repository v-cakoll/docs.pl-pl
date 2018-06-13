---
title: Wnioskowanie o typie (F#)
description: 'Dowiedz się, jak kompilator języka F # wnioskuje typy wartości, zmienne, parametrów i zwracanych wartości.'
ms.date: 05/16/2016
ms.openlocfilehash: 93e1568ebe71436ad8f7119ac9d9628cdf58012a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563709"
---
# <a name="type-inference"></a>Wnioskowanie o typie

W tym temacie opisano, jak kompilator języka F # wnioskuje typy wartości, zmienne, parametrów i zwracanych wartości.

## <a name="type-inference-in-general"></a>Wnioskowanie o typie ogólnie
Pomysł wnioskowanie o typie jest, że nie trzeba określić typy F # konstrukcje, z wyjątkiem przypadków, gdy kompilator ostatecznie nie można wywnioskować typu. Pominięcie jawnego typu informacji nie oznacza, że F # jest typach określanych dynamicznie języka lub czy wartości w języku F # słabo wpisywania. F # to język typami statycznymi, co oznacza, że kompilator deduces dokładnego typu dla każdego konstrukcji podczas kompilacji. Jeśli nie ma wystarczającej ilości informacji dla kompilatora, aby ustalić typy każdego konstrukcji, musisz podać dodatkowe informacje, zazwyczaj przez dodanie adnotacji typu jawnego gdzieś w kodzie.


## <a name="inference-of-parameter-and-return-types"></a>Wnioskowanie parametrów i zwracanych typów
Na liście parametrów nie trzeba określić typ każdego parametru. Jeszcze, F # jest językiem typami statycznymi i w związku z tym każda wartość i wyrażenie ma typ określoną w czasie kompilacji. Dla typów, które nie określają jawnie kompilator wnioskuje typ na podstawie kontekstu. Jeśli typ nie jest w inny sposób określona, jest wywnioskowany aby wartość była ogólna. Jeśli kod używa wartości niespójnie, w taki sposób, że istnieje jeden nie wywnioskować typu, który spełnia wszystkie używa wartości, kompilator zgłasza błąd.

Zwracany typ funkcji jest określana przez typ ostatniego wyrażenia w funkcji.

Na przykład w poniższym kodzie, typy parametrów `a` i `b` i typ zwracany są wywnioskować jako `int` ponieważ literał `100` jest typu `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Wnioskowanie o typie może mieć wpływ, zmieniając literały. Jeśli wprowadzisz `100` `uint32` przez dodanie sufiksu `u`, typy `a`, `b`, i wartości zwracanej są wywnioskować jako `uint32`.

Można również określić wnioskowanie typu przy użyciu innych konstrukcji sugerujących ograniczenia dotyczące typu, na przykład funkcje i metody, które współpracują z określonego typu.

Ponadto można zastosować jawnego typu adnotacji do parametrów funkcji lub metody lub do zmiennych w wyrażeniach, jak pokazano w poniższych przykładach. Powoduje błędy, jeśli występują konflikty między różne ograniczenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Można również jawnie określić wartość zwracaną przez funkcję, zapewniając adnotację typu, po wszystkich parametrach.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Typowych przypadkach, gdy adnotację typu jest przydatne w parametrze jest, gdy parametr jest typu obiektu i chcesz użyć członka.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a>Automatyczna generalizacja
Jeśli kod funkcji nie jest zależny od typu parametru, kompilator uwzględnia parametr, aby wartość była ogólna. Ta metoda jest wywoływana *automatyczna Generalizacja*, i może być zaawansowaną pomoc do pisania kodu ogólnego bez zwiększania złożoności.

Na przykład następująca funkcja łączy dwa parametry dowolnego typu w spójnej kolekcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Typ jest wywnioskowany się

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Dodatkowe informacje
Wnioskowanie o typie jest opisany bardziej szczegółowo w specyfikacji języka F #.


## <a name="see-also"></a>Zobacz też
[Automatyczna generalizacja](generics/automatic-generalization.md)
