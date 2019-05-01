---
title: 'Wyjątki: Try... with — wyrażenie'
description: Dowiedz się, jak używać F# "try... with —" wyrażenia dla obsługi wyjątków.
ms.date: 05/16/2016
ms.openlocfilehash: 742e0b595525c69b83a55682c3c8b9b650326ac7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945538"
---
# <a name="exceptions-the-trywith-expression"></a>Wyjątki: Try... with — wyrażenie

W tym temacie opisano `try...with` wyrażenia, wyrażenie, które służy do obsługi wyjątków w F# języka.

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

`try...with` Wyrażenie jest używane do obsługi wyjątków w F#. Jest on podobny do `try...catch` instrukcji w języku C#. W poprzedniej składni kodu w *wyrażenie1* może generować wyjątek. `try...with` Wyrażenie zwróci wartość. Jeśli jest zgłaszany żaden wyjątek, całe wyrażenie zwraca wartość *wyrażenie1*. Jeśli wyjątek jest zgłaszany, każdy *wzorzec* jest porównywany z kolei, z wyjątkiem i dopasowywania wzorca pierwszego odpowiedniego *wyrażenie*, znaną jako *obsługi wyjątków*dla tej gałęzi jest wykonywany i ogólną wyrażenie zwraca wartość wyrażenia w tym obsługi wyjątków. Jeśli wzorzec nie jest zgodny, wyjątek propaguje górę stosu wywołań, dopóki nie znaleziono pasującej klauzuli obsługi. Typy wartości zwracanych z każde wyrażenie w obsługi wyjątków musi odpowiadać typ zwracany z wyrażenia w `try` bloku.

Nie ma prawidłowej wartości, które mogą być zwrócone z wyrażeń w każdy program obsługi wyjątków oznacza często fakt również wystąpił błąd. Częsty wzór jest typ wyrażenia jest typem opcji. Poniższy przykład kodu ilustruje ten wzorzec.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Wyjątki mogą być wyjątki platformy .NET lub mogą być F# wyjątków. Można zdefiniować F# wyjątków za pomocą `exception` — słowo kluczowe.

Można użyć różnych wzorców do filtrowania typ wyjątku i innych warunków; opcje są podsumowane w poniższej tabeli.

|Wzorzec|Opis|
|-------|-----------|
|:? *Typ wyjątku*|Jest zgodny z określonym typem wyjątku .NET.|
|:? *Typ wyjątku* jako *identyfikator*|Jest zgodny z określonym typem wyjątku .NET, ale zapewnia wyjątek nazwanej wartości.|
|*nazwa wyjątku*(*argumenty*)|Dopasowuje F# typ wyjątku i powiązań argumenty.|
|*Identyfikator*|Dopasowuje dowolny wyjątek i wiąże nazwę obiektu wyjątku. Odpowiednikiem **:? System.Exception jako**_identyfikator_|
|*Identyfikator* podczas *warunku*|Dopasowuje każdy wyjątek, jeśli warunek jest prawdziwy.|

## <a name="examples"></a>Przykłady

Poniższe przykłady kodu ilustrują używanie różnych wzorców obsługi wyjątków.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> `try...with` Konstrukcja jest wyrażeniem osobnych z `try...finally` wyrażenia. W związku z tym jeśli kod wymaga zarówno `with` bloku i `finally` bloku, należy zagnieździć dwóch wyrażeń.

> [!NOTE]
> Możesz użyć `try...with` w Asynchroniczne przepływy pracy i inne wyrażenia obliczeń, w którym zamierzone, Zapisz dostosowaną wersję `try...with` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [Asynchroniczne przepływy pracy](../asynchronous-workflows.md), i [wyrażenia obliczeń](../computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...finally` Wyrażenia](the-try-finally-expression.md)