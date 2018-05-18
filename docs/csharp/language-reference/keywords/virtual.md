---
title: virtual (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 5a188e9a7cbb7a1c497d577039c2b2578eaa7526
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="virtual-c-reference"></a>virtual (odwołanie w C#)
`virtual` — Słowo kluczowe służy do modyfikowania deklaracji — metoda, właściwość, indeksator lub zdarzenie i zezwalają na zastąpienia w klasie pochodnej. Na przykład tej metody może zostać przesłonięta przez wszystkie klasy, która dziedziczy on:  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 Implementacja elementu członkowskiego wirtualnego może zostać zmieniona przez [zastępowanie elementu członkowskiego](../../../csharp/language-reference/keywords/override.md) w klasie pochodnej. Aby uzyskać więcej informacji o sposobie używania `virtual` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedząc, gdy Użyj zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="remarks"></a>Uwagi  
 Po wywołaniu metody wirtualnej typ środowiska wykonawczego obiektu jest sprawdzany pod kątem zastępowanie elementu członkowskiego. Zastępowanie elementu członkowskiego w klasie pochodnej najbardziej nosi nazwę, która może być oryginalnego elementu członkowskiego, jeśli nie Klasa pochodna przesłoniła element członkowski.  
  
 Domyślnie są niewirtualną metody. Nie można zastąpić metody niewirtualnej.  
  
 Nie można użyć `virtual` modyfikator z `static`, `abstract`, `private`, lub `override` modyfikatorów. W poniższym przykładzie przedstawiono właściwości wirtualnych:  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Właściwości wirtualnych przypominają metody abstrakcyjne, z wyjątkiem różnice w deklaracji i wywołanie składni.  
  
-   Jest błędem `virtual` modyfikator na właściwość statyczna.  
  
-   Wirtualne właściwość dziedziczona może zostać przesłonięta w klasie pochodnej przez tym deklaracji właściwości, która używa `override` modyfikator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Shape` klasa zawiera dwie współrzędne `x`, `y`i `Area()` metoda wirtualna. Kształt różnych klas takich jak `Circle`, `Cylinder`, i `Sphere` dziedziczą `Shape` klasy i powierzchni jest obliczana dla każdego elementu. Każda klasa pochodna została ona właścicielem wykonania zastąpienie `Area()`.  
  
 Zwróć uwagę, że klasy dziedziczone `Circle`, `Sphere`, i `Cylinder` używają konstruktorów zainicjować klasy podstawowej, jak pokazano w poniższych deklaracji.  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Następujący program oblicza i wyświetla odpowiedniego obszaru dla każdego elementu za pomocą odpowiedniej implementacji `Area()` metody zgodnie z obiektu, który jest skojarzony z metodą.  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [new](../../../csharp/language-reference/keywords/new.md)
