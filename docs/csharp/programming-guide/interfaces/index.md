---
title: 'Interfejsy - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
  - 'interfaces [C#]'
  - 'C# language, interfaces'
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)

Interfejs zawiera definicje dla grupy powiązane funkcje, [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/keywords/struct.md) można zaimplementować.
  
Korzystając z interfejsów, można na przykład zawierać zachowanie z wielu źródeł w klasie. Czy funkcja jest ważna w języku C#, ponieważ język nie obsługują wielokrotnego dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenia dla struktur, ponieważ są faktycznie nie może dziedziczyć z innej struktury lub klasy.  
  
Zdefiniuj interfejs, za pomocą [interfejsu](../../language-reference/keywords/interface.md) — słowo kluczowe. jak w poniższym przykładzie pokazano.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

Nazwa struktury musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md). Według Konwencji nazwy interfejsu rozpoczynają się od wielkiej litery `I`.

Wszystkie klasy lub struktury, która implementuje <xref:System.IEquatable%601> interfejs musi zawierać definicję <xref:System.IEquatable%601.Equals%2A> metodę, która pasuje do podpisu, który określa interfejs. Dlatego możesz liczyć na klasę, która implementuje `IEquatable<T>` zawierać `Equals` metoda, za pomocą którego wystąpienia klasy można określić, czy jest równy do innego wystąpienia tej samej klasy.  
  
Definicja `IEquatable<T>` nie dostarcza implementację `Equals`. Interfejs definiuje tylko podpisu. W ten sposób interfejs w języku C# jest podobny do klasy abstrakcyjnej, w którym wszystkie metody są abstrakcyjne. Jednak klasy lub struktury, można zaimplementować wiele interfejsów, ale klasa może odziedziczyć tylko jedną klasę abstrakcyjną, czy nie. W związku z tym korzystając z interfejsów, można dołączyć zachowanie z wielu źródeł w klasie.  
  
Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Interfejsy może zawierać metody, właściwości, zdarzenia, indeksatorów lub dowolnej kombinacji tych typów cztery elementu członkowskiego. Aby uzyskać linki do przykładów, zobacz [sekcje pokrewne](../interfaces/index.md#BKMK_RelatedSections). Interfejs nie może zawierać stałe, pola, operatory, konstruktory wystąpień, finalizatory lub typów. Elementy członkowskie interfejsu są automatycznie publiczne, a nie mogą zawierać żadnych modyfikatory dostępu. Elementy członkowskie nie może być również [statyczne](../../language-reference/keywords/static.md).  
  
Aby implementować składowej interfejsu, odpowiedniego elementu członkowskiego klasy implementującej musi być publiczna, niestatycznej i mają taką samą nazwę i podpis, jak składowej interfejsu.  
  
Gdy klasa lub struktura implementuje interfejs, klasy lub struktury musi zapewniać implementację dla wszystkich elementów członkowskich, które definiuje interfejs. Sam interfejs zapewnia żadnych funkcji, która klasa lub struktura może dziedziczyć w taki sposób, może dziedziczyć klasy podstawowej funkcjonalności. Jednak jeśli klasa bazowa implementuje interfejs, każdej klasy, która jest pochodną klasy bazowej dziedziczy tę implementację.  
  
W poniższym przykładzie pokazano implementację <xref:System.IEquatable%601> interfejsu. Klasy implementującej `Car`, należy podać implementacja <xref:System.IEquatable%601.Equals%2A> metody.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Właściwości i indeksatorów w klasie, można zdefiniować dodatkowe metody dostępu właściwości lub indeksatora, który jest zdefiniowany w interfejsie. Na przykład interfejs może zadeklarować właściwości, która ma [uzyskać](../../language-reference/keywords/get.md) metody dostępu. Klasa, która implementuje interfejs można zadeklarować tej właściwości przy użyciu zarówno `get` i [ustaw](../../language-reference/keywords/set.md) metody dostępu. Jednakże jeśli właściwość lub indeksator używa jawnych implementacji, metod dostępu muszą być zgodne. Aby uzyskać więcej informacji dotyczących jawnych implementacji, zobacz [jawnej implementacji interfejsu](explicit-interface-implementation.md) i [właściwości interfejsu](../classes-and-structs/interface-properties.md).  

Interfejsy mogą dziedziczyć z innych interfejsów. Klasa może zawierać interfejs wielokrotnie za pośrednictwem klasy bazowej, która dziedziczy lub interfejsów, które dziedziczą inne interfejsy. Klasa może jednak zapewniać implementację interfejsu tylko jedna godzina i tylko jeśli klasa deklaruje interfejsu w ramach definicji klasy (`class ClassName : InterfaceName`). Jeśli interfejs jest dziedziczone, ponieważ dziedziczone klasy bazowej, która implementuje interfejs, klasa bazowa zawiera implementację składowych interfejsu. Klasa pochodna może jednak ponownie żadnych składowych interfejsu wirtualnego zamiast dziedziczona implementacja.  
  
Klasa bazowa również wdrożyć składowych interfejsu przy użyciu wirtualnych elementów członkowskich. W takim przypadku Klasa pochodna można zmienić zachowania interfejsu zastępowanie wirtualnych elementów członkowskich. Aby uzyskać więcej informacji na temat wirtualnych elementów członkowskich, zobacz [polimorfizm](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Podsumowanie interfejsów

Interfejs ma następujące właściwości:  

- Interfejs przypomina abstrakcyjną klasę bazową. Wszystkie klasy lub struktury, która implementuje interfejs musi implementować wszystkich jej członków.
- Nie można bezpośrednio utworzyć wystąpienia interfejsu. Jego członkowie są implementowane przez klasy lub struktury, która implementuje interfejs.
- Interfejsy mogą zawierać zdarzenia, indeksatory, metod i właściwości.
- Interfejsy zawierać żadnej implementacji metody.
- Klasa lub struktura może zaimplementować wiele interfejsów. Klasy mogą dziedziczyć z klasy bazowej i także implementować jeden lub więcej interfejsów.

## <a name="in-this-section"></a>W tej sekcji

[Implementacja interfejsu jawnego](explicit-interface-implementation.md)  
 Wyjaśnia, jak utworzyć element członkowski klasy, które są specyficzne dla interfejsu.  
  
 [Instrukcje: Jawne Implementowanie elementów interfejsu](how-to-explicitly-implement-interface-members.md)  
 Zawiera przykład sposobu jawne Implementowanie elementów interfejsów.  
  
 [Instrukcje: Jawne Implementowanie elementów dwóch interfejsów](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Zawiera przykład sposobu jawne Implementowanie elementów współpracuje z dziedziczenia.  
  
## <a name="BKMK_RelatedSections"></a> Sekcje pokrewne

- [Właściwości interfejsu](../classes-and-structs/interface-properties.md)  
- [Indeksatory w interfejsach](../indexers/indexers-in-interfaces.md)  
- [Instrukcje:  Zdarzenia implementowania interfejsu](../events/how-to-implement-interface-events.md)  
- [Klasy i struktury](../classes-and-structs/index.md)  
- [Dziedziczenie](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polimorfizm](../classes-and-structs/polymorphism.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Właściwości](../classes-and-structs/properties.md)  
- [Zdarzenia](../events/index.md)  
- [Indeksatory](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>polecany rozdział książki

[Interfejsy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) w [uczenia C# 3.0: Opanowanie podstaw C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
