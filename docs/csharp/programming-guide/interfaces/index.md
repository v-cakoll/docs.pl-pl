---
title: "Interfejsy (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f14d4bf48d117558a4019a8f016e194af27a9ebf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interfaces-c-programming-guide"></a>Interfejsy (Przewodnik programowania w języku C#)
Interfejs zawiera definicje dla grupy powiązane funkcje który [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) można zaimplementować.  
  
 Za pomocą interfejsów, na przykład można dołączyć zachowanie z wielu źródeł w klasie. Czy funkcja jest ważne w języku C#, ponieważ język nie obsługuje wielu dziedziczenia klas. Ponadto należy użyć interfejsu, jeśli chcesz symulować dziedziczenia struktur, ponieważ ich faktycznie nie może dziedziczyć z innego struktury lub klasy.  
  
 Możesz definiować za pomocą interfejsu [interfejsu](../../../csharp/language-reference/keywords/interface.md) — słowo kluczowe, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 Klasy lub struktury, która implementuje <xref:System.IEquatable%601> interfejs musi zawierać definicję <xref:System.IEquatable%601.Equals%2A> metodę, która odpowiada podpisie, który określa interfejs. W związku z tym można liczyć na klasę, która implementuje `IEquatable<T>` zawiera `Equals` metody, z którym wystąpienia klasy można określić, czy jest taki sam, jak inne wystąpienie tego samego rodzaju.  
  
 Definicja `IEquatable<T>` nie dostarcza implementację `Equals`. Interfejs definiuje tylko sygnaturę. W ten sposób interfejs w języku C# jest podobny do klasy abstrakcyjnej, w którym abstrakcyjne są wszystkie metody. Jednak klasie lub strukturze można zaimplementować wiele interfejsów, ale klasa może dziedziczyć tylko jedną klasę, abstrakcyjny lub nie. W związku z tym za pomocą interfejsów, mogą obejmować zachowanie z wielu źródeł w klasie.  
  
 Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Interfejsy może zawierać metod, właściwości, zdarzenia, indeksatorów lub dowolnej kombinacji tych typów cztery elementu członkowskiego. Łącza do przykłady, zobacz [sekcje pokrewne](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections). Interfejs nie może zawierać stałe, pola, operatory, konstruktory wystąpień, finalizatory lub typów. Elementy członkowskie interfejsu są automatycznie publiczne i nie mogą zawierać żadnych modyfikatorów dostępu. Elementy członkowskie nie mogą być również [statycznych](../../../csharp/language-reference/keywords/static.md).  
  
 Aby zaimplementować elementu członkowskiego interfejsu, odpowiedni element członkowski klasy implementującej musi być publiczne, niestatycznej i ma taką samą nazwę i sygnaturę jako elementu członkowskiego interfejsu.  
  
 Po klasie lub strukturze implementuje interfejs, klasy lub struktury musi zapewniać implementację dla wszystkich elementów członkowskich, które definiuje interfejs. Sam interfejs zapewnia nie funkcji klasie lub strukturze może dziedziczyć w taki sposób, może dziedziczyć funkcje klasy podstawowej. Jednak jeśli klasą podstawową implementuje interfejs, dowolnej klasy pochodzącej od klasy podstawowej dziedziczy tę implementację.  
  
 Poniższy przykład przedstawia implementację interfejsu IEquatable < T\> interfejsu. Klasy implementującej `Car`, musi zapewniać implementację elementu <xref:System.IEquatable%601.Equals%2A> metody.  
  
 [!code-csharp[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 Właściwości i indeksatorów w klasie można zdefiniować dodatkowe metody dostępu właściwości lub indeksatora, który jest zdefiniowany w interfejsie. Na przykład interfejs może zadeklarować właściwość, która ma [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu. Klasa, która implementuje interfejs można zadeklarować tej właściwości zarówno `get` i [ustawić](../../../csharp/language-reference/keywords/set.md) metody dostępu. Jednak jeśli właściwość lub indeksator używa jawnej implementacji, metody dostępu muszą być zgodne. Aby uzyskać więcej informacji na temat jawną implementację, zobacz [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) i [właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).  
  
 Interfejsy mogą zawierać inne interfejsy. Klasa może zawierać interfejsu wiele razy przy użyciu klas podstawowych, które dziedziczy lub za pośrednictwem interfejsów, które implementują inne interfejsy. Jednak klasy może zapewniać implementację interfejsu tylko jeden czasu i tylko wtedy, jeśli klasa deklaruje interfejsu w definicji klasy (`class ClassName : InterfaceName`). Jeśli interfejs jest dziedziczone, ponieważ dziedziczone klasy podstawowej, która implementuje interfejs, klasa podstawowa zawiera implementacji członków interfejsu. Klasa pochodna można jednak reimplement elementy członkowskie interfejsu zamiast dziedziczone implementacji.  
  
 Klasa podstawowa również mogą implementować członków interfejsu przy użyciu wirtualnych elementów członkowskich. W takim przypadku Klasa pochodna zmienić zachowanie interfejsu przez zastąpienie wirtualne elementy członkowskie. Aby uzyskać więcej informacji o wirtualnych elementów członkowskich, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Podsumowanie interfejsów  
 Interfejs ma następujące właściwości:  
  
-   Interfejs przypomina abstrakcyjną klasę podstawową. Klasy lub struktury, która implementuje interfejs musi implementować wszyscy jej członkowie.  
  
-   Nie można bezpośrednio utworzyć wystąpienia interfejsu. Jej elementów członkowskich są implementowane przez klasy lub struktury, która implementuje interfejs.  
  
-   Interfejsy mogą zawierać zdarzenia, indeksatorów, metod i właściwości.  
  
-   Interfejsy zawierać żadnej implementacji metody.  
  
-   Wiele interfejsów można zaimplementować w klasie lub strukturze. Klasy mogą dziedziczyć klasa podstawowa i także implementować jeden lub więcej interfejsów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Jawna implementacja interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 Wyjaśnia sposób tworzenia elementu członkowskiego klasy, które są specyficzne dla interfejsu.  
  
 [Porady: jawne Implementowanie elementów interfejsu](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 Przykład sposobu jawne Implementowanie elementów interfejsów.  
  
 [Porady: jawne Implementowanie elementów dwóch interfejsów](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 Przykład sposobu jawne Implementowanie elementów interfejsów z dziedziczenia.  
  
##  <a name="BKMK_RelatedSections"></a>Sekcje pokrewne  
  
-   [Właściwości interfejsu](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Indeksatory w interfejsach](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Porady: zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
  
-   [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Polecany rozdział książki  
 [Interfejsy](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) w [Learning C# 3.0: wzorca podstawy języka C# 3.0](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
