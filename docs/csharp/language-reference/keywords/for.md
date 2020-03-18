---
title: dla instrukcji - odwołanie do języka C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74552267"
---
# <a name="for-c-reference"></a>dla (odwołanie do języka C#)

Instrukcja `for` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne oblicza .

W dowolnym momencie `for` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break](break.md) lub przejść do następnej iteracji w pętli przy użyciu [instrukcji continue.](continue.md) Możesz również wyjść `for` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.

## <a name="structure-of-the-for-statement"></a>Struktura oświadczenia `for`

Instrukcja `for` definiuje *sekcje inicjatora*, *warunek*i *iteratora:*

```csharp
for (initializer; condition; iterator)
    body
```

Wszystkie trzy sekcje są opcjonalne. Treść pętli jest instrukcją lub blokiem instrukcji.

W poniższym `for` przykładzie przedstawiono instrukcję ze wszystkimi zdefiniowanymi sekcjami:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>Sekcja *inicjatora*

Instrukcje w sekcji *inicjatora* są wykonywane tylko raz, przed wejściem do pętli. Sekcja *inicjatora* jest jedną z następujących czynności:

- Deklaracja i inicjowanie zmiennej pętli lokalnej, do której nie można uzyskać dostępu spoza pętli.

- Zero lub więcej wyrażeń instrukcji z poniższej listy, oddzielone przecinkami:

  - [instrukcja przypisania](../operators/assignment-operator.md)

  - wywołanie metody

  - prefiks lub wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`

  - prefiks lub wyrażenie [dekrementacji,](../operators/arithmetic-operators.md#decrement-operator---) takie jak `--i` lub`i--`

  - stworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora

  - [oczekiwanie na](../operators/await.md) wyrażenie

Sekcja *inicjatora* w powyższym przykładzie deklaruje i `i`inicjuje zmienną pętli lokalnej:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>Sekcja *warunków*

Sekcja *warunku,* jeśli jest obecna, musi być wyrażeniem wartości ą logiczną. To wyrażenie jest oceniane przed każdą iteracją pętli. Jeśli sekcja *warunku* nie jest obecny lub `true`wyrażenie logiczne oblicza , następna iteracja pętli jest wykonywana; w przeciwnym razie pętla zostanie wycofana.

Sekcja *warunku* w powyższym przykładzie określa, czy pętla kończy się na podstawie wartości zmiennej pętli lokalnej:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>Sekcja *iterator*

Sekcja *iterator* określa, co dzieje się po każdej iteracji treści pętli. Sekcja *iterator* zawiera zero lub więcej z następujących wyrażeń instrukcji, oddzielonych przecinkami:

- [instrukcja przypisania](../operators/assignment-operator.md)

- wywołanie metody

- prefiks lub wyrażenie [przyrostu](../operators/arithmetic-operators.md#increment-operator-) postfix, takie jak `++i` lub`i++`

- prefiks lub wyrażenie [dekrementacji,](../operators/arithmetic-operators.md#decrement-operator---) takie jak `--i` lub`i--`

- stworzenie obiektu przy użyciu [nowego](../operators/new-operator.md) operatora

- [oczekiwanie na](../operators/await.md) wyrażenie

Sekcja *iterator* w powyższym przykładzie zwiększa zmienną pętli lokalnej:

```csharp
i++
```

## <a name="examples"></a>Przykłady

W poniższym przykładzie przedstawiono kilka mniej `for` typowych zastosowań sekcji instrukcji: przypisywanie wartości do zmiennej pętli zewnętrznej w sekcji *inicjatora,* wywoływanie metody w sekcjach *inicjatora* i *iteratorze* oraz zmiana wartości dwóch zmiennych w sekcji *iteratora.* Wybierz **uruchom,** aby uruchomić przykładowy kod. Następnie można zmodyfikować kod i uruchomić go ponownie.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

Poniższy przykład definiuje nieskończoną `for` pętlę:

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Instrukcja dla](~/_csharplang/spec/statements.md#the-for-statement) [specyfikacji języka Języka Języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [foreach, in](foreach-in.md)
