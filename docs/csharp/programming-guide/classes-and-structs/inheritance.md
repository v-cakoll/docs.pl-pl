---
title: Dziedziczenie C# — Przewodnik programowania
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
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626662"
---
# <a name="inheritance-c-programming-guide"></a>Dziedziczenie (Przewodnik programowania w języku C#)

Dziedziczenie, wraz z hermetyzacją i polimorfizmem, jest jedną z trzech podstawowych cech programowania zorientowanego obiektowo. Dziedziczenie umożliwia tworzenie nowych klas, które będą ponownie używać, zwiększać i modyfikować zachowanie zdefiniowane w innych klasach. Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*. Klasa pochodna może mieć tylko jedną bezpośrednią klasę bazową. Dziedziczenie jest jednak przechodnie. Jeśli `ClassC` pochodzi od `ClassB`, a `ClassB` pochodzi od `ClassA`, `ClassC` dziedziczy członków zadeklarowanych w `ClassB` i `ClassA`.

> [!NOTE]
> Struktury nie obsługują dziedziczenia, ale mogą implementować interfejsy. Aby uzyskać więcej informacji, zobacz [interfejsy](../interfaces/index.md).

Koncepcyjnie Klasa pochodna jest specjalizacją klasy bazowej. Na przykład jeśli masz klasę bazową `Animal`, może istnieć jedna klasa pochodna o nazwie `Mammal` i inna Klasa pochodna o nazwie `Reptile`. `Mammal` jest `Animal`, a `Reptile` jest `Animal`, ale każda klasa pochodna reprezentuje różne specjalizacje klasy bazowej.

Deklaracje interfejsu mogą definiować domyślną implementację jej elementów członkowskich. Te implementacje są dziedziczone przez interfejsy pochodne i klasy, które implementują te interfejsy. Aby uzyskać więcej informacji na temat domyślnych metod interfejsu, zobacz artykuł dotyczący [interfejsów](../../language-reference/keywords/interface.md) w sekcji Dokumentacja języka.

Podczas definiowania klasy, która ma pochodzić z innej klasy, Klasa pochodna niejawnie uzyskuje wszystkie elementy członkowskie klasy bazowej, z wyjątkiem konstruktorów i finalizatorów. Klasa pochodna ponownie używa kodu w klasie bazowej bez konieczności jego ponownego wdrożenia. Można dodać więcej elementów członkowskich w klasie pochodnej. Klasa pochodna rozszerza funkcjonalność klasy bazowej.

Na poniższej ilustracji przedstawiono klasę `WorkItem`, która reprezentuje element pracy w pewnym procesie biznesowym. Podobnie jak w przypadku wszystkich klas, pochodzi ona z <xref:System.Object?displayProperty=nameWithType> i dziedziczy wszystkie jej metody. `WorkItem` dodaje pięciu członków. Te składowe zawierają konstruktora, ponieważ konstruktory nie są dziedziczone. Klasa `ChangeRequest` dziedziczy po `WorkItem` i reprezentuje konkretny rodzaj elementu pracy. `ChangeRequest` dodaje dwóch więcej członków do elementów członkowskich, które dziedziczy z `WorkItem` i <xref:System.Object>. Musi dodać własnego konstruktora i dodaje `originalItemID`. Właściwość `originalItemID` umożliwia skojarzenie wystąpienia `ChangeRequest` z oryginalnym `WorkItem`, do którego ma zastosowanie żądanie zmiany.

![Diagram przedstawiający dziedziczenie klas](./media/inheritance/class-inheritance-diagram.png)

Poniższy przykład pokazuje, jak relacje klas pokazane na poprzedniej ilustracji są wyrażone w C#. W przykładzie pokazano również, jak `WorkItem` przesłania metodę wirtualną <xref:System.Object.ToString%2A?displayProperty=nameWithType>i jak Klasa `ChangeRequest` dziedziczy implementację `WorkItem` metody. Pierwszy blok definiuje klasy:

[!code-csharp[DefineClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#Classes)]

Ten następny blok pokazuje, jak używać klas podstawowych i pochodnych:

[!code-csharp[UseClasses](~/samples/snippets/csharp/objectoriented/inheritance.cs#UseClasses)]

## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualne

Gdy klasa bazowa deklaruje metodę jako [`virtual`](../../language-reference/keywords/virtual.md), Klasa pochodna może [`override`](../../language-reference/keywords/override.md) metodę z własną implementacją. Jeśli klasa bazowa deklaruje element członkowski jako [`abstract`](../../language-reference/keywords/abstract.md), ta metoda musi zostać zastąpiona w dowolnej klasie nieabstrakcyjnej, która bezpośrednio dziedziczy z tej klasy. Jeśli klasa pochodna jest abstrakcyjna, dziedziczy abstrakcyjne elementy członkowskie bez wdrażania ich. Abstrakcyjne i wirtualne elementy członkowskie są podstawą dla polimorfizmu, który jest drugą podstawową cechą programowania zorientowanego obiektowo. Aby uzyskać więcej informacji, zobacz [polimorfizm](./polymorphism.md).

## <a name="abstract-base-classes"></a>Abstrakcyjne klasy podstawowe

Można zadeklarować klasę jako [abstrakcyjną](../../language-reference/keywords/abstract.md) , jeśli chcesz zapobiec bezpośredniemu tworzeniu wystąpienia przy użyciu operatora [New](../../language-reference/operators/new-operator.md) . Klasa abstrakcyjna może być używana tylko wtedy, gdy tworzona jest nowa klasa. Klasa abstrakcyjna może zawierać co najmniej jeden podpis metody, który sam jest zadeklarowany jako abstrakcyjny. Te podpisy określają parametry i wartość zwracaną, ale nie mają implementacji (treść metody). Klasa abstrakcyjna nie musi zawierać abstrakcyjnych elementów członkowskich; Jeśli jednak Klasa zawiera abstrakcyjną składową, sama klasa musi być zadeklarowana jako abstract. Klasy pochodne, które nie są abstrakcyjne, muszą dostarczać implementację dla wszelkich metod abstrakcyjnych z abstrakcyjnej klasy bazowej. Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](abstract-and-sealed-classes-and-class-members.md).

## <a name="interfaces"></a>Interfejsy

*Interfejs* jest typem referencyjnym, który definiuje zestaw elementów członkowskich. Wszystkie klasy i struktury implementujące ten interfejs muszą implementować ten zestaw elementów członkowskich. Interfejs może definiować domyślną implementację dla każdego lub wszystkich tych elementów członkowskich. Klasa może zaimplementować wiele interfejsów, chociaż może dziedziczyć tylko z pojedynczej bezpośredniej klasy bazowej.

Interfejsy służą do definiowania określonych funkcji dla klas, które nie muszą mieć relacji "is". Na przykład interfejs <xref:System.IEquatable%601?displayProperty=nameWithType> może być zaimplementowany przez dowolną klasę lub strukturę, aby określić, czy dwa obiekty typu są równoważne (jednak typ definiuje równoważność). <xref:System.IEquatable%601> nie implikuje tego samego rodzaju relacji "is", która istnieje między klasą bazową a klasą pochodną (na przykład `Mammal` jest `Animal`). Aby uzyskać więcej informacji, zobacz [interfejsy](../interfaces/index.md).

## <a name="preventing-further-derivation"></a>Zapobieganie dalszemu wyprowadzaniu  

Klasa może uniemożliwić innym klasom dziedziczenie z niego lub z dowolnego elementu członkowskiego, deklarując sam lub element członkowski jako [`sealed`](../../language-reference/keywords/sealed.md). Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](./abstract-and-sealed-classes-and-class-members.md).

## <a name="derived-class-hiding-of-base-class-members"></a>Ukrywanie klasy pochodnej elementów członkowskich klasy bazowej  

Klasa pochodna może ukryć składowe klasy bazowej, deklarując składowe o tej samej nazwie i podpisie. Modyfikator [`new`](../../language-reference/keywords/new-modifier.md) może służyć do jawnego wskazywania, że element członkowski nie jest celem przesłonięcia podstawowego elementu członkowskiego. Użycie [`new`](../../language-reference/keywords/new-modifier.md) nie jest wymagane, ale zostanie wygenerowane Ostrzeżenie kompilatora, jeśli nie [`new`](../../language-reference/keywords/new-modifier.md) nie jest używany. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji z zastępowaniem i nowymi słowami kluczowymi](./versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [class](../../language-reference/keywords/class.md)
