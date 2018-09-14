---
title: New — modyfikator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 496339a7c3b95f16fd13479b096d90058b0799d4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591376"
---
# <a name="new-modifier-c-reference"></a>New — modyfikator (odwołanie w C#)

Stosowania jako modyfikator deklaracji, `new` — słowo kluczowe jawnie ukrywa składową, która jest dziedziczona z klasy bazowej. Po ukryciu dziedziczonego członka, pochodna wersja członka zastępuje wersję klasy podstawowej. Chociaż można ukryć elementy członkowskie bez korzystania z `new` modyfikator, zostanie wyświetlone ostrzeżenie kompilatora. Jeśli używasz `new` Aby jawnie ukryć członka, powoduje to pominięcie ostrzeżenia.

Do ukrywania odziedziczonej składowej, Zadeklaruj go w klasie pochodnej przy użyciu tej samej nazwy elementu członkowskiego i zmodyfikuj go za pomocą `new` — słowo kluczowe. Na przykład:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

W tym przykładzie `BaseC.Invoke` jest ukryta przez `DerivedC.Invoke`. Pole `x` pozostanie niezmienione, ponieważ nie jest ukryty przez podobną nazwę.

Ukrywanie nazw poprzez dziedziczenie ma jedną z następujących form:

Ogólnie rzecz biorąc stała, pole, właściwość lub typ, który został wprowadzony w klasie lub strukturze ukrywa wszystkie składowe klasy podstawowej, które współdzielą jego nazwę.  Istnieją przypadki specjalne.  Na przykład, jeśli zadeklarujesz nowe pole o nazwie `N` typu, którego nie można wywołać i typ podstawowy deklaruje `N` jako metodę, nowe pole nie powoduje ukrycia podstawowej deklaracji w składni wywołania.  Zobacz [specyfikacji języka C# w wersji 5.0](https://www.microsoft.com/download/details.aspx?id=7029) Aby uzyskać szczegółowe informacje (zobacz sekcję "Wyszukanie członka" w sekcji "Wyrażenia").

Metoda wprowadzona w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie bazowej. Ukrywa wszystkie metody klasy podstawowej, które mają taki sam podpis.

Indeksator wprowadzony w klasie lub strukturze ukrywa wszystkie indeksatory klas podstawowych, które mają taki sam podpis.

Jest to błąd, można użyć zarówno `new` i [zastąpienia](override.md) na tym samym użytkownikiem, ponieważ modyfikatorów mają znaczenie wzajemnie się wykluczają. `new` Modyfikator tworzy nowy element członkowski o takiej samej nazwie i powoduje, że oryginalny element członkowski będzie ukryty. `override` Modyfikator rozszerza implementację dla odziedziczonego członka.

Za pomocą `new` modyfikatora w deklaracji, która nie ukrywa dziedziczonej składowej generuje ostrzeżenie.

## <a name="example"></a>Przykład

W tym przykładzie klasę bazową `BaseC`i klasę pochodną `DerivedC`, użyj tej samej nazwy pola `x`, która ukrywa wartość odziedziczonego pola. W przykładzie pokazano użycie `new` modyfikator. Ilustruje też sposób dostępu do ukrytych członków klasy podstawowej za pomocą ich w pełni kwalifikowanych nazw.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Przykład

W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie bazowej. W przykładzie pokazano sposób użycia `new` modyfikator, aby wyeliminować komunikat ostrzegawczy i instrukcje dostęp do członków ukrytej klasy za pomocą ich w pełni kwalifikowanych nazw.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Jeśli usuniesz `new` modyfikator, program się skompiluje i uruchamiania, ale otrzymasz następujące ostrzeżenie:

```
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe operatora](operator-keywords.md)
- [Modyfikatory](modifiers.md)
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Użycie przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
