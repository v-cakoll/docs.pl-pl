---
title: Ograniczanie dostępności metody dostępu C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: a332fef814f0c81914eb7b8c308de68f719fbaac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714694"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)
Fragmenty [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) właściwości lub indeksatora są nazywane metodyą *dostępu*. Domyślnie te metody dostępu mają ten sam poziom widoczności lub dostępu do właściwości lub indeksatora, do którego należą. Aby uzyskać więcej informacji, zobacz [poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md). Jednak czasami warto ograniczyć dostęp do jednego z tych metod dostępu. Zazwyczaj obejmuje to ograniczenie dostępności metody dostępu `set`, przy jednoczesnym zachowaniu dostępu `get` publicznie. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 W tym przykładzie właściwość o nazwie `Name` definiuje metodę dostępu `get` i `set`. Metoda dostępu `get` odbiera poziom dostępności samej właściwości, `public` w tym przypadku, podczas gdy metoda dostępu `set` jest jawnie ograniczona przez zastosowanie modyfikatora dostępu [chronionego](../../language-reference/keywords/protected.md) do samej metody dostępu.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Ograniczenia dotyczące modyfikatorów dostępu w przypadku metod dostępu  
 Używanie modyfikatorów metody dostępu we właściwościach lub indeksatorach podlega następujących warunkom:  
  
- Nie można używać modyfikatorów metody dostępu dla interfejsu lub jawnej implementacji elementu członkowskiego [interfejsu](../../language-reference/keywords/interface.md) .  
  
- Modyfikatory metod dostępu można używać tylko wtedy, gdy właściwość lub indeksator ma zarówno metody dostępu `set`, jak i `get`. W takim przypadku modyfikator jest dozwolony tylko dla jednego z dwóch metod dostępu.  
  
- Jeśli właściwość lub indeksator ma modyfikator [przesłonięcia](../../language-reference/keywords/override.md) , modyfikator metody dostępu musi być zgodny z akcesorem przesłoniętej metody dostępu, jeśli istnieje.  
  
- Poziom dostępności na metodzie dostępu musi być bardziej restrykcyjny niż poziom dostępności właściwości lub indeksatora.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modyfikatory dostępu podczas zastępowania metod dostępu  
 Podczas przesłonięcia właściwości lub indeksatora zastępowane metody dostępu muszą być dostępne dla zastępujący kod. Ponadto dostępność właściwości/indeksatora i jego metod dostępu musi być zgodna z odpowiadającą jej przesłoniętą właściwością/indeksatorem oraz jej metod dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów  
 W przypadku użycia metody dostępu do zaimplementowania interfejsu metoda dostępu może nie mieć modyfikatora dostępu. Jednak w przypadku zaimplementowania interfejsu przy użyciu jednej metody dostępu, takiej jak `get`, inna metoda dostępu może mieć Modyfikator dostępu, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Domena dostępności metody dostępu  
 Jeśli używasz modyfikatora dostępu do akcesora, [domena dostępności](../../language-reference/keywords/accessibility-domain.md) metody dostępu jest określana przez ten modyfikator.  
  
 Jeśli nie używasz modyfikatora dostępu do akcesora, domena dostępności metody dostępu jest określana na podstawie poziomu dostępności właściwości lub indeksatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera trzy klasy, `BaseClass`, `DerivedClass`i `MainClass`. Na `BaseClass`znajdują się dwie właściwości, `Name` i `Id` dla obu klas. W przykładzie pokazano, jak Właściwość `Id` na `DerivedClass` może być ukryta przez właściwość `Id` na `BaseClass` w przypadku używania ograniczonego modyfikatora dostępu, takiego jak [Protected](../../language-reference/keywords/protected.md) lub [Private](../../language-reference/keywords/private.md). W związku z tym, gdy przypiszesz wartości do tej właściwości, w zamian zostanie wywołana właściwość klasy `BaseClass`. Zastąpienie modyfikatora dostępu [publicznego](../../language-reference/keywords/public.md) spowoduje udostępnienie właściwości.  
  
 W przykładzie pokazano również, że restrykcyjny modyfikator dostępu, taki jak `private` lub `protected`, `set` metoda dostępu do właściwości `Name` w `DerivedClass` uniemożliwia dostęp do akcesora i generuje błąd podczas przypisywania do niego.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Komentarze  
 Zwróć uwagę, że w przypadku zastąpienia deklaracji `new private string Id` przez `new public string Id`otrzymujesz dane wyjściowe:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Indeksatory](../indexers/index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
