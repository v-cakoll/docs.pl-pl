---
title: override (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="override-c-reference"></a>override (odwołanie w C#)
`override` Modyfikator jest wymagana, aby rozszerzyć lub zmodyfikować abstrakcyjna lub wirtualna wykonania dziedziczonej metody, właściwość, indeksator lub zdarzenie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Square` klasy musi zapewniać implementację przesłoniętych z `Area` ponieważ `Area` jest dziedziczona z klasy abstrakcyjnej `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 `override` Metoda zawiera nową implementacją elementu członkowskiego, który jest dziedziczona z klasy podstawowej. Metoda, która zostanie zastąpiona przez `override` deklaracji nosi nazwę przesłoniętej metody podstawowej. Przesłoniętej metody podstawowej musi mieć taką samą sygnaturę jak `override` metody. Informacje o dziedziczeniu znajdują się w temacie [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Nie można zastąpić metodę niewirtualną lub statycznej. Musi być przesłoniętej metody podstawowej `virtual`, `abstract`, lub `override`.  
  
 `override` Deklaracji nie można zmienić dostępności `virtual` metody. Zarówno `override` — metoda i `virtual` metody muszą mieć ten sam [poziomu modyfikator dostępu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Nie można użyć `new`, `static`, lub `virtual` Modyfikatory do modyfikowania `override` metody.  
  
 Zastępowanie deklaracja właściwości należy określić dokładnie tego samego modyfikator dostępu, typ i nazwa jako właściwość dziedziczona i przesłanianej właściwości musi być `virtual`, `abstract`, lub `override`.  
  
 Aby uzyskać więcej informacji o sposobie używania `override` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [użycie zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie definiuje klasę podstawową o nazwie `Employee`, a klasa pochodna o nazwie `SalesEmployee`. `SalesEmployee` Klasa zawiera dodatkowe właściwości `salesbonus`i zastępuje metodę `CalculatePay` w celu uwzględnienia konta.  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
