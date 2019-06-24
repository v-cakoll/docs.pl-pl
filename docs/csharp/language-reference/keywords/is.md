---
title: jest - C# odwołania
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306591"
---
# <a name="is-c-reference"></a>is (odwołanie w C#)

`is` Operator sprawdza, czy wynikiem wyrażenia jest zgodne z danym typem lub (począwszy od C# 7.0) sprawdza wyrażenie do wzorca. Aby uzyskać informacje na temat typu testowania `is` Zobacz operator [jest operatorem](../operators/type-testing-and-conversion-operators.md#is-operator) części [operatory badania typu i konwersji](../operators/type-testing-and-conversion-operators.md) artykułu.

## <a name="pattern-matching-with-is"></a>Dopasowywanie wzorca z `is`

Począwszy od C# 7.0, `is` i [Przełącz](switch.md) instrukcje obsługują dopasowywania do wzorca. `is` — Słowo kluczowe obsługuje następujące wzorce:

- [Wpisz wzór](#type-pattern), który sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu.

- [Wzór stałej](#constant-pattern), która sprawdza, czy wyrażenie ma określoną wartość stałą.

- [wzorzec var](#var-pattern), dopasowania zawsze zakończy się pomyślnie i Nowa zmienna lokalna jest powiązana wartość wyrażenia.

### <a name="type-pattern"></a>Wpisz wzór

W przypadku używania wzorca typu do realizacji dopasowania do wzorca, `is` sprawdza, czy wyrażenie można przekonwertować na określony typ i, jeśli może zostać rzutuje zmiennej tego typu. To proste rozszerzenie `is` instrukcję, która umożliwia ocenę zwięzły typ i konwersji. Ogólna postać `is` typu wzorzec jest:

```csharp
   expr is type varname
```

gdzie *expr* jest wyrażeniem, które daje w wyniku wystąpienia określonego typu *typu* nazwę typu, do którego jest wynikiem *wyrażenie* ma być przekonwertowany i *nazwa_zmiennej* obiekt, do którego jest wynikiem *expr* jest konwertowany, jeśli `is` test jest `true`. 

`is` Wyrażenie jest `true` Jeśli *expr* nie jest `null`, i jest spełniony jeden z następujących czynności:

- *wyrażenie* to wystąpienie tego samego typu co *typu*.

- *wyrażenie* jest wystąpieniem typu, który pochodzi od klasy *typu*. Innymi słowy, wynikiem *expr* może być rzutowany w górę do wystąpienia *typu*.

- *wyrażenie* ma typ kompilacji, która jest klasą bazową dla *typu*, i *expr* ma typ środowiska uruchomieniowego, który jest *typu* lub typu pochodnego względem *typu*. *Typów w czasie kompilacji* zmiennej jest typem zmiennej, zgodnie z definicją w jego deklaracji. *Typ środowiska uruchomieniowego* zmiennej jest typem wystąpienia, która jest przypisana do zmiennej.

- *wyrażenie* jest wystąpieniem typu, który implementuje *typu* interfejsu.

Począwszy od C# 7.1, *expr* może mieć typ kompilacji, zdefiniowane przez parametr typu ogólnego i ograniczenia.

Jeśli *expr* jest `true` i `is` jest używana z `if` instrukcji *nazwa_zmiennej* jest przypisywane w ramach `if` tylko instrukcji. Zakres *nazwa_zmiennej* pochodzi z `is` wyrażenia na końcu otaczający blok `if` instrukcji. Za pomocą *nazwa_zmiennej* w dowolnej innej lokalizacji generuje błąd w czasie kompilacji do użytku w zmiennej, która nie została przypisana.

W poniższym przykładzie użyto `is` wpisz wzór do implementacji typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez dopasowywania do wzorca, ten kod może być zapisana w następujący sposób. Używanie dopasowania wzorca typu generuje kod bardziej zwarty, czytelny dzięki wyeliminowaniu konieczności, aby sprawdzić, czy wynik konwersji jest `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Wpisz wzór również generuje kod bardziej zwarty podczas określania typu o typie wartości. W poniższym przykładzie użyto `is` wpisz wzór, aby ustalić, czy obiekt jest `Person` lub `Dog` wystąpienia przed wyświetleniem wartości odpowiednich właściwości.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Równoważny kod bez dopasowywania do wzorca wymaga oddzielnych przypisania, które obejmuje jawnego rzutowania.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Wzór stałej

Podczas przeprowadzania dopasowywanie wzorca za wzór stałej `is` sprawdza, czy wyrażenie jest równe określonej stałej. W języku C# 6 i starszych wersji wzór stałej jest obsługiwana przez [Przełącz](switch.md) instrukcji. Począwszy od C# 7.0, nie jest obsługiwany przez `is` także instrukcji. Jego składnia jest następująca:

```csharp
   expr is constant
```

gdzie *expr* jest wyrażenie do oceny, i *stałej* jest wartością do testowania. *Stała* może być dowolną z następujących stałych wyrażeń:

- Wartość literału.

- Nazwa deklarowanej `const` zmiennej.

- Stała wyliczenia.

Stałe wyrażenie jest obliczane w następujący sposób:

- Jeśli *expr* i *stałej* typów całkowitych operatora porównania języka C# Określa, czy wyrażenie zwraca `true` (oznacza to, czy `expr == constant`).

- W przeciwnym razie wartość wyrażenia jest określana przez wywołanie statycznego [metody Object.Equals (wyrażenie stałe)](xref:System.Object.Equals(System.Object,System.Object)) metody.  

Poniższy przykład łączy wzorców typu i stała, aby sprawdzić, czy obiekt jest `Dice` wystąpienia, a jeśli tak jest, aby określić, czy wartość skumulowane dice to 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Sprawdzanie `null` mogą być wykonywane przy użyciu wzorca stałej. `null` — Słowo kluczowe jest obsługiwana przez `is` instrukcji. Jego składnia jest następująca:

```csharp
   expr is null
```

W poniższym przykładzie przedstawiono porównanie `null` sprawdza, czy:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>wzorzec var

`var` Wzorzec jest wychwytywania dla dowolnego typu lub wartości. Wartość *expr* jest zawsze przypisywana do zmiennej lokalnej taki sam typ co typ czasu kompilacji *expr*. Wynik `is` wyrażenie ma zawsze wartość `true`. Jego składnia jest następująca:

```csharp
   expr is var varname
```

W poniższym przykładzie użyto wzorca var można przypisać wyrażenia do zmiennej o nazwie `obj`. Następnie wyświetla wartość i typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>specyfikacja języka C#
  
Aby uzyskać więcej informacji, zobacz [jest operatorem](~/_csharplang/spec/expressions.md#the-is-operator) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md) następujący kod C# propozycji języka:

- [Dopasowanie do wzorca](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Dopasowywanie wzorca do typów ogólnych](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Operatory badania typu i konwersji](../operators/type-testing-and-conversion-operators.md)
