---
title: 'Wyjątki: try...with — Wyrażenie (F#)'
description: 'Dowiedz się, jak użyć F # "try... with" wyrażenia dla obsługi wyjątków.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 06e40b79fc1958918dc0615ce9d1004e0a6e74a5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-trywith-expression"></a>Wyjątki: try...with — Wyrażenie

W tym temacie opisano `try...with` wyrażenia, wyrażenie, które służy do obsługi wyjątków w języku F #.


## <a name="syntax"></a>Składnia

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>Uwagi
`try...with` Wyrażenie jest używane do obsługi wyjątków w języku F #. Jest on podobny do `try...catch` instrukcji w języku C#. W powyższej składni kod w *wyrażenie1* może generować wyjątek. `try...with` Wyrażenie zwraca wartość. Jeśli żaden wyjątek jest zgłaszany, całe wyrażenie zwraca wartość *wyrażenie1*. Jeśli jest zgłaszany wyjątek, każdy *wzorzec* jest porównywany z kolei, z wyjątkiem i pierwszy pasujący wzorzec odpowiadającego *wyrażenie*, znaną jako *program obsługi wyjątku*dla tej gałęzi jest wykonywana, a ogólną wyrażenie zwraca wartość wyrażenia w tym obsługi wyjątków. Jeśli wzorzec nie jest zgodny, wyjątek propaguje górę stosu wywołań, aż do znalezienia zgodnego programu obsługi. Typy wartości zwrócone przez każde wyrażenie w programy obsługi wyjątków musi odpowiadać typowi zwrócony z wyrażenia w `try` bloku.

Często fakt również wystąpił błąd oznacza, że nie ma prawidłowej wartości, które mogą być zwrócone z wyrażeń w każdym obsługi wyjątków. Częste wzorzec jest typ wyrażenia jest typ opcji. Poniższy przykład kodu pokazuje tego wzorca.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Wyjątki mogą być wyjątki .NET lub mogą być wyjątki F #. Możesz zdefiniować wyjątki F # za pomocą `exception` — słowo kluczowe.

Można użyć różnych wzorców do filtrowania typ wyjątku i innych warunków; Opcje podsumowano w poniższej tabeli.


|Wzorzec|Opis|
|-------|-----------|
|:? *Typ wyjątku*|Zgodne z określonym typem wyjątku .NET.|
|:? *Typ wyjątku* jako *identyfikator*|Zgodne z określonym typem wyjątku .NET, ale zapewnia wyjątek nazwanych wartości.|
|*nazwa wyjątku*(*argumenty*)|Zgodny z typem wyjątku języka F # i wiąże argumentów.|
|*Identyfikator*|Zgodny z żadnym wyjątku i wiąże nazwę obiekt wyjątku. Odpowiednikiem **:? System.Exception jako *** identyfikator*|
|*Identyfikator* podczas *warunku*|Odpowiada wyjątku, jeśli wynikiem warunku jest PRAWDA.|

## <a name="examples"></a>Przykłady
W poniższych przykładach kodu ilustrują korzystanie z różnych wzorców obsługi wyjątków.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
`try...with` Konstrukcja jest oddzielne wyrażenie z `try...finally` wyrażenia. W związku z tym jeśli kod wymaga obu `with` bloku i `finally` bloku, konieczne będzie zagnieździć dwóch wyrażeń.

>[!NOTE] 
Można użyć `try...with` w Asynchroniczne przepływy pracy i inne wyrażenia obliczeń, w których przypadku dostosowaną wersję `try...with` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [Asynchroniczne przepływy pracy](../asynchronous-workflows.md), i [wyrażenia obliczeń](../computation-expressions.md).


## <a name="see-also"></a>Zobacz też
[Obsługa wyjątków](index.md)

[Typy wyjątków](exception-types.md)

[Wyjątki: `try...finally` wyrażenia](the-try-finally-expression.md)
