---
title: C# for, instrukcja
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: ba156eed25f28a0568e11c986de1e84db3cd9cf0
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504486"
---
# <a name="for-c-reference"></a>Aby uzyskać (odwołanie w C#)

`for` Instrukcji wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne, które daje w wyniku `true`.

W dowolnym punkcie w `for` blok instrukcji, można zerwać pętlę za pomocą [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli za pomocą [nadal](continue.md) instrukcji. Możesz również wyjść `for` pętli przez [przejdź do](goto.md), [zwracają](return.md), lub [throw](throw.md) instrukcji.

## <a name="structure-of-the-for-statement"></a>Struktura `for` — instrukcja

`for` Instrukcja definiuje *inicjatora*, *warunek*, i *iteratora* sekcje:

```csharp
for (initializer; condition; iterator)
    body
```

Wszystkie trzy sekcje są opcjonalne. Treść pętli jest instrukcję lub blok instrukcji.

W poniższym przykładzie przedstawiono `for` instrukcję, określając wszystkie sekcje zdefiniowane:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Inicjatora* sekcji

Instrukcje w *inicjatora* sekcji są wykonywane tylko raz, przed wprowadzeniem pętli. *Inicjatora* sekcja jest jedną z następujących czynności:

- Deklaracji i inicjowania zmiennej lokalnej, co nie jest dostępny z zewnątrz pętli.

- Zero lub więcej wyrażenia instrukcji z następującej listy, rozdzielonych przecinkami:

  - [Przypisanie](../operators/assignment-operator.md) — instrukcja

  - Wywołanie metody

  - Wstawianie prefiksu lub przyrostkowe [przyrostu](../operators/arithmetic-operators.md#increment-operator-) wyrażenie, takie jak `++i` lub `i++`

  - Wstawianie prefiksu lub przyrostkowe [dekrementacji](../operators/arithmetic-operators.md#decrement-operator---) wyrażenie, takie jak `--i` lub `i--`

  - Tworzenie obiektu za pomocą [nowe](new-operator.md) — słowo kluczowe

  - [await](await.md) wyrażenia

*Inicjatora* sekcji w powyższym przykładzie deklaruje i inicjuje zmienną lokalnej `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Warunek* sekcji

*Warunek* sekcji, jeśli jest obecna, musi być wyrażenie logiczne. To wyrażenie jest oceniane przed każdą iteracją pętli. Jeśli *warunek* sekcja nie istnieje lub wyrażenie logiczne, które daje w wyniku `true`, następnej iteracji pętli wykonane; w przeciwnym razie, pętla zostanie zakończone.

*Warunek* określa sekcji w powyższym przykładzie, jeśli pętla kończy się na podstawie wartości zmiennej lokalnej:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Iteratora* sekcji

*Iteratora* sekcja definiuje, co się dzieje po każdej iteracji w treści pętli. *Iteratora* sekcja zawiera zero lub więcej z następujących wyrażeń instrukcji, oddzielonych przecinkami:

- [Przypisanie](../operators/assignment-operator.md) — instrukcja

- Wywołanie metody

- Wstawianie prefiksu lub przyrostkowe [przyrostu](../operators/arithmetic-operators.md#increment-operator-) wyrażenie, takie jak `++i` lub `i++`

- Wstawianie prefiksu lub przyrostkowe [dekrementacji](../operators/arithmetic-operators.md#decrement-operator---) wyrażenie, takie jak `--i` lub `i--`

- Tworzenie obiektu za pomocą [nowe](new-operator.md) — słowo kluczowe

- [await](await.md) wyrażenia

*Iteratora* sekcji w powyższym przykładzie zwiększa zmiennej lokalnej:

```csharp
i++
```

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano kilka mniej typowe sposoby użycia `for` sekcje instrukcji: przypisywanie wartości do zmiennej w zewnętrznej pętli *inicjatora* sekcji wywołania metody w obu  *Inicjator* i *iteratora* sekcje i zmianę wartości dwóch zmiennych w *iteratora* sekcji. Wybierz **Uruchom** do uruchamiania kodu przykładu. Po tym można zmodyfikować kod i uruchom go ponownie.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

W poniższym przykładzie zdefiniowano nieskończone `for` Pętla:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [dla instrukcji](~/_csharplang/spec/statements.md#the-for-statement) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje iteracji](iteration-statements.md)
- [foreach, in](foreach-in.md)
