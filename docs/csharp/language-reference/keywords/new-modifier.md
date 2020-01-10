---
title: nowy modyfikator- C# odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713343"
---
# <a name="new-modifier-c-reference"></a>New — modyfikatorC# (odwołanie)

Gdy jest używany jako modyfikator deklaracji, słowo kluczowe `new` jawnie ukrywa element członkowski, który jest Dziedziczony z klasy bazowej. W przypadku ukrycia dziedziczonego elementu członkowskiego wersja pochodna elementu członkowskiego zastępuje wersję klasy bazowej. Chociaż można ukryć składowe bez używania modyfikatora `new`, zostanie wyświetlone ostrzeżenie kompilatora. Jeśli używasz `new` do jawnego ukrywania elementu członkowskiego, pomija to ostrzeżenie.

Można również użyć słowa kluczowego `new`, aby [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako [ograniczenie typu ogólnego](./new-constraint.md).

Aby ukryć dziedziczoną składową, zadeklaruj ją w klasie pochodnej przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikuj ją za pomocą słowa kluczowego `new`. Na przykład:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

W tym przykładzie `BaseC.Invoke` jest ukryta przez `DerivedC.Invoke`. Nie ma to wpływ na `x` pola, ponieważ nie jest on ukryty przez podobną nazwę.

Nazwa ukrywając przy użyciu dziedziczenia ma jedną z następujących form:

- Ogólnie rzecz biorąc, stała, pole, właściwość lub typ, który jest wprowadzany w klasie lub strukturze ukrywa wszystkie elementy członkowskie klasy bazowej, które współdzielą swoją nazwę. Istnieją specjalne przypadki. Na przykład jeśli zadeklarujesz nowe pole o nazwie `N` tak, aby miało typ, który nie jest wywoływać, a typ podstawowy deklaruje `N` jako metodę, nowe pole nie ukrywa podstawowej deklaracji w składni wywołania. Aby uzyskać więcej informacji, zobacz sekcję [odnośnik elementu członkowskiego](~/_csharplang/spec/expressions.md#member-lookup) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

- Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie bazowej. Ukrywa także wszystkie metody klasy bazowej, które mają taki sam podpis.

- Indeksator wprowadzony w klasie lub strukturze ukrywa wszystkie indeksatory klasy bazowej, które mają taki sam podpis.

Wystąpił błąd zarówno `new`, jak i [przesłonięcia](override.md) dla tego samego elementu członkowskiego, ponieważ dwa Modyfikatory mają wzajemnie wykluczające się znaczenie. Modyfikator `new` tworzy nowy element członkowski o tej samej nazwie i powoduje, że oryginalny element członkowski staje się ukryty. Modyfikator `override` rozszerza implementację dziedziczonego elementu członkowskiego.

Użycie modyfikatora `new` w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego, generuje ostrzeżenie.

## <a name="example"></a>Przykład

W tym przykładzie Klasa bazowa, `BaseC`i Klasa pochodna, `DerivedC`, Użyj tej samej nazwy pola `x`, która ukrywa wartość dziedziczonego pola. W przykładzie pokazano użycie modyfikatora `new`. Pokazano również, jak uzyskać dostęp do ukrytych elementów członkowskich klasy podstawowej przy użyciu ich w pełni kwalifikowanych nazw.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Przykład

W tym przykładzie Klasa zagnieżdżona ukrywa klasę o tej samej nazwie w klasie bazowej. W przykładzie pokazano, jak za pomocą modyfikatora `new` wyeliminować komunikat ostrzegawczy i jak uzyskać dostęp do ukrytych elementów członkowskich klasy przy użyciu ich w pełni kwalifikowanych nazw.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

W przypadku usunięcia modyfikatora `new` program nadal kompiluje i uruchamia, ale otrzymasz następujące ostrzeżenie:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [New modyfikator](~/_csharplang/spec/classes.md#the-new-modifier) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Użycie przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
