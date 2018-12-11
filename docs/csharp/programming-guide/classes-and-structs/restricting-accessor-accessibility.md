---
title: Ograniczanie dostępności metody dostępu — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: d168444bb2e7df6aa71d729a44bd6f20f7bfce3d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242038"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)
[Uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustaw](../../../csharp/language-reference/keywords/set.md) noszą nazwę porcjach właściwości lub indeksatora *Akcesory*. Domyślnie te metody dostępu mają ten sam poziom widoczności lub dostęp do właściwości lub indeksatora, do której należą. Aby uzyskać więcej informacji, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). Jednak czasami jest przydatne ograniczyć dostęp do jednej z tych metod dostępu. Zwykle wymaga to, ograniczenie dostępności `set` akcesor przy zachowaniu `get` publicznie dostępne metody dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 W tym przykładzie właściwość o nazwie `Name` definiuje `get` i `set` metody dostępu. `get` Akcesor odbiera poziom ułatwień dostępu właściwości, `public` while, w tym przypadku `set` akcesor jawnie jest ograniczony przez zastosowanie [chronione](../../../csharp/language-reference/keywords/protected.md) modyfikator dostępu do Metoda dostępu sam.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Ograniczenia dotyczące modyfikatorów dostępu  
 Za pomocą modyfikatorów dostępu na właściwości i indeksatorów podlega tych warunków:  
  
-   Nie można używać modyfikatorów dostępu na interfejs lub jawnie [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji elementu członkowskiego.  
  
-   Modyfikatory dostępu można użyć tylko wtedy, gdy właściwość lub indeksator zarówno `set` i `get` metod dostępu. W tym przypadku modyfikator jest dozwolony na tylko jednego z dwóch metod dostępu.  
  
-   Jeśli właściwość lub indeksator ma [zastąpienia](../../../csharp/language-reference/keywords/override.md) modyfikator, modyfikator dostępu muszą być zgodne dostępu przesłonięte metody dostępu, jeśli istnieje.  
  
-   Poziom dostępności metody dostępu musi być bardziej restrykcyjny niż poziom dostępności na właściwość lub indeksator sam.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modyfikatory dostępu w przypadku przesłaniania metody dostępu  
 Gdy zastąpisz właściwość lub indeksator przesłoniętych metod dostępu muszą być dostępne dla kodu nadrzędnych. Ponadto dostępność właściwości/indeksatora i jego metod dostępu muszą być zgodne, odpowiedni zastąpione właściwości/indeksatora i jego metod dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów.  
 Gdy używasz metody dostępu do zaimplementowania interfejsu akcesor nie może mieć modyfikatora dostępu. Jednak jeśli zaimplementować interfejs za pomocą jedną metodę dostępu, takich jak `get`, inne metody dostępu może mieć modyfikatora dostępu, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a>Domena dostępności metody dostępu  
 Użycie modyfikatora dostępu dla metody dostępu, [domena dostępności](../../../csharp/language-reference/keywords/accessibility-domain.md) metody dostępu jest określana przez ten modyfikator.  
  
 Jeśli nie użyto modyfikatora dostępu na akcesor, domena dostępności metody dostępu jest określany przez poziom ułatwień dostępu właściwości lub indeksatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera trzy klasy `BaseClass`, `DerivedClass`, i `MainClass`. Istnieją dwie właściwości na `BaseClass`, `Name` i `Id` w obu klasach. W przykładzie pokazano, jak właściwość `Id` na `DerivedClass` może być ukryta przez właściwość `Id` na `BaseClass` zastosowania modyfikatora dostępu ograniczające takich jak [chronione](../../../csharp/language-reference/keywords/protected.md) lub [ prywatne](../../../csharp/language-reference/keywords/private.md). W związku z tym, kiedy przypisujesz wartości tej właściwości, właściwość na `BaseClass` zamiast tego wywoływany jest klasa. Modyfikator dostępu przez zastąpienie [publicznych](../../../csharp/language-reference/keywords/public.md) spowoduje, że właściwość dostępny.  
  
 W przykładzie pokazano również, modyfikator dostępu ograniczające, takich jak `private` lub `protected`na `set` akcesor `Name` właściwość `DerivedClass` uniemożliwia dostęp do metody dostępu i generuje błąd, po przypisaniu do go.  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a>Komentarze  
 Należy zauważyć, że jeżeli wymienisz deklaracji `new private string Id` przez `new public string Id`, otrzymasz dane wyjściowe:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
