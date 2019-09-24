---
title: 'Pętle: for...in — Wyrażenie'
description: Zobacz, F# jak... w konstrukcji zapętlania wyrażeń jest używany do iteracji na dopasowaniach wzorca w wyliczalnej kolekcji.
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216445"
---
# <a name="loops-forin-expression"></a>Pętle: for...in — Wyrażenie

Ta konstrukcja zapętlenia służy do iteracji na dopasowaniach wzorca w wyliczalnej kolekcji, takiej jak wyrażenie zakresu, sekwencja, lista, tablica lub inna konstrukcja, która obsługuje Wyliczenie.

## <a name="syntax"></a>Składnia

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Uwagi

Wyrażenie można porównać `for each` z instrukcją w innych językach .NET, ponieważ jest używana do pętli w przypadku wartości w wyliczalnej kolekcji. `for...in` Program `for...in` obsługuje jednak również dopasowanie wzorców do kolekcji, a nie tylko iteracji w całej kolekcji.

Wyliczalne wyrażenie może być określone jako wyliczalna kolekcja lub, za `..` pomocą operatora, jako zakresu w typie całkowitym. Wyliczalne kolekcje obejmują listy, sekwencje, tablice, zestawy, mapy itd. Można użyć dowolnego typu `System.Collections.IEnumerable` , który implementuje.

Gdy wyrażasz zakres przy użyciu `..` operatora, możesz użyć następującej składni.

*Rozpocznij* .. *ukończyć*

Możesz również użyć wersji, która zawiera przyrost o nazwie *Skip*, jak w poniższym kodzie.

*Rozpocznij* .. *Pomiń* .. *ukończyć*

W przypadku korzystania z zakresów całkowitych i prostej zmiennej licznika jako wzorca typowym zachowaniem jest zwiększenie zmiennej licznika o 1 dla każdej iteracji, ale jeśli zakres zawiera wartość pomijania, licznik zostanie zwiększony przez wartość pomijania.

W wyrażeniu treści można także użyć wartości pasujących do wzorca.

Poniższe przykłady kodu ilustrują użycie `for...in` wyrażenia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Dane wyjściowe są następujące:

```console
1
5
100
450
788
```

Poniższy przykład pokazuje, jak wykonać pętlę w sekwencji i jak używać wzorca krotek zamiast prostej zmiennej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

Dane wyjściowe są następujące:

```console
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

Poniższy przykład pokazuje, jak wykonać pętlę dla prostego zakresu liczb całkowitych.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Dane wyjściowe function1 są następujące.

```console
1 2 3 4 5 6 7 8 9 10
```

Poniższy przykład pokazuje, jak pętla w zakresie z pominięciem 2, które obejmuje każdy inny element zakresu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Dane wyjściowe `function2` są w następujący sposób.

```console
1 3 5 7 9
```

Poniższy przykład pokazuje, jak używać zakresu znaków.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Dane wyjściowe `function3` są w następujący sposób.

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Poniższy przykład pokazuje, jak używać ujemnej wartości pomijania dla iteracji odwrotnej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Dane wyjściowe `function4` są w następujący sposób.

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Początek i koniec zakresu mogą również być wyrażeniami, takimi jak funkcje, jak w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Dane wyjściowe `function5` z tymi danymi wejściowymi są następujące.

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

W następnym przykładzie pokazano użycie symbolu wieloznacznego (\_), gdy element nie jest wymagany w pętli.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Dane wyjściowe są następujące:

```console
Number of elements in list1: 5
```

`Note`Można używać `for...in` w wyrażeniach sekwencji i innych wyrażeniach obliczeniowych, w tym przypadku używana jest dostosowana wersja `for...in` wyrażenia. Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md), [asynchroniczne przepływy pracy](asynchronous-workflows.md)i [wyrażenia obliczeń](computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętli `for...to`Wyrażenia](loops-for-to-expression.md)
- [Pętli `while...do`Wyrażenia](loops-while-do-expression.md)
