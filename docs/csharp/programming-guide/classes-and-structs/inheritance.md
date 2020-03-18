---
title: Dziedziczenie — przewodnik programowania Języka C#
ms.date: 02/07/2020
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 448b1695a4afc50f4afa20383e5fda280b9f12e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626662"
---
# <a name="inheritance-c-programming-guide"></a>Dziedziczenie (Przewodnik programowania w języku C#)

Dziedziczenie, wraz z hermetyzacją i polimorfizmem, jest jedną z trzech podstawowych cech programowania obiektowego. Dziedziczenie umożliwia tworzenie nowych klas, które ponownie używać, rozszerzać i modyfikować zachowanie zdefiniowane w innych klasach. Klasa, której elementy członkowskie są dziedziczone jest nazywany *klasy podstawowej*, a klasa, która dziedziczy te elementy członkowskie jest *wywoływana klasy pochodnej*. Klasa pochodna może mieć tylko jedną bezpośrednią klasę podstawową. Dziedziczenie jest jednak przechodnie. Jeśli `ClassC` pochodzi z `ClassB`, `ClassB` i pochodzi `ClassA` `ClassC` z , dziedziczy członków zadeklarowanych w `ClassB` i `ClassA`.

> [!NOTE]
> Struktury nie obsługują dziedziczenia, ale mogą implementować interfejsy. Aby uzyskać więcej informacji, zobacz [Interfejsy](../interfaces/index.md).

Koncepcyjnie klasa pochodna jest specjalizacją klasy podstawowej. Na przykład jeśli masz klasę `Animal`podstawową, może mieć jedną `Mammal` klasę pochodną, która `Reptile`ma nazwę i inną klasę pochodną, która ma nazwę . A `Mammal` jest `Animal`, `Reptile` a `Animal`a jest , ale każda klasa pochodna reprezentuje różne specjalizacje klasy podstawowej.

Deklaracje interfejsu może zdefiniować domyślną implementację dla swoich członków. Implementacje te są dziedziczone przez interfejsy pochodne i przez klasy, które implementują te interfejsy. Aby uzyskać więcej informacji na temat domyślnych metod interfejsu, zobacz artykuł na [temat interfejsów](../../language-reference/keywords/interface.md) w sekcji odwołania do języka.

Po zdefiniowaniu klasy pochodzi ć z innej klasy, klasa pochodna niejawnie zyskuje wszystkie elementy członkowskie klasy podstawowej, z wyjątkiem jego konstruktorów i finalizatorów. Klasa pochodna ponownie używa kodu w klasie podstawowej bez konieczności ponownego zaimplementowania go. Można dodać więcej elementów członkowskich w klasie pochodnej. Klasa pochodna rozszerza funkcjonalność klasy podstawowej.

Na poniższej ilustracji przedstawiono klasę, `WorkItem` która reprezentuje element pracy w niektórych procesów biznesowych. Podobnie jak wszystkie klasy, <xref:System.Object?displayProperty=nameWithType> pochodzi z i dziedziczy wszystkie jego metody. `WorkItem`dodaje pięciu własnych członków. Te elementy członkowskie obejmują konstruktora, ponieważ konstruktory nie są dziedziczone. Klasa `ChangeRequest` dziedziczy i `WorkItem` reprezentuje określony rodzaj elementu pracy. `ChangeRequest`dodaje dwa kolejne elementy członkowskie do `WorkItem` elementów <xref:System.Object>członkowskich, które dziedziczy z i z . Musi dodać własny konstruktor, `originalItemID`a także dodaje . Właściwość `originalItemID` umożliwia `ChangeRequest` wystąpienie, które mają `WorkItem` być skojarzone z oryginałem, do którego ma zastosowanie żądanie zmiany.

![Diagram przedstawiający dziedziczenie klasy](./media/inheritance/class-inheritance-diagram.png)

W poniższym przykładzie pokazano, jak relacje klas przedstawione na poprzedniej ilustracji są wyrażone w języku C#. W przykładzie pokazano `WorkItem` również, <xref:System.Object.ToString%2A?displayProperty=nameWithType>jak zastępuje `ChangeRequest` metodę wirtualną `WorkItem` i jak klasa dziedziczy implementację metody. Pierwszy blok definiuje klasy:

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Ten następny blok pokazuje, jak używać klas podstawowych i pochodnych:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualne

Gdy klasa podstawowa deklaruje [`virtual`](../../language-reference/keywords/virtual.md)metodę jako , [`override`](../../language-reference/keywords/override.md) klasa pochodna może metody z własną implementacją. Jeśli klasa podstawowa deklaruje [`abstract`](../../language-reference/keywords/abstract.md)element członkowski jako , ta metoda musi zostać zastąpiona w dowolnej klasie nieabstrakcyjnej, która bezpośrednio dziedziczy z tej klasy. Jeśli klasa pochodna jest sama abstrakcyjna, dziedziczy abstrakcyjne elementy członkowskie bez ich implementowania. Abstrakcyjne i wirtualne elementy członkowskie są podstawą polimorfizmu, który jest drugą podstawową cechą programowania obiektowego. Aby uzyskać więcej informacji, zobacz [Polimorfizm](./polymorphism.md).

## <a name="abstract-base-classes"></a>Abstrakcyjne klasy podstawowe

Można zadeklarować klasę jako [abstrakcyjną,](../../language-reference/keywords/abstract.md) jeśli chcesz zapobiec bezpośredniemu wystąpieniu przy użyciu [nowego](../../language-reference/operators/new-operator.md) operatora. Klasa abstrakcyjna może służyć tylko wtedy, gdy nowa klasa pochodzi z niego. Klasa abstrakcyjna może zawierać jeden lub więcej podpisów metody, które same są zadeklarowane jako abstrakcyjne. Podpisy te określają parametry i wartość zwracaną, ale nie mają implementacji (treść metody). Klasa abstrakcyjna nie musi zawierać abstrakcyjnych elementów członkowskich; jednak jeśli klasa zawiera abstrakcyjny element członkowski, sama klasa musi być zadeklarowana jako abstrakcyjna. Klasy pochodne, które nie są abstrakcyjne same musi zapewnić implementację dla wszelkich metod abstrakcyjnych z abstrakcyjnej klasy podstawowej. Aby uzyskać więcej informacji, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Członkowie klasy](abstract-and-sealed-classes-and-class-members.md).

## <a name="interfaces"></a>Interfejsy

*Interfejs* jest typem odwołania, który definiuje zestaw elementów członkowskich. Wszystkie klasy i struktury, które implementują ten interfejs musi implementować ten zestaw elementów członkowskich. Interfejs może zdefiniować domyślną implementację dla dowolnego lub wszystkich z tych elementów członkowskich. Klasa może zaimplementować wiele interfejsów, mimo że może pochodzić tylko z jednej bezpośredniej klasy podstawowej.

Interfejsy są używane do definiowania określonych możliwości dla klas, które niekoniecznie mają relację "jest". Na przykład <xref:System.IEquatable%601?displayProperty=nameWithType> interfejs może być zaimplementowany przez dowolną klasę lub strukturę, aby ustalić, czy dwa obiekty typu są równoważne (jednak typ definiuje równoważność). <xref:System.IEquatable%601>nie oznacza tego samego rodzaju relacji "jest" który istnieje między klasą podstawową a `Mammal` klasą pochodną (na przykład a jest). `Animal` Aby uzyskać więcej informacji, zobacz [Interfejsy](../interfaces/index.md).

## <a name="preventing-further-derivation"></a>Zapobieganie dalszemu wyprowadzaniu  

Klasa może uniemożliwić innym klasom dziedziczenie z niego lub od dowolnego z [`sealed`](../../language-reference/keywords/sealed.md)jej członków, deklarując siebie lub członka jako . Aby uzyskać więcej informacji, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Członkowie klasy](./abstract-and-sealed-classes-and-class-members.md).

## <a name="derived-class-hiding-of-base-class-members"></a>Ukrywanie klasy pochodnej elementów członkowskich klasy podstawowej  

Klasa pochodna może ukryć członków klasy podstawowej, deklarując członków o tej samej nazwie i podpisie. Modyfikator [`new`](../../language-reference/keywords/new-modifier.md) może służyć do jawnie wskazać, że element członkowski nie jest przeznaczony do zastąpienia podstawowego elementu członkowskiego. Użycie nie [`new`](../../language-reference/keywords/new-modifier.md) jest wymagane, ale ostrzeżenie kompilatora [`new`](../../language-reference/keywords/new-modifier.md) zostanie wygenerowany, jeśli nie jest używany. Aby uzyskać więcej informacji, zobacz [Przechowywanie wersji za pomocą słów kluczowych zastępowania i nowych](./versioning-with-the-override-and-new-keywords.md) oraz wiedza o [tym, kiedy należy użyć zastępowania i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Klasa](../../language-reference/keywords/class.md)
