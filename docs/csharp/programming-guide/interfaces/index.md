---
title: Interfejsy (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 3b6cdffdaab508d898e7caa8c93ac0f7b1365d01
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408883"
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)
Interfejs zawiera definicje dla grupy powiązane funkcje, [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) można zaimplementować.  
  
 Korzystając z interfejsów, można na przykład zawierać zachowanie z wielu źródeł w klasie. Czy funkcja jest ważna w języku C#, ponieważ język nie obsługują wielokrotnego dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenia dla struktur, ponieważ są faktycznie nie może dziedziczyć z innej struktury lub klasy.  
  
 Zdefiniuj interfejs, za pomocą [interfejsu](../../../csharp/language-reference/keywords/interface.md) — słowo kluczowe, co ilustruje poniższy przykład.  
  
 [!code-csharp[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 Wszystkie klasy lub struktury, która implementuje <xref:System.IEquatable%601> interfejs musi zawierać definicję <xref:System.IEquatable%601.Equals%2A> metodę, która pasuje do podpisu, który określa interfejs. Dlatego możesz liczyć na klasę, która implementuje `IEquatable<T>` zawierać `Equals` metoda, za pomocą którego wystąpienia klasy można określić, czy jest równy do innego wystąpienia tej samej klasy.  
  
 Definicja `IEquatable<T>` nie dostarcza implementację `Equals`. Interfejs definiuje tylko podpisu. W ten sposób interfejs w języku C# jest podobny do klasy abstrakcyjnej, w którym wszystkie metody są abstrakcyjne. Jednak klasy lub struktury, można zaimplementować wiele interfejsów, ale klasa może odziedziczyć tylko jedną klasę abstrakcyjną, czy nie. W związku z tym korzystając z interfejsów, można dołączyć zachowanie z wielu źródeł w klasie.  
  
 Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Interfejsy może zawierać metody, właściwości, zdarzenia, indeksatorów lub dowolnej kombinacji tych typów cztery elementu członkowskiego. Aby uzyskać linki do przykładów, zobacz [sekcje pokrewne](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections). Interfejs nie może zawierać stałe, pola, operatory, konstruktory wystąpień, finalizatory lub typów. Elementy członkowskie interfejsu są automatycznie publiczne, a nie mogą zawierać żadnych modyfikatory dostępu. Elementy członkowskie nie może być również [statyczne](../../../csharp/language-reference/keywords/static.md).  
  
 Aby implementować składowej interfejsu, odpowiedniego elementu członkowskiego klasy implementującej musi być publiczna, niestatycznej i mają taką samą nazwę i podpis, jak składowej interfejsu.  
  
 Gdy klasa lub struktura implementuje interfejs, klasy lub struktury musi zapewniać implementację dla wszystkich elementów członkowskich, które definiuje interfejs. Sam interfejs zapewnia żadnych funkcji, która klasa lub struktura może dziedziczyć w taki sposób, może dziedziczyć klasy podstawowej funkcjonalności. Jednak jeśli klasa bazowa implementuje interfejs, każdej klasy, która jest pochodną klasy bazowej dziedziczy tę implementację.  
  
 W poniższym przykładzie pokazano implementację IEquatable < T\> interfejsu. Klasy implementującej `Car`, należy podać implementacja <xref:System.IEquatable%601.Equals%2A> metody.  
  
 [!code-csharp[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 Właściwości i indeksatorów w klasie, można zdefiniować dodatkowe metody dostępu właściwości lub indeksatora, który jest zdefiniowany w interfejsie. Na przykład interfejs może zadeklarować właściwości, która ma [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu. Klasa, która implementuje interfejs można zadeklarować tej właściwości przy użyciu zarówno `get` i [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu. Jednakże jeśli właściwość lub indeksator używa jawnych implementacji, metod dostępu muszą być zgodne. Aby uzyskać więcej informacji dotyczących jawnych implementacji, zobacz [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) i [właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).  
  
 Interfejsy mogą zawierać inne interfejsy. Klasa może zawierać interfejs wielokrotnie za pośrednictwem klasy bazowej, która dziedziczy lub interfejsów, które implementują inne interfejsy. Klasa może jednak zapewniać implementację interfejsu tylko jedna godzina i tylko jeśli klasa deklaruje interfejsu w ramach definicji klasy (`class ClassName : InterfaceName`). Jeśli interfejs jest dziedziczone, ponieważ dziedziczone klasy bazowej, która implementuje interfejs, klasa bazowa zawiera implementację składowych interfejsu. Klasa pochodna może jednak ponownie składowych interfejsu zamiast dziedziczona implementacja.  
  
 Klasa bazowa również wdrożyć składowych interfejsu przy użyciu wirtualnych elementów członkowskich. W takim przypadku Klasa pochodna można zmienić zachowania interfejsu zastępowanie wirtualnych elementów członkowskich. Aby uzyskać więcej informacji na temat wirtualnych elementów członkowskich, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Podsumowanie interfejsów  
 Interfejs ma następujące właściwości:  
  
-   Interfejs przypomina abstrakcyjną klasę bazową. Wszystkie klasy lub struktury, która implementuje interfejs musi implementować wszystkich jej członków.  
  
-   Nie można bezpośrednio utworzyć wystąpienia interfejsu. Jego członkowie są implementowane przez klasy lub struktury, która implementuje interfejs.  
  
-   Interfejsy mogą zawierać zdarzenia, indeksatory, metod i właściwości.  
  
-   Interfejsy zawierać żadnej implementacji metody.  
  
-   Klasa lub struktura może zaimplementować wiele interfejsów. Klasy mogą dziedziczyć z klasy bazowej i także implementować jeden lub więcej interfejsów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementacja interfejsu jawnego](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 Wyjaśnia, jak utworzyć element członkowski klasy, które są specyficzne dla interfejsu.  
  
 [Instrukcje: jawne implementowanie elementów interfejsu](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 Zawiera przykład sposobu jawne Implementowanie elementów interfejsów.  
  
 [Instrukcje: jawne implementowanie elementów dwóch interfejsów](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 Zawiera przykład sposobu jawne Implementowanie elementów współpracuje z dziedziczenia.  
  
##  <a name="BKMK_RelatedSections"></a> Sekcje pokrewne  
  
-   [Właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Indeksatory w interfejsach](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Porady: zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
  
-   [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Polecany rozdział książki  
 [Interfejsy](https://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) w [Nauka języka C# 3.0: Opanuj podstawy języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
