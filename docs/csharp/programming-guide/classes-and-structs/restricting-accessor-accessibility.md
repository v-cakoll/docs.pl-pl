---
title: Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: bf9ead7934630d3974657107ca38e08bbd3bed85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)
[Uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustawić](../../../csharp/language-reference/keywords/set.md) fragmenty właściwość lub indeksator są nazywane *metody dostępu*. Domyślnie te metody dostępu mają taką samą widoczność lub poziom dostępu: te właściwości lub indeksatora, do którego należą. Aby uzyskać więcej informacji, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). Jednak czasami jest przydatne w celu ograniczenia dostępu do jednej z tych metod dostępu. Zazwyczaj polega to na ograniczanie dostępności `set` akcesor przy zachowaniu `get` akcesor publicznie. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 W tym przykładzie właściwość o nazwie `Name` definiuje `get` i `set` metody dostępu. `get` Akcesor odbiera poziom dostępności właściwość, `public` w takim przypadku podczas `set` akcesor jawnie jest ograniczony przez zastosowanie [chronione](../../../csharp/language-reference/keywords/protected.md) modyfikator dostępu do Metoda dostępu samej siebie.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Ograniczenia dotyczące modyfikatorów dostępu  
 Za pomocą modyfikatorów dostępu na właściwości i indeksatorów podlega następujące warunki:  
  
-   Nie można używać modyfikatorów dostępu na interfejs lub jawnego [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacja elementu członkowskiego.  
  
-   Modyfikatory dostępu można użyć tylko wtedy, gdy właściwość lub indeksator ma zarówno atrybut `set` i `get` metody dostępu. W takim przypadku modyfikator jest dozwolony na tylko jedna z dwóch metod dostępu.  
  
-   Jeśli właściwość lub indeksator ma [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator, modyfikator dostępu muszą być zgodne akcesor przesłoniętej metody dostępu, jeśli istnieje.  
  
-   Poziom dostępności w metodzie dostępu musi być bardziej restrykcyjny niż poziom dostępności na właściwość lub indeksator samej siebie.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modyfikatory dostępu na zastępowanie metody dostępu  
 Aby zastąpić właściwość lub indeksator, przesłoniętej metody dostępu muszą być dostępne dla zastępowanie kodu. Ponadto poziom dostępności zarówno właściwości/indeksatora i który metody dostępu muszą być zgodne odpowiednie właściwości/indeksatora przesłoniętych i metody dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów  
 Gdy używasz metody dostępu do zaimplementowania interfejsu metodzie dostępu nie mogą mieć modyfikatora dostępu. Jednak jeśli implementuje interfejs za pomocą jedną metodę dostępu, takich jak `get`, inne metody dostępu może mieć modyfikatora dostępu, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a>Domena dostępności metody dostępu  
 Jeśli używasz modyfikatora dostępu w metodzie dostępu, [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md) metody dostępu jest określany przez modyfikator.  
  
 Jeśli nie używasz modyfikatora dostępu w metodzie dostępu, domena dostępności metody dostępu jest określany przez właściwość lub indeksator poziom dostępności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera trzy klasy `BaseClass`, `DerivedClass`, i `MainClass`. Istnieją dwie właściwości na `BaseClass`, `Name` i `Id` w obu klasach. W przykładzie pokazano, jak właściwość `Id` na `DerivedClass` może być ukryty przez właściwość `Id` na `BaseClass` korzystając modyfikator dostępu ograniczające takich jak [chronione](../../../csharp/language-reference/keywords/protected.md) lub [ prywatne](../../../csharp/language-reference/keywords/private.md). W związku z tym podczas można przypisać wartości do tej właściwości, właściwość `BaseClass` klasy jest wywoływana zamiast tego. Modyfikator dostępu przez zastąpienie [publicznego](../../../csharp/language-reference/keywords/public.md) będzie Udostępnij właściwość.  
  
 W przykładzie pokazano także który modyfikator dostępu ograniczające, takich jak `private` lub `protected`na `set` akcesor `Name` właściwości w `DerivedClass` uniemożliwia dostęp do metody dostępu i generuje błąd podczas przypisywania do go.  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a>Komentarze  
 Zwróć uwagę, że jeśli zamienisz deklaracji `new private string Id` przez `new public string Id`, uzyskać dane wyjściowe:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
