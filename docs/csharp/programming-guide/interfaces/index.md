---
title: Interfejsy — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 30c44b9f98bcc61d54b8103b6b40d14fd35715f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589177"
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)

Interfejs zawiera definicje dla grupy powiązanych funkcji, które może zaimplementować [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/keywords/struct.md) .
  
Korzystając z interfejsów, można na przykład uwzględnić zachowanie z wielu źródeł w klasie. Ta funkcja jest ważna w C# przypadku, gdy język nie obsługuje wielokrotnego dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenie dla struktur, ponieważ nie może faktycznie dziedziczyć z innej struktury lub klasy.  
  
Interfejs można zdefiniować za pomocą słowa kluczowego [Interface](../../language-reference/keywords/interface.md) . jak pokazano na poniższym przykładzie.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

Nazwa struktury musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md). Według Konwencji nazwy interfejsów zaczynają się od Wielkiej `I`litery.

Każda klasa lub struktura implementująca <xref:System.IEquatable%601> interfejs musi zawierać definicję <xref:System.IEquatable%601.Equals%2A> metody, która pasuje do sygnatury określanej przez interfejs. W związku z tym można obliczyć na klasie implementującej `IEquatable<T>` `Equals` metodę, za pomocą której wystąpienie klasy może określić, czy jest ono równe innemu wystąpieniu tej samej klasy.  
  
Definicja `IEquatable<T>` nie zawiera implementacji dla programu `Equals`. Interfejs definiuje tylko sygnaturę. W ten sposób interfejs w C# jest podobny do klasy abstrakcyjnej, w której wszystkie metody są abstrakcyjne. Jednak Klasa lub struktura może zaimplementować wiele interfejsów, ale Klasa może dziedziczyć tylko pojedynczą klasę, abstrakcyjną lub nie.
  
Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Interfejsy mogą zawierać metody, właściwości, zdarzenia, indeksatory lub dowolną kombinację tych czterech typów elementów członkowskich. Aby uzyskać linki do przykładów, zobacz sekcję [pokrewne](./index.md#BKMK_RelatedSections). Interfejs nie może zawierać stałych, pól, operatorów, konstruktorów wystąpień, finalizatorów lub typów. Elementy członkowskie interfejsu są automatycznie publiczne i nie mogą zawierać żadnych modyfikatorów dostępu. Elementy członkowskie również nie mogą być [statyczne](../../language-reference/keywords/static.md).  
  
Aby zaimplementować element członkowski interfejsu, odpowiadający mu element członkowski klasy implementującej musi być publiczny, niestatyczny i mieć taką samą nazwę i podpis jak element członkowski interfejsu.  
  
Gdy Klasa lub struktura implementuje interfejs, Klasa lub struktura musi dostarczyć implementację dla wszystkich elementów członkowskich, które definiuje interfejs. Sam interfejs nie udostępnia funkcji, które Klasa lub struktura może dziedziczyć w sposób, w jaki może dziedziczyć funkcje klasy podstawowej. Jeśli jednak Klasa bazowa implementuje interfejs, każda klasa, która jest pochodną klasy bazowej, dziedziczy tę implementację.  
  
Poniższy przykład pokazuje implementację <xref:System.IEquatable%601> interfejsu. Implementacja klasy, `Car`, musi dostarczyć implementację <xref:System.IEquatable%601.Equals%2A> metody.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Właściwości i indeksatory klasy mogą definiować dodatkowe metody dostępu do właściwości lub indeksatora zdefiniowanego w interfejsie. Na przykład interfejs może deklarować właściwość, która ma metodę dostępu [Get](../../language-reference/keywords/get.md) . Klasa implementująca interfejs może zadeklarować tę samą Właściwość zarówno jako `get` akcesora, jak i [zestawu](../../language-reference/keywords/set.md) . Jeśli jednak właściwość lub indeksator używa jawnej implementacji, metody dostępu muszą być zgodne. Aby uzyskać więcej informacji na temat implementacji jawnej, zobacz [jawne implementacje interfejsu](explicit-interface-implementation.md) i [Właściwości interfejsu](../classes-and-structs/interface-properties.md).  

Interfejsy mogą dziedziczyć z innych interfejsów. Klasa może zawierać wiele razy interfejs za pomocą klas bazowych, które dziedziczy lub przez interfejsy, które dziedziczy inne interfejsy. Jednak Klasa może zapewnić implementację interfejsu tylko jeden raz i tylko wtedy, gdy Klasa deklaruje interfejs jako część definicji klasy (`class ClassName : InterfaceName`). Jeśli interfejs jest dziedziczony, ponieważ dziedziczy Klasa bazowa implementująca interfejs, Klasa bazowa zapewnia implementację elementów członkowskich interfejsu. Jednak Klasa pochodna może zaimplementować wszystkie elementy członkowskie interfejsu wirtualnego zamiast korzystać z dziedziczonej implementacji.  
  
Klasa bazowa może również implementować składowe interfejsu za pomocą wirtualnych elementów członkowskich. W takim przypadku Klasa pochodna może zmienić zachowanie interfejsu przez zastąpienie wirtualnych elementów członkowskich. Aby uzyskać więcej informacji na temat wirtualnych elementów członkowskich, zobacz [polimorfizm](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Podsumowanie interfejsów

Interfejs ma następujące właściwości:  

- Interfejs jest podobny do abstrakcyjnej klasy bazowej zawierającej tylko abstrakcyjne elementy członkowskie. Każda klasa lub struktura implementująca interfejs musi implementować wszystkie jego elementy członkowskie.
- Nie można bezpośrednio utworzyć wystąpienia interfejsu. Jego składowe są implementowane przez dowolną klasę lub strukturę, która implementuje interfejs.
- Interfejsy mogą zawierać zdarzenia, indeksatory, metody i właściwości.
- Interfejsy nie zawierają implementacji metod.
- Klasa lub struktura może zaimplementować wiele interfejsów. Klasa może dziedziczyć klasę bazową, a także zaimplementować jeden lub więcej interfejsów.

## <a name="in-this-section"></a>W tej sekcji

[Implementacja interfejsu jawnego](explicit-interface-implementation.md)  
 Wyjaśnia, jak utworzyć element członkowski klasy, który jest specyficzny dla interfejsu.  
  
 [Instrukcje: Jawnie Implementuj składowe interfejsu](how-to-explicitly-implement-interface-members.md)  
 Przedstawia przykład sposobu jawnego implementowania elementów członkowskich interfejsów.  
  
 [Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsów](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Przedstawia przykład sposobu jawnego implementowania elementów członkowskich interfejsów przy użyciu dziedziczenia.  
  
## <a name="BKMK_RelatedSections"></a>Sekcje pokrewne

- [Właściwości interfejsu](../classes-and-structs/interface-properties.md)  
- [Indeksatory w interfejsach](../indexers/indexers-in-interfaces.md)  
- [Instrukcje:  Implementowanie zdarzeń interfejsu](../events/how-to-implement-interface-events.md)  
- [Klasy i struktury](../classes-and-structs/index.md)  
- [Dziedziczenie](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polimorfizm](../classes-and-structs/polymorphism.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Właściwości](../classes-and-structs/properties.md)  
- [Zdarzenia](../events/index.md)  
- [Indeksatory](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>polecany rozdział książki

[Interfejsy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) w [uczeniu C# 3,0: Główne podstawy C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
