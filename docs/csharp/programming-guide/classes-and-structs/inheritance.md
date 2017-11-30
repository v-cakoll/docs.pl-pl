---
title: "Dziedziczenie (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
caps.latest.revision: "38"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc3d448d311fe0a67839757fa43a209d92141214
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inheritance-c-programming-guide"></a>Dziedziczenie (Przewodnik programowania w języku C#)

Dziedziczenie, wraz z hermetyzacji i polimorfizm, jest jednym z trzech właściwości głównej programowanie zorientowane obiektowo. Dziedziczenie pozwala tworzyć nowe klasy, które ponownie używane, rozszerzać i zmodyfikować zachowanie, który jest zdefiniowany w innych klas. Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*, i nosi nazwę klasy, która dziedziczy tych członków *klasy*. Klasa pochodna może mieć tylko jeden bezpośredniej klasie podstawowej. Jednak dziedziczenia jest przechodnie. Jeśli klasa c jest pochodną ClassB i ClassB jest pochodną ClassA, klasa c dziedziczy zadeklarowany w ClassB i ClassA elementów członkowskich.  
  
> [!NOTE]
>  Struktury nie obsługują dziedziczenia, ale miały zaimplementowane interfejsy. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
 Klasa pochodna jest koncepcyjnie, specjalizacji klasy podstawowej. Na przykład, jeśli masz klasę podstawową `Animal`, może być jednej klasy pochodnej, o nazwie `Mammal` i innej klasy pochodnej, która jest o nazwie `Reptile`. A `Mammal` jest `Animal`, a `Reptile` jest `Animal`, ale każda klasa pochodna reprezentuje inną specjalizacji klasy podstawowej.  
  
 Po zdefiniowaniu klasy pochodzić z innej klasy pochodnej klasy niejawnie uzyskuje wszystkich elementów członkowskich klasy podstawowej, z wyjątkiem jej konstruktorów i finalizatory. Klasy pochodne mogą co ponowne użycie kodu w klasie podstawowej bez konieczności jej ponownego zdefiniowania. W klasie pochodnej możesz dodać więcej elementów członkowskich. W ten sposób klasy pochodnej, rozszerzający funkcje klasy podstawowej.  
  
 Na poniższej ilustracji przedstawiono klasy `WorkItem` reprezentujący element pracy w niektórych procesów biznesowych. Podobnie jak wszystkie klasy dziedziczy <xref:System.Object?displayProperty=nameWithType> i wszystkie jego metody dziedziczy. `WorkItem`dodaje pięciu członków własnych. Obejmują one konstruktora, ponieważ nie są dziedziczone przez konstruktorów. Klasa `ChangeRequest` dziedziczy `WorkItem` i reprezentuje określonego typu elementu roboczego. `ChangeRequest`dodaje dwa więcej elementów członkowskich do elementów członkowskich, które dziedziczy on z `WorkItem` i z <xref:System.Object>. Należy dodać własną konstruktora, a także dodaje `originalItemID`. Właściwość `originalItemID` umożliwia `ChangeRequest` wystąpienia, które mają być skojarzone z oryginalnym `WorkItem` którego dotyczy żądanie zmiany.  
  
 ![Dziedziczenie klas](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class_Inheritance")  
Dziedziczenie klas  
  
 W poniższym przykładzie pokazano, jak relacje klas przedstawiona na poprzedniej ilustracji są wyrażane w języku C#. Przykładzie przedstawiono również sposób `WorkItem` zastępuje metodę wirtualną <xref:System.Object.ToString%2A?displayProperty=nameWithType>i jak `ChangeRequest` klasa dziedziczy `WorkItem` implementacji metody.  
  
 [!code-csharp[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjna i wirtualna  
 Po klasie podstawowej deklaruje metody jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), można w klasie pochodnej [zastąpienia](../../../csharp/language-reference/keywords/override.md) metody z własną implementację. Jeśli klasą podstawową deklaruje elementu członkowskiego jako [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md), że metoda musi zostać zastąpiona w dowolnej klasy nieabstrakcyjnej, która bezpośrednio dziedziczy z klasy. Jeśli klasa pochodna jest abstrakcyjna, dziedziczy abstrakcyjne elementy członkowskie bez ich wdrożenie. Abstrakcyjnych i wirtualnych elementów członkowskich stanowią podstawę polimorfizm, która jest drugi głównej cech programowanie zorientowane obiektowo. Aby uzyskać więcej informacji, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Abstrakcyjnych klas podstawowych  
 Można zadeklarować klasy jako [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) Jeśli chcesz uniemożliwić bezpośrednie wystąpienia przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe. Jeśli to zrobisz, klasa może być używana tylko wtedy, gdy nowa klasa pochodzi od niego. Abstrakcyjna klasa może zawierać jeden lub więcej podpisów metoda tego same jest zadeklarowany jako abstrakcyjny. Te podpisy Określ parametry i zwracać wartość, ale nie implementacją (treści metody). Klasa abstrakcyjna nie musi zawierać abstrakcyjnych elementów członkowskich; Jednak jeśli klasa zawiera abstrakcyjny element członkowski, ta sama klasa musi być zadeklarowany jako abstrakcyjny. Klasy pochodne, które nie są abstrakcyjny się podać implementację dla dowolnej metody abstrakcyjne z abstrakcyjną klasę podstawową. Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Interfejsy  
 *Interfejsu* jest typem referencyjnym, który przypomina trochę abstrakcyjna klasa podstawowa, która składa się z tylko abstrakcyjne elementy członkowskie. Gdy klasa implementuje interfejs, musi zapewniać implementację, dla wszystkich członków interfejsu. Klasę można zaimplementować wiele interfejsów, nawet jeśli mogą dziedziczyć z tylko jednym bezpośredniej klasie podstawowej.  
  
 Interfejsy są używane do definiowania możliwości dla klas, które nie muszą być "to" relacji. Na przykład <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu może być zaimplementowany przez klasy lub struktury, aby włączyć kod klienta w celu ustalenia, czy dwa obiekty tego typu są równoważne (jednak typ definiuje równoważność). <xref:System.IEquatable%601>nie oznacza taki sam rodzaj "jest" relację między klasą bazową i Klasa pochodna (na przykład `Mammal` jest `Animal`). Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Uniemożliwia dalsze wyprowadzenia  
 Klasę można uniemożliwić dziedziczenie z niej, lub z dowolnego z jego elementów członkowskich przez zadeklarowanie siebie lub element członkowski jako innych klas [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md). Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Klasa pochodna ukrytych elementów członkowskich klasy podstawowej  
 Klasa pochodna można ukryć elementów członkowskich klasy podstawowej przez zadeklarowanie elementów członkowskich o tej samej nazwie i podpisie. [Nowe](../../../csharp/language-reference/keywords/new.md) modyfikatora można używać, aby jawnie wskazać, że element członkowski nie ma być przesłonięcie podstawowego elementu członkowskiego. Korzystanie z [nowe](../../../csharp/language-reference/keywords/new.md) nie jest wymagana, ale ostrzeżenie kompilatora zostanie wygenerowany, jeśli [nowe](../../../csharp/language-reference/keywords/new.md) nie jest używany. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedząc, gdy użycie zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [klasy](../../../csharp/language-reference/keywords/class.md)  
 [— Struktura](../../../csharp/language-reference/keywords/struct.md)
