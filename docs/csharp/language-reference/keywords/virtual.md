---
title: wirtualny - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 0a6eb7bfcd598eb54b4b0cc5661d219367da2238
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237392"
---
# <a name="virtual-c-reference"></a>virtual (odwołanie w C#)
`virtual` Słowo kluczowe jest używane do modyfikowania deklaracji metody, właściwości, indeksatora lub zdarzenia i umożliwia jej zastąpienie w klasie pochodnej. Na przykład tej metody może zostać przesłonięta przez wszystkie klasy, która dziedziczy on:  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 Implementacja członka wirtualnego mogą zostać zmienione przez [zastępującej składowej](../../../csharp/language-reference/keywords/override.md) w klasie pochodnej. Aby uzyskać więcej informacji o sposobie używania `virtual` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [, wiedząc, gdy Użyj zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="remarks"></a>Uwagi  
 Po wywołaniu metody wirtualnej typu run-time obiektu jest sprawdzane pod kątem zastępującej składowej. Zastępującej składowej w klasie najbardziej pochodnej jest wywoływana, który może być oryginalnego elementu członkowskiego, jeśli nie Klasa pochodna przesłoniła elementu członkowskiego.  
  
 Domyślnie metody są inne niż wirtualny. Nie można zastąpić metody niewirtualnej.  
  
 Nie można użyć `virtual` modyfikator z `static`, `abstract`, `private`, lub `override` modyfikatorów. Właściwość wirtualną można znaleźć w poniższym przykładzie:  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Właściwości wirtualne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywoływania.  
  
-   Jest to błąd, aby użyć `virtual` modyfikator na właściwość statyczna.  
  
-   Wirtualne właściwość dziedziczona może zostać przesłonięta w klasie pochodnej przez tym deklaracja właściwości, która używa `override` modyfikator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `Shape` klasa zawiera dwie współrzędne `x`, `y`i `Area()` metodę wirtualną. Klasy innego kształtu, takie jak `Circle`, `Cylinder`, i `Sphere` dziedziczą `Shape` klasy i obszar powierzchni jest obliczana dla każdego elementu. Każda klasa pochodna ma własną implementację zastąpienie `Area()`.  
  
 Należy zauważyć, że klasy dziedziczone `Circle`, `Sphere`, i `Cylinder` używają konstruktorów, które inicjowania klasy bazowej, jak pokazano w poniższej deklaracji.  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Następujący program oblicza i wyświetla odpowiedni obszar dla każdego elementu przez wywołanie odpowiedniej implementacji `Area()` metodę, zgodnie z obiektu, który jest skojarzony z metodą.  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
- [abstract](../../../csharp/language-reference/keywords/abstract.md)  
- [override](../../../csharp/language-reference/keywords/override.md)  
- [new](../../../csharp/language-reference/keywords/new.md)
