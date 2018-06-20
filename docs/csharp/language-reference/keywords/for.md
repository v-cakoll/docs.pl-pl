---
title: for (odwołanie w C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208388"
---
# <a name="for-c-reference"></a>Aby uzyskać (odwołanie w C#)

`for` Instrukcji wykonuje instrukcję lub blok instrukcji, podczas określonego wyrażenia logicznego daje w wyniku `true`.

W dowolnym punktu w `for` blok instrukcji, można przerwać poza pętli przy użyciu [podziału](break.md) instrukcji lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) instrukcji. Możesz również zakończyć działanie `for` pętli przez [przejdź do](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.
  
## <a name="structure-of-the-for-statement"></a>Struktura `for` — instrukcja

`for` Definiuje instrukcji *inicjatora*, *warunku*, i *iterator* sekcje:
  
```csharp
for (initializer; condition; iterator)  
    body  
```

Wszystkie trzy sekcje są opcjonalne. Treść pętli jest instrukcji lub bloku instrukcji.

W poniższym przykładzie przedstawiono `for` instrukcji z wszystkich zdefiniowanych sekcji:

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*Inicjatora* sekcji

Instrukcje w *inicjatora* sekcji są wykonywane tylko raz, przed wprowadzeniem pętli. *Inicjatora* sekcja jest jedną z następujących czynności:

- Deklaracji i inicjowania zmiennej lokalnej nie mogą być dostępne spoza pętli.

- Zero lub więcej wyrażenia instrukcji z poniższej listy rozdzielonych przecinkami:

  - [Przypisanie](../operators/assignment-operator.md) — instrukcja

  - Wywołanie metody  

  - Prefiks lub przyrostka [przyrostu](../operators/increment-operator.md) wyrażenia, takich jak `++i` lub `i++`  

  - Prefiks lub przyrostka [dekrementacji](../operators/decrement-operator.md) wyrażenia, takich jak `--i` lub `i--`  

  - Tworzenie obiektu przy użyciu [nowe](new-operator.md) — słowo kluczowe

  - [await](await.md) wyrażenia

*Inicjatora* sekcji w powyższym przykładzie deklaruje i inicjuje zmiennej lokalnej `i`:

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*Warunku* sekcji

*Warunku* sekcji, jeśli jest obecny, musi być wyrażenie logiczne. Czy wyrażenie jest obliczane przed każdym iteracji pętli. Jeśli *warunku* sekcji nie istnieje lub wyrażenie warunkowe daje w wyniku `true`następnej iteracji pętli jest wykonywane; w przeciwnym razie, pętla zostanie zakończone.

*Warunku* sekcja w powyższym przykładzie określa, czy pętli kończy się na podstawie wartości zmiennej lokalnej:

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*Iterator* sekcji

*Iterator* sekcja definiuje co się stanie po każdej iteracji pętli treści. *Iterator* sekcja zawiera zero lub więcej z następujących wyrażenia instrukcji, oddzielonych przecinkami:  

- [Przypisanie](../operators/assignment-operator.md) — instrukcja

- Wywołanie metody  

- Prefiks lub przyrostka [przyrostu](../operators/increment-operator.md) wyrażenia, takich jak `++i` lub `i++`  

- Prefiks lub przyrostka [dekrementacji](../operators/decrement-operator.md) wyrażenia, takich jak `--i` lub `i--`  

- Tworzenie obiektu przy użyciu [nowe](new-operator.md) — słowo kluczowe

- [await](await.md) wyrażenia

*Iterator* sekcji w powyższym przykładzie zwiększa zmiennej lokalnej:

```csharp
i++
```

## <a name="examples"></a>Przykłady

Poniższy przykład przedstawia kilka mniej typowe zastosowania `for` sekcje instrukcji: przypisywanie wartości do zmiennej pętli zewnętrznych w *inicjatora* sekcji wywołania metody w obu  *Inicjator* i *iterator* sekcje i zmianę wartości dwie zmienne *iterator* sekcji. Wybierz **Uruchom** do uruchomienia przykładu kodu. Następnie można zmodyfikować kod i uruchom go ponownie.
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
W poniższym przykładzie zdefiniowano nieskończone `for` Pętla:
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a>specyfikacja języka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>Zobacz także

[For — instrukcja (specyfikacja języka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[Dokumentacja języka C#](../index.md)  
[Przewodnik programowania w języku C#](../../programming-guide/index.md)  
[Słowa kluczowe języka C#](index.md)  
[foreach, in](foreach-in.md)  
[for, instrukcja (C++)](/cpp/cpp/for-statement-cpp)  
[Instrukcje iteracji](iteration-statements.md)
