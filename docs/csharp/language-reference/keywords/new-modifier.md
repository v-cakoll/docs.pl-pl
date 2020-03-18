---
title: nowy modyfikator — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713343"
---
# <a name="new-modifier-c-reference"></a>nowy modyfikator (odwołanie do języka C#)

Gdy jest używany jako modyfikator deklaracji, `new` słowo kluczowe jawnie ukrywa element członkowski, który jest dziedziczony z klasy podstawowej. Po ukryciu dziedziczonego elementu członkowskiego pochodna wersja elementu członkowskiego zastępuje wersję klasy podstawowej. Mimo że można ukryć `new` członków bez użycia modyfikatora, otrzymasz ostrzeżenie kompilatora. Jeśli używasz `new` jawnie ukryć element członkowski, pomija to ostrzeżenie.

Za pomocą słowa `new` kluczowego można również [utworzyć wystąpienie typu](../operators/new-operator.md) lub jako ograniczenie typu [ogólnego](./new-constraint.md).

Aby ukryć dziedziczonego elementu członkowskiego, zadeklarować go w klasie pochodnej `new` przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikować go za pomocą słowa kluczowego. Przykład:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

W tym `BaseC.Invoke` przykładzie jest `DerivedC.Invoke`ukryty przez . Nie `x` ma to wpływu na to pole, ponieważ nie jest ukryte pod podobną nazwą.

Ukrywanie nazw w dziedziczeniu przyjmuje jedną z następujących form:

- Ogólnie rzecz biorąc stała, pole, właściwość lub typ, który jest wprowadzany w klasie lub struktury ukrywa wszystkie elementy członkowskie klasy podstawowej, które współużytkują jego nazwę. Istnieją szczególne przypadki. Na przykład jeśli ogłosisz nowe `N` pole o nazwie, które ma typ, który `N` nie jest inwolny, a typ podstawowy deklaruje się jako metoda, nowe pole nie ukrywa deklaracji podstawowej w składni wywołania. Aby uzyskać więcej informacji, zobacz sekcję [wyszukiwania elementów członkowskich](~/_csharplang/spec/expressions.md#member-lookup) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

- Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie podstawowej. Ukrywa również wszystkie metody klasy podstawowej, które mają ten sam podpis.

- Indeksator wprowadzony w klasie lub struktury ukrywa wszystkie indeksatory klasy podstawowej, które mają ten sam podpis.

Jest to błąd, `new` aby użyć obu i [zastąpić](override.md) na tym samym e-elementczłonko, ponieważ dwa modyfikatory mają wzajemnie wykluczające się znaczenia. Modyfikator `new` tworzy nowy element członkowski o tej samej nazwie i powoduje, że oryginalny element członkowski staje się ukryty. Modyfikator `override` rozszerza implementację dla dziedziczonego elementu członkowskiego.

Za `new` pomocą modyfikatora w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego generuje ostrzeżenie.

## <a name="example"></a>Przykład

W tym przykładzie klasa `BaseC`podstawowa i klasa `DerivedC`pochodna używają tej `x`samej nazwy pola , która ukrywa wartość odziedziczonego pola. W przykładzie przedstawiono użycie `new` modyfikatora. Pokazuje również, jak uzyskać dostęp do ukrytych elementów członkowskich klasy podstawowej przy użyciu ich w pełni kwalifikowane nazwy.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Przykład

W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie podstawowej. W przykładzie pokazano, `new` jak używać modyfikatora, aby wyeliminować komunikat ostrzegawczy i jak uzyskać dostęp do ukrytych elementów członkowskich klasy przy użyciu ich w pełni kwalifikowane nazwy.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Jeśli usuniesz `new` modyfikator, program będzie nadal kompilować i uruchamiać, ale pojawi się następujące ostrzeżenie:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Sekcję modyfikatora](~/_csharplang/spec/classes.md#the-new-modifier) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../../language-reference/index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory](index.md)
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Użycie zastępowania i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
