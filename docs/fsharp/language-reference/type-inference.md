---
title: Wnioskowanie o typie
description: Dowiedz się F# , w jaki sposób kompilator wnioskuje typy wartości, zmienne, parametry i wartości zwracane.
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630184"
---
# <a name="type-inference"></a>Wnioskowanie o typie

W tym temacie opisano sposób F# , w jaki kompilator wnioskuje typy wartości, zmiennych, parametrów i zwracanych wartości.

## <a name="type-inference-in-general"></a>Ogólne wnioskowanie o typie

Pomysłem na wnioskowanie o typie jest to, że nie trzeba określać typów F# konstrukcji, z wyjątkiem sytuacji, w których kompilator nie może jednoznacznie wywnioskować typu. Pomijanie jawnych informacji o typie nie oznacza F# , że jest to język wpisany dynamicznie lub że F# wartości w są słabo wpisane. F#jest statycznie wpisanym językiem, co oznacza, że kompilator określa dokładny typ dla każdej konstrukcji podczas kompilacji. Jeśli nie ma wystarczającej ilości informacji dla kompilatora do ustalenia typów każdej konstrukcji, należy podać dodatkowe informacje o typie, zazwyczaj poprzez dodanie jawnych adnotacji typu w kodzie.

## <a name="inference-of-parameter-and-return-types"></a>Wnioskowanie dotyczące parametrów i zwracanych typów

Na liście parametrów nie trzeba określać typu każdego parametru. A jeszcze, F# to statycznie wpisany język, w związku z czym każda wartość i wyrażenie ma określony typ w czasie kompilacji. Dla tych typów, które nie są jawnie określone, kompilator wnioskuje typ na podstawie kontekstu. Jeśli typ nie jest określony w inny sposób, jest wywnioskowany jako ogólny. Jeśli kod używa wartości niespójnie, w taki sposób, że nie istnieje pojedynczy typ, który spełnia wszystkie zastosowania wartości, kompilator zgłosi błąd.

Zwracany typ funkcji jest określany na podstawie typu ostatniego wyrażenia w funkcji.

Na przykład, w `a` poniższym kodzie, typy parametrów i `b` i typ zwracany są wywnioskowane jako `int` , ponieważ literał `100` jest typu `int`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

Można mieć wpływ na wnioskowanie o typie, zmieniając literały. W przypadku wybrania `100` a `uint32` przez dołączenie `a`sufiksu `u`, typy, `b`i wartość zwracana są wywnioskowane `uint32`.

Można również wpływać na wnioskowanie o typie przy użyciu innych konstrukcji, które oznaczają ograniczenia dotyczące typu, takie jak funkcje i metody, które współpracują z określonym typem.

Ponadto można zastosować jawne adnotacje typu do parametrów funkcji lub metod lub do zmiennych w wyrażeniach, jak pokazano w poniższych przykładach. Wynik błędów w przypadku konfliktów między różnymi ograniczeniami.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

Można również jawnie określić wartość zwracaną funkcji, dostarczając adnotację typu po wszystkich parametrach.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

Typowy przypadek, w którym adnotacja typu jest przydatna na parametrze, gdy parametr jest typem obiektu i chcesz użyć elementu członkowskiego.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>Automatyczna generalizacja

Jeśli kod funkcji nie zależy od typu parametru, kompilator traktuje parametr jako generyczny. Jest to nazywane *automatycznym uogólnieniem*i może być zaawansowaną pomocą do pisania kodu generycznego bez zwiększania złożoności.

Na przykład następująca funkcja łączy dwa parametry dowolnego typu do krotki.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

Typ jest wywnioskowany jako

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>Dodatkowe informacje

Wnioskowanie o typie zostało opisane bardziej szczegółowo w F# specyfikacji języka.

## <a name="see-also"></a>Zobacz także

- [Automatyczna generalizacja](./generics/automatic-generalization.md)
