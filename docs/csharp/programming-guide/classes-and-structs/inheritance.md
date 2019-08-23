---
title: Dziedziczenie C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
ms.openlocfilehash: 3211a4741eb56ad9e138a848e52fabbc1d3daaeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924470"
---
# <a name="inheritance-c-programming-guide"></a>Dziedziczenie (Przewodnik programowania w języku C#)

Dziedziczenie, wraz z hermetyzacją i polimorfizmem, jest jedną z trzech podstawowych cech programowania zorientowanego obiektowo. Dziedziczenie umożliwia tworzenie nowych klas, które będą używać, zwiększać i modyfikować zachowanie zdefiniowane w innych klasach. Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*. Klasa pochodna może mieć tylko jedną bezpośrednią klasę bazową. Dziedziczenie jest jednak przechodnie. Jeśli ClassC pochodzi z ClassB, a ClassB pochodzi od ClassA, ClassC dziedziczy składowe zadeklarowane w ClassB i ClassA.  
  
> [!NOTE]
> Struktury nie obsługują dziedziczenia, ale mogą implementować interfejsy. Więcej informacji znajdziesz w artykule [Interfejsy](../interfaces/index.md).  
  
 Koncepcyjnie Klasa pochodna jest specjalizacją klasy bazowej. Na przykład jeśli masz klasę `Animal`bazową, może istnieć jedna klasa pochodna o nazwie `Mammal` i innej klasie pochodnej o nazwie `Reptile`. A to a, `Reptile` i jest `Animal`, ale każda klasa pochodna reprezentuje różne specjalizacje klasy bazowej. `Mammal` `Animal`  
  
 Podczas definiowania klasy, która ma pochodzić z innej klasy, Klasa pochodna niejawnie uzyskuje wszystkie elementy członkowskie klasy bazowej, z wyjątkiem konstruktorów i finalizatorów. Klasa pochodna może w efekcie ponownie użyć kodu w klasie bazowej bez konieczności jego ponownego wdrożenia. W klasie pochodnej można dodać więcej elementów członkowskich. W ten sposób Klasa pochodna rozszerza funkcjonalność klasy bazowej.  
  
 Na poniższej ilustracji przedstawiono klasę `WorkItem` , która reprezentuje element pracy w pewnym procesie biznesowym. Podobnie jak w przypadku wszystkich klas, <xref:System.Object?displayProperty=nameWithType> pochodzi z i dziedziczy wszystkie metody. `WorkItem`dodaje pięciu członków. Należą do nich Konstruktor, ponieważ konstruktory nie są dziedziczone. Klasa `ChangeRequest` dziedziczy z `WorkItem` i reprezentuje konkretny rodzaj elementu pracy. `ChangeRequest`dodaje dwóch więcej członków do członków, z `WorkItem` <xref:System.Object>których dziedziczy. Musi dodać własnego konstruktora, a także dodaje `originalItemID`. Umożliwia skojarzenie wystąpienia z oryginałem `WorkItem` , do którego ma zastosowanie żądanie zmiany. `ChangeRequest` `originalItemID`  
  
 ![Diagram przedstawiający dziedziczenie klas](./media/inheritance/class-inheritance-diagram.png)  
  
 Poniższy przykład pokazuje, jak relacje klas pokazane na poprzedniej ilustracji są wyrażone w C#. W przykładzie pokazano również, `WorkItem` jak zastępuje metodę <xref:System.Object.ToString%2A?displayProperty=nameWithType>wirtualną oraz `WorkItem` sposób, w `ChangeRequest` jaki Klasa dziedziczy implementację metody.  
  
 [!code-csharp[csProgGuideInheritance#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#49)]  
  
## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualne  
 Gdy klasa bazowa deklaruje metodę jako [wirtualną](../../language-reference/keywords/virtual.md), Klasa pochodna może [zastąpić](../../language-reference/keywords/override.md) metodę własną implementacją. Jeśli klasa bazowa deklaruje element członkowski jako [abstrakcyjny](../../language-reference/keywords/abstract.md), ta metoda musi zostać zastąpiona w dowolnej klasie nieabstrakcyjnej, która bezpośrednio dziedziczy z tej klasy. Jeśli klasa pochodna jest abstrakcyjna, dziedziczy abstrakcyjne elementy członkowskie bez wdrażania ich. Abstrakcyjne i wirtualne elementy członkowskie są podstawą dla polimorfizmu, który jest drugą podstawową cechą programowania zorientowanego obiektowo. Aby uzyskać więcej informacji, zobacz [polimorfizm](./polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Abstrakcyjne klasy podstawowe  
 Można zadeklarować klasę jako [abstrakcyjną](../../language-reference/keywords/abstract.md) , jeśli chcesz zapobiec bezpośredniemu tworzeniu wystąpienia przy użyciu operatora [New](../../language-reference/operators/new-operator.md) . Jeśli to zrobisz, Klasa może być używana tylko wtedy, gdy nowa klasa pochodzi od niej. Klasa abstrakcyjna może zawierać co najmniej jeden podpis metody, który sam jest zadeklarowany jako abstrakcyjny. Te podpisy określają parametry i wartość zwracaną, ale nie mają implementacji (treść metody). Klasa abstrakcyjna nie musi zawierać abstrakcyjnych elementów członkowskich; Jeśli jednak Klasa zawiera abstrakcyjną składową, sama klasa musi być zadeklarowana jako abstract. Klasy pochodne, które nie są abstrakcyjne, muszą dostarczać implementację dla wszelkich metod abstrakcyjnych z abstrakcyjnej klasy bazowej. Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](./abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Interfejsy  
 *Interfejs* jest typem referencyjnym, który jest nieco podobny do abstrakcyjnej klasy bazowej, która składa się tylko z abstrakcyjnych elementów członkowskich. Gdy klasa implementuje interfejs, musi dostarczyć implementację dla wszystkich elementów członkowskich interfejsu. Klasa może zaimplementować wiele interfejsów, chociaż może dziedziczyć tylko z pojedynczej bezpośredniej klasy bazowej.  
  
 Interfejsy służą do definiowania określonych funkcji dla klas, które nie muszą mieć relacji "is". Na przykład <xref:System.IEquatable%601?displayProperty=nameWithType> interfejs może być zaimplementowany przez dowolną klasę lub strukturę, która musi umożliwić kod klienta, aby określić, czy dwa obiekty typu są równoważne (jednak typ definiuje równoważność). <xref:System.IEquatable%601>nie implikuje tego samego rodzaju relacji "is", która istnieje między klasą bazową a klasą pochodną (na przykład a `Mammal` `Animal`). Więcej informacji znajdziesz w artykule [Interfejsy](../interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Zapobieganie dalszemu wyprowadzaniu  
 Klasa może uniemożliwić innym klasom dziedziczenie z niego lub z dowolnego elementu członkowskiego, deklarując siebie lub element członkowski jako [zapieczętowany](../../language-reference/keywords/sealed.md). Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](./abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Ukrywanie klasy pochodnej elementów członkowskich klasy bazowej  
 Klasa pochodna może ukryć składowe klasy bazowej, deklarując składowe o tej samej nazwie i podpisie. Przy użyciu [nowego](../../language-reference/keywords/new-modifier.md) modyfikatora można jawnie wskazać, że element członkowski nie jest przesłonięciem podstawowego elementu członkowskiego. Korzystanie z [nowych](../../language-reference/keywords/new-modifier.md) nie jest wymagane, ale jeśli [nowe](../../language-reference/keywords/new-modifier.md) nie zostanie użyte, zostanie wygenerowane Ostrzeżenie kompilatora. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji z zastępowaniem i nowymi słowami kluczowymi](./versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
