---
title: Ograniczanie dostępności metody dostępu C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: ca990693d29f8c8abd2e4ba2488a429a797afaec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596172"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)
Fragmenty [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) właściwości lub indeksatora są nazywane metodyą *dostępu*. Domyślnie te metody dostępu mają ten sam poziom widoczności lub dostępu do właściwości lub indeksatora, do którego należą. Aby uzyskać więcej informacji, zobacz [poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md). Jednak czasami warto ograniczyć dostęp do jednego z tych metod dostępu. Zazwyczaj obejmuje to ograniczenie dostępności `set` metody dostępu, zachowując `get` publicznie dostępną metodę dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 W tym przykładzie właściwość o nazwie `Name` `get` definiuje a i `set` akcesor. Metoda dostępu odbiera poziom dostępności samej właściwości, `public` w `set` tym przypadku, gdy metoda dostępu jest jawnie ograniczona przez zastosowanie modyfikatora dostępu [chronionego](../../language-reference/keywords/protected.md) do samej metody dostępu. `get`  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Ograniczenia dotyczące modyfikatorów dostępu w przypadku metod dostępu  
 Używanie modyfikatorów metody dostępu we właściwościach lub indeksatorach podlega następujących warunkom:  
  
- Nie można używać modyfikatorów metody dostępu dla interfejsu lub jawnej implementacji elementu członkowskiego [interfejsu](../../language-reference/keywords/interface.md) .  
  
- Modyfikatory metody dostępu można używać tylko wtedy, gdy właściwość lub indeksator ma zarówno `set` metody `get` dostępu, jak i. W takim przypadku modyfikator jest dozwolony tylko dla jednego z dwóch metod dostępu.  
  
- Jeśli właściwość lub indeksator ma modyfikator przesłonięcia, modyfikator metody dostępu musi być zgodny z akcesorem przesłoniętej metody dostępu, jeśli istnieje. [](../../language-reference/keywords/override.md)  
  
- Poziom dostępności na metodzie dostępu musi być bardziej restrykcyjny niż poziom dostępności właściwości lub indeksatora.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modyfikatory dostępu podczas zastępowania metod dostępu  
 Podczas przesłonięcia właściwości lub indeksatora zastępowane metody dostępu muszą być dostępne dla zastępujący kod. Ponadto dostępność właściwości/indeksatora i jego metod dostępu musi być zgodna z odpowiadającą jej przesłoniętą właściwością/indeksatorem oraz jej metod dostępu. Na przykład:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów  
 W przypadku użycia metody dostępu do zaimplementowania interfejsu metoda dostępu może nie mieć modyfikatora dostępu. Jednak w przypadku zaimplementowania interfejsu przy użyciu jednej metody dostępu, `get`takiej jak, inna metoda dostępu może mieć Modyfikator dostęp, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Domena dostępności metody dostępu  
 Jeśli używasz modyfikatora dostępu do akcesora, [domena dostępności](../../language-reference/keywords/accessibility-domain.md) metody dostępu jest określana przez ten modyfikator.  
  
 Jeśli nie używasz modyfikatora dostępu do akcesora, domena dostępności metody dostępu jest określana na podstawie poziomu dostępności właściwości lub indeksatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera trzy klasy, `BaseClass`, `DerivedClass`, i `MainClass`. Istnieją dwie właściwości w `BaseClass` `Name` i `Id` dla obu klas. W przykładzie pokazano, jak Właściwość `Id` włączona `DerivedClass` może być ukryta przez właściwość `Id` w `BaseClass` przypadku używania ograniczonego modyfikatora dostępu, takiego jak [Protected](../../language-reference/keywords/protected.md) lub [Private](../../language-reference/keywords/private.md). W związku z tym podczas przypisywania wartości do tej właściwości zamiast niej `BaseClass` wywoływana jest właściwość klasy. Zastąpienie modyfikatora dostępu [publicznego](../../language-reference/keywords/public.md) spowoduje udostępnienie właściwości.  
  
 W przykładzie pokazano również, że restrykcyjny modyfikator dostępu, taki `private` jak `protected`lub, `Name` na `set` akcesorze właściwości w programie `DerivedClass` uniemożliwia dostęp do akcesora i generuje błąd podczas przypisywania do go.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Komentarze  
 Zwróć uwagę, że w przypadku zastąpienia `new private string Id` deklaracji `new public string Id`przez, otrzymujesz dane wyjściowe:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Właściwości](./properties.md)
- [Indeksatory](../indexers/index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
