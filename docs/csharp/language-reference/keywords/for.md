---
title: dla instrukcji — odwołanie do języka C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: cb83fa015eea19b156faebb5bed18cc1f0970cc1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738796"
---
# <a name="for-c-reference"></a>dla (odwołanie C#)

Instrukcja `for` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne ocenia .

W dowolnym momencie w bloku `for` instrukcji można wyrwać z pętli przy użyciu [break](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [continue](continue.md) instrukcji. Można również wyjść `for` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

## <a name="structure-of-the-for-statement"></a>Struktura `for` oświadczenia

Instrukcja `for` definiuje *inicjalizatora*, *warunek*i *iteratora* sekcje:

```csharp
for (initializer; condition; iterator)
    body
```

Wszystkie trzy sekcje są opcjonalne. Treść pętli jest instrukcja lub blok instrukcji.

Poniższy przykład `for` przedstawia instrukcję ze wszystkimi zdefiniowanymi sekcjami:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>Sekcja *inicjatora*

Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wprowadzeniem pętli. Sekcja *inicjatora* jest jedną z następujących czynności:

- Deklaracja i inicjowanie zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.

- Zero lub więcej wyrażeń instrukcji z poniższej listy, oddzielonych przecinkami:

  - [instrukcja przydziału](../operators/assignment-operator.md)

  - powołanie się na metodę

  - prefiks lub wyrażenie [przyrostowe](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`

  - prefiks lub wyrażenie [dekrementacji](../operators/arithmetic-operators.md#decrement-operator---) postfix, takie jak `--i` lub`i--`

  - tworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora

  - [await](../operators/await.md) wyrażenie

Sekcja *inicjatora* w powyższym przykładzie deklaruje i inicjuje zmienną `i`pętli lokalnej:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>Sekcja *warunek*

Sekcja *warunek,* jeśli jest obecny, musi być wyrażeniem logicznym. To wyrażenie jest oceniane przed każdą iteracją pętli. Jeśli sekcja *warunek* nie jest obecny lub wyrażenie `true`logiczne ocenia do , następna iteracja pętli jest wykonywana; w przeciwnym razie pętla zostanie przerwana.

Sekcja *warunek* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>Sekcja *iteratora*

Sekcja *iteratora* definiuje, co się dzieje po każdej iteracji treści pętli. Sekcja *iteratora* zawiera zero lub więcej następujących wyrażeń instrukcji, oddzielonych przecinkami:

- [instrukcja przydziału](../operators/assignment-operator.md)

- powołanie się na metodę

- prefiks lub wyrażenie [przyrostowe](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`

- prefiks lub wyrażenie [dekrementacji](../operators/arithmetic-operators.md#decrement-operator---) postfix, takie jak `--i` lub`i--`

- tworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora

- [await](../operators/await.md) wyrażenie

Sekcja *iteratora* w powyższym przykładzie zwiększa zmienną pętli lokalnej:

```csharp
i++
```

## <a name="examples"></a>Przykłady

Poniższy przykład ilustruje kilka mniej `for` typowych zastosowań sekcji instrukcji: przypisywanie wartości do zmiennej pętli zewnętrznej w sekcji *inicjatora,* wywoływanie metody zarówno w sekcjach *inicjatora,* jak i *iteratora* oraz zmiana wartości dwóch zmiennych w sekcji *iteratora.* Wybierz **uruchom,** aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Poniższy przykład definiuje `for` nieskończoną pętlę:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcja [instrukcji](~/_csharplang/spec/statements.md#the-for-statement) [specyfikacji języka języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [foreach, in](foreach-in.md)
