---
title: "Pętle: for...in — Wyrażenie (F#)"
description: "Zobacz temat jak for. F #.. w wyrażeniu konstrukcji pętli jest używanej do wykonywania iteracji dopasowania wzorca w kolekcji wyliczalny."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a>Pętle: for...in — Wyrażenie

Ta konstrukcja pętli jest używanej do wykonywania iteracji dopasowania wzorca w wyliczalny kolekcji, takie jak wyrażenia zakres, sekwencji, listy, tablicy lub innych konstrukcji obsługującego wyliczenie.


## <a name="syntax"></a>Składnia

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Uwagi
`for...in` Wyrażenie, które można porównać do `for each` instrukcji w innych językach .NET, ponieważ jest używany do pętli wartości wyliczenia kolekcji. Jednak `for...in` obsługuje również wzorzec dopasowany w kolekcji, a nie tylko iteracji w całej kolekcji.

Wyliczalny wyrażenie, które można określić jako wyliczalny kolekcji lub, za pomocą `..` operatora jako zakres na typ całkowity. Wyliczalny kolekcje zawierają list, sekwencji, tablic, zestawy, map i tak dalej. Dowolnego typu, który implementuje `System.Collections.IEnumerable` mogą być używane.

Gdy express zakresu przy użyciu `..` operatora, należy użyć następującej składni.

*Uruchom* ... *Zakończ*

Można również użyć wersji, która obejmuje przyrostu o nazwie *pominąć*, jak w poniższym kodzie.

*Uruchom* ... *Pomiń* ... *Zakończ*

Gdy używasz integralną zakresy i zmienną prostego licznika jako wzorzec typowe zachowanie jest aby zwiększyć wartości zmiennej licznika przez 1 w każdej iteracji, ale jeśli zakres zawiera wartość pomijania, licznik jest zwiększany o wartość Pomiń zamiast tego.

Można także dopasować we wzorcu wartości w wyrażeniu treści.

Następujący przykładowy kod, przedstawiający zastosowanie `for...in` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Dane wyjściowe są następujące:

```
1
5
100
450
788
```

Poniższy przykład przedstawia sposób pętli sekwencji i sposobu użycia wzorca krotki zamiast prostej zmiennej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

Dane wyjściowe są następujące:

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

Poniższy przykład pokazuje, jak pętli w zakresie proste liczby całkowitej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Dane wyjściowe function1 ma następującą składnię.

```
1 2 3 4 5 6 7 8 9 10
```

Poniższy przykład pokazuje, jak pętli w zakresie z pominięciem 2, w tym każdy element zakresu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Dane wyjściowe `function2` ma następującą składnię.

```
1 3 5 7 9
```

Poniższy przykład przedstawia użycie zakresu znaków.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Dane wyjściowe `function3` ma następującą składnię.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Poniższy przykład przedstawia użycie wartości ujemnej Pomiń dla odwrotnej iteracji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Dane wyjściowe `function4` ma następującą składnię.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Początek i koniec zakresu można także wyrażeń, takich jak funkcje, zgodnie z poniższym kodem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Dane wyjściowe `function5` z tych danych wejściowych jest w następujący sposób.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

W kolejnym przykładzie pokazano użycie symbolu wieloznacznego (_), jeśli element nie jest konieczne w pętli.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Dane wyjściowe są następujące:

```
Number of elements in list1: 5
```

`Note`Można użyć `for...in` w wyrażeniach sekwencji i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `for...in` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)

[Pętle: `while...do` wyrażenia](loops-while-do-expression.md)
