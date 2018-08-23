---
title: override (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: c0fdb777c4f5a64dbc92f6afe78cdb714585efe0
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753959"
---
# <a name="override-c-reference"></a>override (odwołanie w C#)
`override` Modyfikator jest wymagane, aby rozszerzyć lub zmodyfikować implementacji abstrakcyjne lub wirtualne dziedziczonej metody, właściwości, indeksatora lub zdarzenia.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Square` klasa musi dostarczać implementację zgodnym z przesłoniętą `Area` ponieważ `Area` jest dziedziczony z abstrakcyjnej `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 `override` Metoda dostarcza nową implementację elementu członkowskiego, który jest dziedziczony z klasy bazowej. Metoda, która została zastąpiona przez `override` deklaracji jest znany jako przesłonięte metody podstawowej. Zastąpione metody podstawowej musi mieć taką samą sygnaturę jak `override` metody. Aby uzyskać informacji na temat dziedziczenia, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Nie można zastąpić niewirtualną lub statycznej metody. Zastąpione metody podstawowej musi być `virtual`, `abstract`, lub `override`.  
  
 `override` Deklaracji nie można zmienić dostępności `virtual` metody. Zarówno `override` metody i `virtual` metoda musi mieć takie same [modyfikator dostępu dla poziomu](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Nie można użyć `new`, `static`, lub `virtual` Modyfikatory do modyfikowania `override` metody.  
  
 Przesłanianie deklaracja właściwości należy określić jako właściwość dziedziczona dokładnie tych samych modyfikator dostępu, typ i nazwa i właściwości musi być `virtual`, `abstract`, lub `override`.  
  
 Aby uzyskać więcej informacji o sposobie używania `override` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [użycie przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład definiuje klasę bazową, o nazwie `Employee`, a klasa pochodna o nazwie `SalesEmployee`. `SalesEmployee` Klasa zawiera dodatkowe pola, `salesbonus`i zastępuje metodę `CalculatePay` niezbędny do konta.  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
