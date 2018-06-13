---
title: new — Modyfikator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: b66cfacc2203e0e529c19b5c566abad6c676f149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273971"
---
# <a name="new-modifier-c-reference"></a>new — Modyfikator (odwołanie w C#)
Gdy jest używany jako modyfikatory deklaracji, `new` — słowo kluczowe jawnie ukrywa element członkowski, który jest dziedziczona z klasy podstawowej. Ukrycie dziedziczonego elementu członkowskiego pochodnymi wersjami element członkowski zastępuje wersji klasy podstawowej. Mimo że można ukryć składniki bez użycia `new` modyfikator, zostanie wyświetlone ostrzeżenie kompilatora. Jeśli używasz `new` Aby jawnie ukrywa element członkowski, powoduje pominięcie to ostrzeżenie.  
  
 Ukrywa dziedziczony element członkowski, Zadeklaruj ją w klasie pochodnej przy użyciu takiej samej nazwie elementu członkowskiego i zmodyfikuj go przy użyciu `new` — słowo kluczowe. Na przykład:  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 W tym przykładzie `BaseC.Invoke` jest ukryty przez `DerivedC.Invoke`. Pole `x` nie ma wpływ, ponieważ nie jest ukryty przez podobną nazwę.  
  
 Ukrywanie poprzez dziedziczenie nazwa przyjmuje jeden z następujących formatów:  
  
-   Ogólnie rzecz biorąc stała, pola, właściwości lub typu, która została wprowadzona w klasie lub strukturze powoduje ukrycie wszystkich elementów członkowskich klasy podstawowej, które mają nazwy.  Brak przypadków specjalnych.  Na przykład, jeśli zadeklarować nowe pole o nazwie `N` typu, który nie jest wywoływać i typem bazowym deklaruje `N` jako metodę nowego pola nie ukrywa deklaracji podstawowej w Składnia wywołania.  Zobacz [specyfikacja języka C# w wersji 5.0](https://www.microsoft.com/download/details.aspx?id=7029) szczegółowe (zobacz sekcję "Wyszukiwanie elementu członkowskiego" w sekcji "Wyrażenia").  
  
-   Metody wprowadzone w klasie lub strukturze ukrywa właściwości, pola i typy, które współużytkują tę nazwę w klasie podstawowej. Ukrywa również wszystkie metody klasy podstawowej, które mają taką samą sygnaturę.  
  
-   Indeksator wprowadzone w klasie lub strukturze ukrywa wszystkie indeksatory klasy podstawowej, które mają taką samą sygnaturę.  
  
 Jest błąd, aby korzystać z obu `new` i [zastąpienia](../../../csharp/language-reference/keywords/override.md) na tym samym użytkownikiem, ponieważ dwie Modyfikatory mają znaczenie wykluczają się wzajemnie. `new` Modyfikator tworzy nowy element członkowski o takiej samej nazwie i powoduje, że oryginalnego elementu na będą ukryte. `override` Modyfikator rozszerza implementację dla dziedziczonego elementu członkowskiego.  
  
 Przy użyciu `new` modyfikatora w deklaracji, która nie ukrywa dziedziczonego elementu członkowskiego generuje ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa podstawowa, `BaseC`i w klasie pochodnej `DerivedC`, użyj takiej samej nazwy pola `x`, która ukrywa wartość pola dziedziczone. W przykładzie pokazano użycie `new` modyfikator. Ilustruje też sposób dostępu do ukrytych elementów członkowskich klasy podstawowej za pomocą ich w pełni kwalifikowane nazwy.  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa zagnieżdżona ukrywa klasę, która ma taką samą nazwę w klasie podstawowej. W przykładzie pokazano sposób użycia `new` modyfikator wyeliminować komunikat ostrzegawczy i jak dostęp do członków klasy ukryte przy użyciu ich w pełni kwalifikowane nazwy.  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Jeśli usuniesz `new` modyfikator, program będzie nadal skompilować i uruchomić, ale spowoduje następujące ostrzeżenie:  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [Użycie przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
