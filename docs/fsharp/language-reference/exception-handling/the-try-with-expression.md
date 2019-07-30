---
title: 'Wyjątki: Wyrażenie try...with'
description: Dowiedz się, F# jak używać metody "try... z wyrażeniem "Expression for Exception obsługi.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630248"
---
# <a name="exceptions-the-trywith-expression"></a>Wyjątki: Wyrażenie try...with

W tym temacie opisano `try...with` wyrażenie, wyrażenie, które jest używane do obsługi wyjątków w F# języku.

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

Wyrażenie służy do obsługi wyjątków w F# `try...with` Jest podobna do `try...catch` instrukcji w C#temacie. W powyższej składni kod w elemencie *wyrażenie1* może generować wyjątek. `try...with` Wyrażenie zwraca wartość. Jeśli żaden wyjątek nie zostanie zgłoszony, całe wyrażenie zwróci wartość *wyrażenie1*. Jeśli wystąpi wyjątek, każdy *wzorzec* jest porównywany z wyjątkiem, a dla pierwszego pasującego wzorca, odpowiednie *wyrażenie*, znane jako *procedura obsługi wyjątków*, dla tej gałęzi jest wykonywane i wyrażenie ogólne Zwraca wartość wyrażenia w tej procedurze obsługi wyjątków. Jeśli żaden wzorzec nie jest zgodny, wyjątek propaguje stos wywołań do momentu znalezienia zgodnej procedury obsługi. Typy wartości zwracane z każdego wyrażenia w obsłudze wyjątków muszą być zgodne z typem zwracanym z wyrażenia w `try` bloku.

Często fakt, że wystąpił błąd, oznacza również, że nie ma prawidłowej wartości, którą można zwrócić z wyrażeń w ramach każdego programu obsługi wyjątków. Częstym wzorcem jest posiadanie typu wyrażenia jako typu opcji. Poniższy przykład kodu ilustruje ten wzorzec.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

Wyjątki mogą być wyjątkami platformy .NET lub mogą być F# wyjątkami. Wyjątki można definiować F# za pomocą `exception` słowa kluczowego.

Można użyć różnych wzorców do filtrowania według typu wyjątku i innych warunków; opcje są podsumowane w poniższej tabeli.

|Wzorzec|Opis|
|-------|-----------|
|:? *Typ wyjątku*|Dopasowuje określony typ wyjątku platformy .NET.|
|:? *Typ wyjątku* jako *Identyfikator*|Dopasowuje określony typ wyjątku .NET, ale daje wyjątek nazwaną wartość.|
|*Nazwa wyjątku* (*argumenty*)|Dopasowuje F# typ wyjątku i wiąże argumenty.|
|*identyfikatora*|Dopasowuje dowolny wyjątek i wiąże nazwę z obiektem Exception. **Równoważne:? System. Exception jako**_Identyfikator_|
|*Identyfikator* , gdy *warunek*|Dopasowuje dowolny wyjątek, jeśli warunek ma wartość true.|

## <a name="examples"></a>Przykłady

Poniższe przykłady kodu ilustrują użycie różnych wzorców obsługi wyjątków.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> Konstrukcja jest osobnym wyrażeniem `try...finally` z wyrażenia. `try...with` W związku z tym, jeśli kod wymaga `with` zarówno bloku, `finally` jak i bloku, należy zagnieździć te dwa wyrażenia.

> [!NOTE]
> Można używać `try...with` w asynchronicznych przepływach pracy i innych wyrażeniach obliczeniowych, w tym przypadku używana `try...with` jest dostosowana wersja wyrażenia. Aby uzyskać więcej informacji, zobacz [asynchroniczne przepływy pracy](../asynchronous-workflows.md)i [wyrażenia obliczeń](../computation-expressions.md).

## <a name="see-also"></a>Zobacz także

- [Obsługa wyjątków](index.md)
- [Typy wyjątków](exception-types.md)
- [Wyjątki: `try...finally` Wyrażenie](the-try-finally-expression.md)
