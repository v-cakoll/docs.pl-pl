---
title: Interfejsy — przewodnik programowania Języka C#
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: f4ee269f41e79562c113a7627816f797b083095e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79157081"
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)

Interfejs zawiera definicje dla grupy powiązanych funkcji, które [klasa](../../language-reference/keywords/class.md) nieabstrakcyjna lub [struktury](../../language-reference/builtin-types/struct.md) musi implementować. Interfejs może `static` definiować metody, które muszą mieć implementację. Interfejs może zapewnić implementację domyślną dla dowolnego lub wszystkich jego zadeklarowanych elementów członkowskich wystąpienia. Interfejs nie może zadeklarować danych wystąpienia, takich jak pola, właściwości auto implementowane lub zdarzenia podobne do właściwości.

Za pomocą interfejsów, można na przykład uwzględnić zachowanie z wielu źródeł w klasie. Ta funkcja jest ważna w języku C#, ponieważ język nie obsługuje wiele dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenie dla struktur, ponieważ nie mogą one faktycznie dziedziczyć z innej struktury lub klasy.

Interfejs można zdefiniować przy użyciu słowa kluczowego [interfejsu,](../../language-reference/keywords/interface.md) jak pokazano w poniższym przykładzie.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Nazwa interfejsu musi być prawidłową [nazwą identyfikatora C#.](../inside-a-program/identifier-names.md) Zgodnie z konwencją nazwy `I`interfejsów zaczynają się od kapitału .

Każda klasa lub struktura, <xref:System.IEquatable%601> która implementuje interfejs <xref:System.IEquatable%601.Equals%2A> musi zawierać definicję dla metody, która pasuje do podpisu, który określa interfejs. W rezultacie można liczyć na klasy, `IEquatable<T>` która `Equals` implementuje zawierać metodę, za pomocą której wystąpienie klasy można określić, czy jest równa inne wystąpienie tej samej klasy.

Definicja `IEquatable<T>` nie zapewnia implementacji `Equals`dla . Klasa lub struktura może implementować wiele interfejsów, ale klasa może dziedziczyć tylko z jednej klasy.

Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Elementy członkowskie klasy](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Interfejsy mogą zawierać metody wystąpienia, właściwości, zdarzenia, indeksatory lub dowolną kombinację tych czterech typów elementów członkowskich. Interfejsy mogą zawierać konstruktory statyczne, pola, stałe lub operatory. Aby uzyskać łącza do przykładów, zobacz [Sekcje pokrewne](./index.md#BKMK_RelatedSections). Interfejs nie może zawierać pól wystąpienia, konstruktorów wystąpień lub finalizatorów. Elementy członkowskie interfejsu są domyślnie publiczne.

Aby zaimplementować element członkowski interfejsu, odpowiedni element członkowski klasy implementującej musi być publiczny, niestatyczny i mieć taką samą nazwę i podpis jak element członkowski interfejsu.

Gdy klasa lub struktura implementuje interfejs, klasy lub struktury musi zapewnić implementację dla wszystkich elementów członkowskich, które reprezentuje interfejs, ale nie zapewnia implementację domyślną dla. Jednak jeśli klasa podstawowa implementuje interfejs, każda klasa, która pochodzi z klasy podstawowej dziedziczy tej implementacji.

W poniższym przykładzie przedstawiono <xref:System.IEquatable%601> implementację interfejsu. Klasa implementująca , `Car`musi zapewnić <xref:System.IEquatable%601.Equals%2A> implementację metody.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Właściwości i indeksatory klasy można zdefiniować dodatkowe akcesory dla właściwości lub indeksatora, który jest zdefiniowany w interfejsie. Na przykład interfejs może zadeklarować właściwość, która ma [get](../../language-reference/keywords/get.md) akcesor. Klasa, która implementuje interfejs można zadeklarować `get` tej samej właściwości z a i [set](../../language-reference/keywords/set.md) akcesor. Jednak jeśli właściwość lub indeksator używa jawnej implementacji, akcesory muszą być zgodne. Aby uzyskać więcej informacji na temat implementacji jawnej, zobacz [Implementacja interfejsu jawnego](explicit-interface-implementation.md) i [właściwości interfejsu](../classes-and-structs/interface-properties.md).

Interfejsy mogą dziedziczyć z jednego lub więcej interfejsów. Interfejs pochodny dziedziczy elementy członkowskie z jego interfejsów podstawowych. Klasa, która implementuje interfejs pochodny musi implementować wszystkie elementy członkowskie w interfejsie pochodnym, w tym wszystkie elementy członkowskie interfejsów podstawowych interfejsu pochodnego. Ta klasa może być niejawnie konwertowane do interfejsu pochodnego lub dowolnego z jego interfejsów podstawowych. Klasa może zawierać interfejs wiele razy za pośrednictwem klas podstawowych, które dziedziczy lub za pośrednictwem interfejsów, które dziedziczą inne interfejsy. Jednak klasa może zapewnić implementację interfejsu tylko jeden raz i tylko wtedy, gdy klasa deklaruje`class ClassName : InterfaceName`interfejs jako część definicji klasy ( ). Jeśli interfejs jest dziedziczony, ponieważ odziedziczył klasę podstawową, która implementuje interfejs, klasa podstawowa zapewnia implementację elementów członkowskich interfejsu. Jednak klasa pochodna można ponownie zaimplementować żadnych członków interfejsu wirtualnego zamiast przy użyciu dziedziczonej implementacji. Gdy interfejsy deklarują domyślną implementację metody, każda klasa implementująca ten interfejs dziedziczy tę implementację. Implementacje zdefiniowane w interfejsach są wirtualne i klasy implementującej może zastąpić tej implementacji.

Klasa podstawowa może również implementować elementy członkowskie interfejsu przy użyciu elementów członkowskich wirtualnych. W takim przypadku klasy pochodnej można zmienić zachowanie interfejsu przez zastąpienie członków wirtualnych. Aby uzyskać więcej informacji na temat członków wirtualnych, zobacz [Polimorfizm](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Podsumowanie interfejsów

Interfejs ma następujące właściwości:

- Interfejs jest zazwyczaj jak abstrakcyjna klasa podstawowa z tylko abstrakcyjne elementy członkowskie. Każda klasa lub struktura, która implementuje interfejs musi implementować wszystkie jego elementy członkowskie. Opcjonalnie interfejs może zdefiniować implementacje domyślne dla niektórych lub wszystkich jego elementów członkowskich.
- Nie można utworzyć interfejsu bezpośrednio. Jego elementy członkowskie są implementowane przez dowolną klasę lub strukturę, która implementuje interfejs.
- Klasa lub struktura może implementować wiele interfejsów. Klasa może dziedziczyć klasy podstawowej, a także implementować jeden lub więcej interfejsów.

## <a name="BKMK_RelatedSections"></a>Sekcje pokrewne

- [Właściwości interfejsu](../classes-and-structs/interface-properties.md)  
- [Indeksatory w interfejsach](../indexers/indexers-in-interfaces.md)  
- [Implementowanie zdarzeń interfejsu](../events/how-to-implement-interface-events.md)
- [Klasy i struktury](../classes-and-structs/index.md)  
- [Dziedziczenie](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polimorfizm](../classes-and-structs/polymorphism.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Właściwości](../classes-and-structs/properties.md)  
- [Zdarzenia](../events/index.md)  
- [Indexers](../indexers/index.md) (Indeksatory)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
