---
title: Interfejsy - Przewodnik programowania języka C#
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 5e39279183f7e3745c9373df246d14d69d5ff99b
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805901"
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)

Interfejs zawiera definicje dla grupy powiązanych funkcji, które klasa nieabstrakcjowa lub [struktura](../../language-reference/builtin-types/struct.md) musi zaimplementować. [class](../../language-reference/keywords/class.md) Interfejs może `static` definiować metody, które muszą mieć implementację. Począwszy od języka C# 8.0, interfejs może zdefiniować domyślną implementację dla elementów członkowskich. Interfejs nie może deklarować danych wystąpienia, takich jak pola, właściwości automatycznie implementowane lub zdarzenia podobne do właściwości.

Za pomocą interfejsów, można na przykład uwzględnić zachowanie z wielu źródeł w klasie. Ta możliwość jest ważne w języku C#, ponieważ język nie obsługuje wielu dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenie dla struktur, ponieważ nie można faktycznie dziedziczyć z innej struktury lub klasy.

Definiujesz interfejs przy użyciu słowa kluczowego [interfejsu,](../../language-reference/keywords/interface.md) jak pokazano w poniższym przykładzie.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Nazwa interfejsu musi być prawidłową [nazwą identyfikatora](../inside-a-program/identifier-names.md)Języka C#. Zgodnie z konwencją nazwy `I`interfejsów zaczynają się od kapitału .

Każda klasa lub struktura, <xref:System.IEquatable%601> która implementuje interfejs <xref:System.IEquatable%601.Equals%2A> musi zawierać definicję metody, która pasuje do podpisu, który określa interfejs. W rezultacie można liczyć na klasę, `IEquatable<T>` która implementuje zawierać `Equals` metodę, za pomocą której wystąpienie klasy można określić, czy jest równa innym wystąpieniu tej samej klasy.

Definicja `IEquatable<T>` nie zapewnia implementacji `Equals`dla . Klasa lub struktura można zaimplementować wiele interfejsów, ale klasa może dziedziczyć tylko z jednej klasy.

Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [Abstrakcyjne i zapieczętowane klasy i członkowie klasy](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Interfejsy mogą zawierać metody wystąpienia, właściwości, zdarzenia, indeksatory lub dowolną kombinację tych czterech typów elementów członkowskich. Interfejsy mogą zawierać statyczne konstruktory, pola, stałe lub operatory. Aby uzyskać łącza do przykładów, zobacz [Sekcje pokrewne](./index.md#BKMK_RelatedSections). Interfejs nie może zawierać pól wystąpień, konstruktorów wystąpień ani finalizatorów. Członkowie interfejsu są domyślnie publiczne.

Aby zaimplementować element członkowski interfejsu, odpowiedni element członkowski klasy implementującej musi być publiczny, niestatyczny i mieć taką samą nazwę i podpis jak element członkowski interfejsu.

Gdy klasa lub struktura implementuje interfejs, klasa lub struktura musi zapewnić implementację dla wszystkich elementów członkowskich, które interfejs deklaruje, ale nie zapewnia domyślnej implementacji. Jednak jeśli klasa podstawowa implementuje interfejs, każda klasa, która pochodzi z klasy podstawowej dziedziczy tej implementacji.

W poniższym przykładzie <xref:System.IEquatable%601> przedstawiono implementację interfejsu. Klasa implementująca, `Car`, musi zapewnić <xref:System.IEquatable%601.Equals%2A> implementację metody.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Właściwości i indeksatory klasy można zdefiniować dodatkowe akcesory dla właściwości lub indeksatora, który jest zdefiniowany w interfejsie. Na przykład interfejs może zadeklarować właściwość, która ma [get](../../language-reference/keywords/get.md) akcesor. Klasa, która implementuje interfejs można zadeklarować `get` tę samą właściwość z akcesorem i [zestaw.](../../language-reference/keywords/set.md) Jednak jeśli właściwość lub indeksator używa jawne implementacji, akcesory muszą być zgodne. Aby uzyskać więcej informacji na temat jawnego implementacji, zobacz [Jawna implementacja interfejsu](explicit-interface-implementation.md) i [właściwości interfejsu](../classes-and-structs/interface-properties.md).

Interfejsy mogą dziedziczyć z jednego lub więcej interfejsów. Interfejs pochodny dziedziczy elementy członkowskie z interfejsów podstawowych. Klasa, która implementuje interfejs pochodny musi implementować wszystkie elementy członkowskie w interfejsie pochodnym, w tym wszystkich elementów członkowskich interfejsów podstawowych interfejsu pochodnego. Ta klasa może być niejawnie konwertowane do interfejsu pochodnego lub dowolnego z jego interfejsów podstawowych. Klasa może zawierać interfejs wiele razy za pośrednictwem klas podstawowych, które dziedziczy lub za pośrednictwem interfejsów, które dziedziczą inne interfejsy. Jednak klasa może zapewnić implementację interfejsu tylko jeden raz i tylko wtedy, gdy klasa deklaruje`class ClassName : InterfaceName`interfejs jako część definicji klasy ( ). Jeśli interfejs jest dziedziczony, ponieważ odziedziczył klasę podstawową, która implementuje interfejs, klasa podstawowa zapewnia implementację elementów członkowskich interfejsu. Jednak klasa pochodna może ponownie wdrożyć żadnych elementów członkowskich interfejsu wirtualnego zamiast przy użyciu implementacji dziedziczonej. Gdy interfejsy deklarują domyślną implementację metody, każda klasa implementująca ten interfejs dziedziczy tę implementację. Implementacje zdefiniowane w interfejsach są wirtualne i klasy implementującej może zastąpić tę implementację.

Klasa podstawowa może również implementować elementy członkowskie interfejsu przy użyciu elementów członkowskich wirtualnych. W takim przypadku klasa pochodna może zmienić zachowanie interfejsu, zastępując elementy członkowskie wirtualne. Aby uzyskać więcej informacji na temat wirtualnych członków, zobacz [Polymorphism](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Podsumowanie interfejsów

Interfejs ma następujące właściwości:

- Interfejs jest zazwyczaj jak abstrakcyjna klasa podstawowa z tylko abstrakcyjne elementy członkowskie. Każda klasa lub struktura, która implementuje interfejs musi implementować wszystkie jego elementów członkowskich. Opcjonalnie interfejs może definiować domyślne implementacje dla niektórych lub wszystkich jego elementów członkowskich.
- Nie można utworzyć wystąpienia interfejsu bezpośrednio. Jego elementy członkowskie są implementowane przez dowolną klasę lub strukturę, która implementuje interfejs.
- Klasa lub struktura można zaimplementować wiele interfejsów. Klasa może dziedziczyć klasę podstawową, a także implementować jeden lub więcej interfejsów.

## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a>Powiązane sekcje

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
- [Indexers (Indeksatory)](../indexers/index.md)  
  
## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
