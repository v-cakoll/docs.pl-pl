---
title: Interfejsy — C# Przewodnik programowania
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 99cbaa458e86c644a46eb62823f1854b3684c6c4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627750"
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)

Interfejs zawiera definicje dla grupy powiązanych funkcji, które muszą implementować [Klasa](../../language-reference/keywords/class.md) nieabstrakcyjna lub [Struktura](../../language-reference/builtin-types/struct.md) . Interfejs może definiować `static` metod, które muszą mieć implementację. Interfejs może zapewnić domyślną implementację dla wszystkich lub wszystkich zadeklarowanych elementów członkowskich wystąpienia. Interfejs nie może deklarować danych wystąpienia, takich jak pola, właściwości zaimplementowane lub zdarzenia podobne do właściwości.

Korzystając z interfejsów, można na przykład uwzględnić zachowanie z wielu źródeł w klasie. Ta funkcja jest ważna w C# przypadku, gdy język nie obsługuje wielokrotnego dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenie dla struktur, ponieważ nie może faktycznie dziedziczyć z innej struktury lub klasy.

Interfejs można zdefiniować za pomocą słowa kluczowego [Interface](../../language-reference/keywords/interface.md) , jak pokazano w poniższym przykładzie.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

Nazwa interfejsu musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md). Według Konwencji nazwy interfejsów zaczynają się od `I`wielkiej litery.

Każda klasa lub struktura implementująca interfejs <xref:System.IEquatable%601> musi zawierać definicję metody <xref:System.IEquatable%601.Equals%2A>, która pasuje do sygnatury określanej przez interfejs. W związku z tym można obliczyć na klasie, która implementuje `IEquatable<T>`, aby zawierała metodę `Equals`, z którą wystąpienie klasy może określić, czy jest ono równe innemu wystąpieniu tej samej klasy.

Definicja `IEquatable<T>` nie zapewnia implementacji dla `Equals`. Klasa lub struktura może implementować wiele interfejsów, ale Klasa może dziedziczyć tylko z pojedynczej klasy.

Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Interfejsy mogą zawierać metody instancji, właściwości, zdarzenia, indeksatory lub dowolną kombinację tych czterech typów elementów członkowskich. Interfejsy mogą zawierać statyczne konstruktory, pola, stałe lub operatory. Aby uzyskać linki do przykładów, zobacz sekcję [pokrewne](./index.md#BKMK_RelatedSections). Interfejs nie może zawierać pól wystąpień, konstruktorów wystąpień ani finalizatorów. Elementy członkowskie interfejsu są domyślnie publiczne.

Aby zaimplementować element członkowski interfejsu, odpowiadający mu element członkowski klasy implementującej musi być publiczny, niestatyczny i mieć taką samą nazwę i podpis jak element członkowski interfejsu.

Gdy Klasa lub struktura implementuje interfejs, Klasa lub struktura musi dostarczyć implementację dla wszystkich elementów członkowskich zadeklarowanych przez interfejs, ale nie udostępnia domyślnej implementacji dla programu. Jeśli jednak Klasa bazowa implementuje interfejs, każda klasa, która jest pochodną klasy bazowej, dziedziczy tę implementację.

W poniższym przykładzie przedstawiono implementację interfejsu <xref:System.IEquatable%601>. Klasa implementująca, `Car`, musi dostarczyć implementację metody <xref:System.IEquatable%601.Equals%2A>.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Właściwości i indeksatory klasy mogą definiować dodatkowe metody dostępu do właściwości lub indeksatora zdefiniowanego w interfejsie. Na przykład interfejs może deklarować właściwość, która ma metodę dostępu [Get](../../language-reference/keywords/get.md) . Klasa implementująca interfejs może zadeklarować tę samą właściwość z elementem dostępu `get` i [Set](../../language-reference/keywords/set.md) . Jeśli jednak właściwość lub indeksator używa jawnej implementacji, metody dostępu muszą być zgodne. Aby uzyskać więcej informacji na temat implementacji jawnej, zobacz [jawne implementacje interfejsu](explicit-interface-implementation.md) i [Właściwości interfejsu](../classes-and-structs/interface-properties.md).

Interfejsy mogą dziedziczyć z jednego lub większej liczby interfejsów. Interfejs pochodny dziedziczy elementy członkowskie z jego interfejsów podstawowych. Klasa implementująca interfejs pochodny musi implementować wszystkie elementy członkowskie w interfejsie pochodnym, w tym wszystkie elementy członkowskie interfejsów bazowych interfejsu pochodnego. Ta klasa może być niejawnie konwertowana na interfejs pochodny lub w dowolnym z jego interfejsów podstawowych. Klasa może zawierać wiele razy interfejs za pomocą klas bazowych, które dziedziczy lub przez interfejsy, które dziedziczy inne interfejsy. Jednak Klasa może zapewnić implementację interfejsu tylko jeden raz i tylko wtedy, gdy Klasa deklaruje interfejs jako część definicji klasy (`class ClassName : InterfaceName`). Jeśli interfejs jest dziedziczony, ponieważ dziedziczy Klasa bazowa implementująca interfejs, Klasa bazowa zapewnia implementację elementów członkowskich interfejsu. Jednak Klasa pochodna może zaimplementować wszystkie elementy członkowskie interfejsu wirtualnego zamiast korzystać z dziedziczonej implementacji. Gdy interfejsy deklarują domyślną implementację metody, każda klasa implementująca ten interfejs dziedziczy tę implementację. Implementacje zdefiniowane w interfejsach są wirtualne, a Klasa implementująca może przesłonić tę implementację.

Klasa bazowa może również implementować składowe interfejsu za pomocą wirtualnych elementów członkowskich. W takim przypadku Klasa pochodna może zmienić zachowanie interfejsu przez zastąpienie wirtualnych elementów członkowskich. Aby uzyskać więcej informacji na temat wirtualnych elementów członkowskich, zobacz [polimorfizm](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Podsumowanie interfejsów

Interfejs ma następujące właściwości:

- Interfejs jest zwykle podobny do abstrakcyjnej klasy bazowej z tylko abstrakcyjnymi elementami członkowskimi. Każda klasa lub struktura implementująca interfejs musi implementować wszystkie jego elementy członkowskie. Opcjonalnie interfejs może definiować domyślne implementacje dla niektórych lub wszystkich elementów członkowskich.
- Nie można bezpośrednio utworzyć wystąpienia interfejsu. Jego składowe są implementowane przez dowolną klasę lub strukturę, która implementuje interfejs.
- Klasa lub struktura może zaimplementować wiele interfejsów. Klasa może dziedziczyć klasę bazową, a także zaimplementować jeden lub więcej interfejsów.

## <a name="BKMK_RelatedSections"></a>Sekcje pokrewne

- [Właściwości interfejsu](../classes-and-structs/interface-properties.md)  
- [Indeksatory w interfejsach](../indexers/indexers-in-interfaces.md)  
- [Jak zaimplementować zdarzenia interfejsu](../events/how-to-implement-interface-events.md)
- [Klasy i struktury](../classes-and-structs/index.md)  
- [Dziedziczenie](../classes-and-structs/inheritance.md)  
- [Metody](../classes-and-structs/methods.md)  
- [Polimorfizm](../classes-and-structs/polymorphism.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Właściwości](../classes-and-structs/properties.md)  
- [Zdarzenia](../events/index.md)  
- [Indexers](../indexers/index.md) (Indeksatory)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Dziedziczenie](../classes-and-structs/inheritance.md)
- [Nazwy identyfikatorów](../inside-a-program/identifier-names.md)
