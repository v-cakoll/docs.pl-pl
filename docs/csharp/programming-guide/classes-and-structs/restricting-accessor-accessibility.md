---
title: Ograniczanie ułatwień dostępu — przewodnik programowania języka C#
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714694"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Ograniczanie dostępności metody dostępu (Przewodnik programowania w języku C#)
[Get](../../language-reference/keywords/get.md) i [set](../../language-reference/keywords/set.md) części właściwości lub indeksatora są nazywane *akcesorów*. Domyślnie te akcesory mają taką samą widoczność lub poziom dostępu właściwości lub indeksatora, do którego należą. Aby uzyskać więcej informacji, zobacz [poziomy ułatwień dostępu](../../language-reference/keywords/accessibility-levels.md). Jednak czasami warto ograniczyć dostęp do jednego z tych akcesorów. Zazwyczaj wiąże się to z ograniczeniem dostępności `set` akcesora, przy jednoczesnym zachowaniu `get` akcesor publicznie dostępne. Przykład:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 W tym przykładzie właściwość `Name` o `get` nazwie `set` definiuje a i akcesor. Akcesor `get` odbiera poziom ułatwień `public` dostępu samej właściwości, w tym przypadku, podczas gdy `set` akcesor jest jawnie ograniczony przez zastosowanie modyfikatora dostępu [chronionego](../../language-reference/keywords/protected.md) do samego akcesora.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Ograniczenia dotyczące modyfikatorów dostępu w programach akcesorów  
 Korzystanie modyfikatorów akcesora na właściwości lub indeksatorów podlega następujących warunkach:  
  
- Nie można użyć modyfikatorów akcesora w interfejsie lub implementacji elementu członkowskiego [interfejsu](../../language-reference/keywords/interface.md) jawnego.  
  
- Modyfikatory akcesora można używać tylko `set` `get` wtedy, gdy właściwość lub indeksator ma zarówno i akcesorów. W takim przypadku modyfikator jest dozwolone tylko na jednym z dwóch akcesorów.  
  
- Jeśli właściwość lub indeksator ma modyfikator [zastępowania,](../../language-reference/keywords/override.md) modyfikator akcesormusi odpowiadać akcesor akcesor, jeśli istnieje.  
  
- Poziom ułatwień dostępu na akcesor musi być bardziej restrykcyjne niż poziom ułatwień dostępu na właściwości lub indeksatora się.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modyfikatory dostępu na zalegające akcesory  
 Po zastąpieniu właściwości lub indeksatora, zastąpione akcesory muszą być dostępne dla kodu nadrzędnego. Ponadto dostępność zarówno właściwości/indeksatora i jego akcesorów musi odpowiadać odpowiedniej właściwości zastąpione/indeksator i jego akcesorów. Przykład:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Implementowanie interfejsów  
 Korzystając z akcesora do zaimplementowania interfejsu, akcesor może nie mieć modyfikator dostępu. Jednak jeśli zaimplementujesz interfejs przy użyciu `get`jednego akcesora, takich jak , inny akcesor może mieć modyfikator dostępu, jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Domena ułatwień dostępu  
 Jeśli używasz modyfikatora dostępu na akcesor, [domena ułatwień dostępu](../../language-reference/keywords/accessibility-domain.md) jest określana przez ten modyfikator.  
  
 Jeśli nie używasz modyfikatora dostępu w akcesorze, domena ułatwień dostępu jest określana przez poziom ułatwień dostępu właściwości lub indeksatora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera trzy `BaseClass` `DerivedClass`klasy, `MainClass`, , i . Istnieją dwie właściwości na `BaseClass` `Name` , `Id` i na obu klasach. W przykładzie pokazano, `Id` `DerivedClass` jak właściwość na `Id` mogą `BaseClass` być ukryte przez właściwość podczas korzystania z modyfikatora dostępu restrykcyjnego, takich jak [chronione](../../language-reference/keywords/protected.md) lub [prywatne](../../language-reference/keywords/private.md). W związku z tym po przypisaniu `BaseClass` wartości do tej właściwości, właściwość na klasy jest wywoływana zamiast. Zastąpienie modyfikatora dostępu [publicznie](../../language-reference/keywords/public.md) spowoduje, że właściwość będzie dostępna.  
  
 W przykładzie pokazano również, że modyfikator dostępu `set` ograniczającego, `Name` takich `DerivedClass` jak `private` lub `protected`, na akcesor właściwości w uniemożliwia dostęp do akcesora i generuje błąd po przypisaniu do niego.  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Komentarze  
 Należy zauważyć, że `new private string Id` jeśli `new public string Id`zastąpisz deklarację przez , otrzymasz dane wyjściowe:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Właściwości](./properties.md)
- [Indexers](../indexers/index.md) (Indeksatory)
- [Modyfikatory dostępu](./access-modifiers.md)
