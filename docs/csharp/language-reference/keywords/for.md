---
title: instrukcja- C# Reference
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552267"
---
# <a name="for-c-reference"></a>for (C# odwołanie)

Instrukcja `for` wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne daje w wyniku `true`.

W dowolnym momencie w bloku instrukcji `for` można przerwać pętlę przy użyciu instrukcji [Break](break.md) lub przejść do następnej iteracji w pętli przy użyciu instrukcji [Continue](continue.md) . Możesz również wyjść z pętli `for` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .

## <a name="structure-of-the-for-statement"></a>Struktura instrukcji `for`

Instrukcja `for` definiuje *inicjatora*, *warunek*i sekcje *iteratora* :

```csharp
for (initializer; condition; iterator)
    body
```

Wszystkie trzy sekcje są opcjonalne. Treść pętli jest instrukcją lub blokiem instrukcji.

W poniższym przykładzie pokazano instrukcję `for` ze wszystkimi zdefiniowanymi sekcjami:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>Sekcja *inicjatora*

Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wprowadzeniem pętli. Sekcja *inicjatora* jest jedną z następujących czynności:

- Deklaracja i inicjalizacja zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.

- Zero lub więcej wyrażeń instrukcji z następującej listy oddzielonych przecinkami:

  - instrukcja [przypisania](../operators/assignment-operator.md)

  - wywołanie metody

  - wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego, takie jak `++i` lub `i++`

  - [wyrażenie "](../operators/arithmetic-operators.md#decrement-operator---) prefix" lub "przyrostka", takie jak `--i` lub `i--`

  - Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)

  - wyrażenie [await](../operators/await.md)

Sekcja *inicjatora* w powyższym przykładzie deklaruje i inicjuje zmienną pętli lokalnej `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>Sekcja *warunku*

Sekcja *warunku* , jeśli jest obecna, musi być wyrażeniem logicznym. To wyrażenie jest oceniane przed każdą iteracją pętli. Jeśli sekcja *Condition* nie istnieje lub wyrażenie logiczne zwróci wartość `true`, wykonywana jest iteracja następnej pętli. w przeciwnym razie pętla zostanie zakończona.

Sekcja *warunek* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>Sekcja *iteratora*

Sekcja *iterator* definiuje, co się stanie po każdej iteracji treści pętli. Sekcja *iteratora* zawiera zero lub więcej następujących wyrażeń instrukcji, rozdzielonych przecinkami:

- instrukcja [przypisania](../operators/assignment-operator.md)

- wywołanie metody

- wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) prefiksu lub przyrostkowego, takie jak `++i` lub `i++`

- [wyrażenie "](../operators/arithmetic-operators.md#decrement-operator---) prefix" lub "przyrostka", takie jak `--i` lub `i--`

- Tworzenie obiektu za pomocą operatora [New](../operators/new-operator.md)

- wyrażenie [await](../operators/await.md)

Sekcja *iterator* w powyższym przykładzie zwiększa zmienną pętli lokalnej:

```csharp
i++
```

## <a name="examples"></a>Przykłady

Poniższy przykład ilustruje kilka rzadziej używanych części instrukcji `for`: przypisanie wartości do zmiennej pętla zewnętrzna w sekcji *inicjatora* , wywoływanie metody w *inicjatorze* i *iterator* i zmiana wartości dwóch zmiennych w sekcji *iterator* . Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

W poniższym przykładzie zdefiniowano nieskończoną pętlę `for`:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [dotyczącą instrukcji](~/_csharplang/spec/statements.md#the-for-statement) [ C# języka](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [foreach, in](foreach-in.md)
