---
title: nowy modyfikator- C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: f62255be9c74a221836b23058bd48a835f38f629
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608630"
---
# <a name="new-modifier-c-reference"></a>New — modyfikatorC# (odwołanie)

Gdy jest używany jako modyfikator deklaracji, `new` słowo kluczowe jawnie ukrywa element członkowski, który jest Dziedziczony z klasy bazowej. W przypadku ukrycia dziedziczonego elementu członkowskiego wersja pochodna elementu członkowskiego zastępuje wersję klasy bazowej. Chociaż można ukryć składowe bez użycia `new` modyfikatora, zostanie wyświetlone ostrzeżenie kompilatora. Jeśli używasz `new` , aby jawnie ukryć element członkowski, pomija to ostrzeżenie.

Możesz również użyć słowa kluczowego, `new` aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [ograniczenie typu ogólnego](./new-constraint.md).

Aby ukryć dziedziczonego elementu członkowskiego, zadeklaruj go w klasie pochodnej przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikuj `new` go za pomocą słowa kluczowego. Na przykład:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

W tym przykładzie `BaseC.Invoke` jest ukryta przez `DerivedC.Invoke`. Nie ma `x` to wpływ na pole, ponieważ nie jest ono ukryte przez podobną nazwę.

Nazwa ukrywając przy użyciu dziedziczenia ma jedną z następujących form:

- Ogólnie rzecz biorąc, stała, pole, właściwość lub typ, który jest wprowadzany w klasie lub strukturze ukrywa wszystkie elementy członkowskie klasy bazowej, które współdzielą swoją nazwę. Istnieją specjalne przypadki. Na przykład jeśli zadeklarujesz nowe pole o nazwie `N` , aby miało typ, który nie jest wywoływać, a typ podstawowy deklaruje `N` jako metodę, nowe pole nie ukrywa deklaracji bazowej w składni wywołania. Aby uzyskać więcej informacji, zobacz sekcję [odnośnik elementu](~/_csharplang/spec/expressions.md#member-lookup) Członkowskiego [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

- Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie bazowej. Ukrywa także wszystkie metody klasy bazowej, które mają taki sam podpis.

- Indeksator wprowadzony w klasie lub strukturze ukrywa wszystkie indeksatory klasy bazowej, które mają taki sam podpis.

Jest to błąd do użycia `new` i przesłonięcia dla tego samego elementu członkowskiego, ponieważ dwa Modyfikatory mają wzajemnie wykluczające się znaczenie. [](override.md) `new` Modyfikator tworzy nowy element członkowski o tej samej nazwie i powoduje, że oryginalny element członkowski staje się ukryty. `override` Modyfikator rozszerza implementację dziedziczonego elementu członkowskiego.

`new` Użycie modyfikatora w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego, generuje ostrzeżenie.

## <a name="example"></a>Przykład

W tym przykładzie Klasa bazowa, `BaseC`, i `DerivedC`Klasa pochodna, używają tej samej nazwy `x`pola, która ukrywa wartość dziedziczonego pola. W przykładzie pokazano użycie `new` modyfikatora. Pokazano również, jak uzyskać dostęp do ukrytych elementów członkowskich klasy podstawowej przy użyciu ich w pełni kwalifikowanych nazw.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Przykład

W tym przykładzie Klasa zagnieżdżona ukrywa klasę o tej samej nazwie w klasie bazowej. W przykładzie pokazano, `new` jak za pomocą modyfikatora wyeliminować komunikat ostrzegawczy i jak uzyskać dostęp do ukrytych elementów członkowskich klasy przy użyciu ich w pełni kwalifikowanych nazw.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Jeśli usuniesz `new` modyfikator, program będzie nadal kompilować i uruchamiać, ale otrzymasz następujące ostrzeżenie:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [New modyfikator](~/_csharplang/spec/classes.md#the-new-modifier) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](modifiers.md)
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Użycie przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
