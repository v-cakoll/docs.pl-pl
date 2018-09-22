---
title: 'Pętle: for...in — Wyrażenie (F#)'
description: 'Zobacz jak F # for... w wyrażeniu konstrukcji pętli jest używany do wykonywania iteracji dopasowania wzorca w kolekcji wyliczenia.'
ms.date: 05/16/2016
ms.openlocfilehash: c4fba1f1dea3993cafa2e37ad0f32d9fb2eed85a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46576814"
---
# <a name="loops-forin-expression"></a>Pętle: for...in — Wyrażenie

Tej konstrukcji pętli jest używany do wykonywania iteracji dopasowania wzorca w wyliczalny kolekcji, takie jak wyrażenie zakresu, sekwencji, listy, tablicy lub innej konstrukcji, który obsługuje wyliczenia.

## <a name="syntax"></a>Składnia

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>Uwagi

`for...in` Wyrażenia można porównać do wyrażenia `for each` instrukcji w innych językach .NET, ponieważ służy on do pętli wartości w kolekcji wyliczenia. Jednak `for...in` obsługuje również dopasowywanie wzorców względem kolekcji, a nie po prostu iteracji przez całą kolekcję.

Wyliczalne wyrażenia można określić jako wyliczalny kolekcji, lub za pomocą `..` operatora, jako zakres na typ całkowitoliczbowy. Przeliczalne kolekcje zawierają listy, sekwencji, tablice, zestawy, mapy i tak dalej. Dowolny typ, który implementuje `System.Collections.IEnumerable` mogą być używane.

Gdy zakres jest wyrazić za pomocą `..` operatora, należy użyć następującej składni.

*Rozpocznij* ... *Zakończ*

Można również użyć wersji, który zawiera przyrostu o nazwie *pominąć*, jak w poniższym kodzie.

*Rozpocznij* ... *Pomiń* ... *Zakończ*

Korzystając z typu całkowitego zakresów i zmienną licznika prostego jako wzorzec, typowe zachowanie to zwiększyć wartości zmiennej licznika o 1 w każdej iteracji, ale jeśli ten zakres obejmuje wartości skip, licznik jest zwiększany przez wartość Pomiń zamiast tego.

Można także dopasować we wzorcu wartości w wyrażeniu treści.

Poniższe przykłady kodu ilustrują używanie `for...in` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

Dane wyjściowe są następujące:

```
1
5
100
450
788
```

Poniższy przykład pokazuje sposób pętli sekwencji oraz korzystania z wzorca krotki zamiast prostej zmiennej.

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

Poniższy przykład pokazuje, jak w pętli za pośrednictwem prostego liczbą całkowitą.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Dane wyjściowe function1 wyglądają następująco.

```
1 2 3 4 5 6 7 8 9 10
```

Poniższy przykład pokazuje, jak w pętli w zakresie z pominięciem 2, która zawiera każdy inny element zakresu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

Dane wyjściowe `function2` jest następujący.

```
1 3 5 7 9
```

Poniższy przykład pokazuje, jak używać zakresu znaków.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

Dane wyjściowe `function3` jest następujący.

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

Poniższy przykład pokazuje, jak używać wartości ujemne Pomiń dla iteracji odwrotnej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

Dane wyjściowe `function4` jest następujący.

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

Początek i koniec zakresu, może być również wyrażeń, takie jak functions, tak jak w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

Dane wyjściowe `function5` z tych danych wejściowych jest w następujący sposób.

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

W kolejnym przykładzie pokazano użycie symbolu wieloznacznego (\_) Jeśli element nie jest potrzebna w pętli.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

Dane wyjściowe są następujące:

```
Number of elements in list1: 5
```

`Note` Możesz użyć `for...in` w sekwencji, wyrażenia i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `for...in` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Pętle: `for...to` wyrażenia](loops-for-to-expression.md)
- [Pętle: `while...do` wyrażenia](loops-while-do-expression.md)
