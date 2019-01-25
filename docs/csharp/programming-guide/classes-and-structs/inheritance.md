---
title: Dziedziczenie — C# przewodnik programowania
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
ms.openlocfilehash: 4ba5c28f6d4842846c55f47b3b40628ec57c9702
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607020"
---
# <a name="inheritance-c-programming-guide"></a>Dziedziczenie (Przewodnik programowania w języku C#)

Dziedziczenie, wraz z hermetyzacji i polimorfizmu, jest jednym z trzech właściwości głównej programowanie zorientowane obiektowo. Dziedziczenie umożliwia utworzenie nowej klasy, które ponownie używane, rozszerzanie i zmodyfikować zachowanie, która jest zdefiniowana w innych klas. Nosi nazwę klasy, której członkowie są dziedziczeni *klasy bazowej*, a klasa, która dziedziczy tych członków, jest nazywana *klasy pochodnej*. Klasa pochodna może mieć tylko jedną bezpośrednią klasą bazową. Dziedziczenie jest jednak przechodnie. Jeśli klasa c jest wyprowadzany z ClassB, a ClassB jest tworzony na podstawie ClassA, ClassC dziedziczy elementów członkowskich zadeklarowanych w ClassB i ClassA.  
  
> [!NOTE]
>  Struktury nie obsługują dziedziczenia, ale mogące implementować interfejsy. Więcej informacji znajdziesz w artykule [Interfejsy](../../../csharp/programming-guide/interfaces/index.md).  
  
 Model klasy pochodnej jest specjalizacją klasy bazowej. Na przykład, jeśli masz klasę bazową `Animal`, Niewykluczone, że jedna klasa pochodna, która nosi nazwę `Mammal` i innej klasy pochodnej, o nazwie `Reptile`. A `Mammal` jest `Animal`, a `Reptile` jest `Animal`, ale każda klasa pochodna reprezentuje różnych specjalizacji klasy bazowej.  
  
 Podczas definiowania klasy pochodzi z innej klasy pochodnej klasy niejawnie uzyskuje wszystkie elementy członkowskie klasy bazowej, z wyjątkiem jego konstruktorów i finalizatory. Kod w klasie bazowej dzięki temu można wykorzystywać klasy pochodnej bez konieczności jej ponownego wdrożenia. W klasie pochodnej można dodać więcej elementów członkowskich. W ten sposób Klasa pochodna rozszerza funkcjonalność klasy bazowej.  
  
 Poniższa ilustracja przedstawia klasy `WorkItem` reprezentujący element pracy w niektórych procesów biznesowych. Podobnie jak wszystkie klasy pochodzi z <xref:System.Object?displayProperty=nameWithType> i dziedziczy jej metody. `WorkItem` dodaje pięciu członków własne. Obejmują one konstruktora, ponieważ konstruktory nie są dziedziczone. Klasa `ChangeRequest` dziedziczy `WorkItem` i reprezentuje określonego typu elementu roboczego. `ChangeRequest` dodaje dwa więcej elementów członkowskich do elementów członkowskich, które dziedziczy `WorkItem` i <xref:System.Object>. Jego należy dodać własną konstruktora, i dodaje także `originalItemID`. Właściwość `originalItemID` umożliwia `ChangeRequest` wystąpienia, które mają być skojarzone z oryginalnym `WorkItem` którego dotyczy żądanie zmiany.  
  
 ![Dziedziczenie klas](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class_Inheritance")  
Dziedziczenie klas  
  
 Poniższy przykład pokazuje, jak pokazano na poprzedniej ilustracji relacje klas są wyrażone w języku C#. W przykładzie przedstawiono również sposób `WorkItem` zastępuje metodę wirtualną <xref:System.Object.ToString%2A?displayProperty=nameWithType>oraz sposób, w jaki `ChangeRequest` klasa dziedziczy `WorkItem` implementacji metody.  
  
 [!code-csharp[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualnych  
 Kiedy klasę bazową deklaruje metodę jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), klasa pochodna może [zastąpienia](../../../csharp/language-reference/keywords/override.md) metoda własną implementację. Jeśli klasa bazowa deklaruje element członkowski jako [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md), że metoda musi zostać zastąpiona w dowolnym nieabstrakcyjnej klasie dziedziczącej bezpośrednio z tej klasy. Jeśli klasa pochodna sama jest abstrakcyjna dziedziczy członków abstrakcyjnych bez ich wdrażania. Abstrakcyjna i wirtualnych elementów członkowskich stanowią podstawę polimorfizm, czyli podstawowy drugiego charakterystyka programowanie zorientowane obiektowo. Aby uzyskać więcej informacji, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Abstrakcyjnych klas bazowych  
 Można zadeklarować klasy jako [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md) Jeśli chcesz zapobiec bezpośredni wystąpienia przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe. Jeśli to zrobisz, klasa może służyć tylko wtedy, gdy nowa klasa pochodzi od niego. Klasa abstrakcyjna może zawierać jeden lub więcej podpisy metod, że same są deklarowane jako abstrakcyjne. Te podpisy określania parametrów i zwracają wartość, ale nie mają implementacji (treści metody). Klasa abstrakcyjna nie musi zawierać członkami abstrakcyjnymi; Jednak jeśli klasa zawiera abstrakcyjną składową, sama klasa musi być zadeklarowany jako abstrakcyjny. Klasy pochodne, które nie są abstrakcyjne samodzielnie zapewniają implementację dla dowolnej metody abstrakcyjne z abstrakcyjną klasę bazową. Aby uzyskać więcej informacji, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Interfejsy  
 *Interfejsu* jest typem referencyjnym, który przypomina nieco abstrakcyjną klasę bazową, która składa się z tylko członków abstrakcyjnych. Gdy klasa implementuje interfejs, musi zapewniać implementację, dla wszystkich członków interfejsu. Klasę można zaimplementować wiele interfejsów, mimo że może dziedziczyć tylko po jednej bezpośredniej klasie bazowej.  
  
 Interfejsy są używane do definiowania konkretne funkcje dla klas, które nie muszą być "to" relacji. Na przykład <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu może być implementowany przez dowolnej klasy lub struktury, która ma, aby włączyć kod klienta w celu ustalenia, czy dwa obiekty tego typu są równoważne (jednak typ definiuje równoważności). <xref:System.IEquatable%601> nie oznacza taki sam rodzaj "to" relacji istnieje między klasa bazowa i Klasa pochodna (na przykład `Mammal` jest `Animal`). Więcej informacji znajdziesz w artykule [Interfejsy](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Uniemożliwia dalsze tworzenie wartości pochodnych  
 Klasa może uniemożliwić dziedziczy z niego lub ze swoich elementów członkowskich, deklarując sam lub elementu członkowskiego jako innych klas [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md). Aby uzyskać więcej informacji, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Klasa pochodna ukrycie elementów członkowskich klasy podstawowej  
 Klasa pochodna można ukryć składowych klasy bazowej przez zadeklarowanie elementów członkowskich z taką samą nazwę i podpis. [Nowe](../../../csharp/language-reference/keywords/new.md) modyfikator może służyć do jawnie wskazywały elementu członkowskiego nie jest przeznaczony do zastąpienia podstawowego elementu członkowskiego. Korzystanie z [nowe](../../../csharp/language-reference/keywords/new.md) nie jest wymagane, ale ostrzeżenia kompilatora zostanie wygenerowany, jeśli [nowe](../../../csharp/language-reference/keywords/new.md) nie jest używany. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [, wiedząc, gdy użycie zastępowania i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
