---
title: "Funkcje śródwierszowe (F#)"
description: "Dowiedz się, jak używać F # funkcji śródwierszowych zintegrowanych bezpośrednio z kodu wywołującego."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a>Funkcje śródwierszowe

*Funkcje śródwierszowe* są funkcje, które są zintegrowane bezpośrednio do wywołującego kodu.


## <a name="using-inline-functions"></a>Przy użyciu funkcji śródwierszowych
Gdy używane są parametry typu na statycznych, wszystkie funkcje, które mają zdefiniowane przez parametry typu musi być wbudowany. Gwarantuje to, że kompilator rozpozna tych parametrów typu. Parametry typu ogólnego zwykłej nie ma żadnych tych ograniczeń.

Inne niż umożliwia używanie ograniczenia elementu członkowskiego, wbudowane funkcje mogą być pomocne w Optymalizacja kodu. Zbyt częste używanie funkcji śródwierszowych może jednak spowodować kodu za mniej odporne na zmiany w optymalizacje kompilatora i stosowania funkcji biblioteki. Z tego powodu należy unikać używania wbudowane funkcje optymalizacji, chyba że nastąpiła innych technik optymalizacji. Tworzenie wbudowanej funkcji lub metody czasami może poprawić wydajność, ale które nie zawsze jest wielkość liter. W związku z tym należy też używać wskaźników wydajności, aby sprawdzić, czy wprowadzania żadnych wbudowanego daną funkcję w rzeczywistości mają pozytywny wpływ.

`inline` Modyfikator może odnosić się do funkcji na najwyższym poziomie, na poziomie modułu lub na poziomie metody w klasie.

Poniższy przykładowy kod przedstawia wbudowanej funkcji najwyższego poziomu, metody wystąpienia wbudowanego i statyczne metodą wbudowaną.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>Funkcje śródwierszowe a wnioskowanie o typie
Obecność `inline` wpływa na wnioskowanie o typie. Jest to spowodowane wbudowane funkcje mogą mieć statycznie rozwiązywane parametry typu podczas, gdy nie można z systemem innym niż wbudowane funkcje. Poniższy przykład kodu pokazuje przypadku gdzie `inline` jest przydatne, ponieważ w przypadku korzystania z funkcji, która ma parametr typu statycznie rozwiązywane `float` operatora konwersji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Bez `inline` , modyfikator wnioskowanie o typie wymusza funkcja do wykonania określonego typu, w tym przypadku `int`. Ale `inline` modyfikator, funkcja jest również wartością parametru typu statycznie rozwiązane. Z `inline` modyfikator, typu jest wywnioskowany być następujące:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Oznacza to, że funkcja akceptuje dowolnego typu, który obsługuje konwersji na **float**.


## <a name="see-also"></a>Zobacz też
[Funkcje](index.md)

[Ograniczenia](../generics/constraints.md)

[Statycznie rozwiązywane parametry typu](../generics/statically-resolved-type-parameters.md)
