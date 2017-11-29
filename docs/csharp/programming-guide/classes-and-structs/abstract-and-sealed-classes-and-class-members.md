---
title: "Klasy abstrakcyjne i zapieczętowane oraz członkowie klas (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dac7570c018bd577faac4540e4d800cc11143578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Klasy abstrakcyjne i zapieczętowane oraz członkowie klas (Przewodnik programowania w języku C#)
[Abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) — słowo kluczowe umożliwia tworzenie klas i [klasy](../../../csharp/language-reference/keywords/class.md) elementów członkowskich, które są niekompletne i musi zostać wdrożona w klasie pochodnej.  
  
 [Zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) — słowo kluczowe pozwala zapobiec dziedziczenia klasy lub niektórych elementów członkowskich klasy, które wcześniej zostały oznaczone [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Klasy abstrakcyjne i elementów członkowskich klasy  
 Klasy mogą być deklarowane jako abstrakcyjny, umieszczając słowo kluczowe `abstract` przed definicją klasy. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Nie można utworzyć wystąpienia klasy abstrakcyjnej. Cel klasy abstrakcyjnej jest zapewnienie wspólną definicję klasy podstawowej, które można udostępniać wielu klas pochodnych. Biblioteki klas może na przykład zdefiniować klasę abstrakcyjną, który jest używany jako parametr do wielu jej funkcji i wymagają Programiści używający tej biblioteki do ich własnych implementacji klasy przy tworzeniu klasy pochodnej.  
  
 Klasy abstrakcyjne mogą również definiować metody abstrakcyjnej. Jest to osiągane przez dodanie słów kluczowych `abstract` przed zwracany typ metody. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Metody abstrakcyjne ma żadnej implementacji, w związku z definicją metody następuje średnik zamiast bloku normalne — metoda. Klasy pochodne klasy abstrakcyjnej musi implementować wszystkie metody abstrakcyjnej. Gdy klasa abstrakcyjna metoda wirtualna z klasy podstawowej, klasa abstrakcyjna można przesłonić metodę wirtualną z metody abstrakcyjnej. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Jeśli `virtual` zadeklarowano metody `abstract`, jest nadal wirtualnych do dowolnej klasy dziedziczy z klasy abstrakcyjnej. Dziedziczenie metody abstrakcyjnej klasy nie ma dostępu do oryginalnego implementacji metody — w poprzednim przykładzie `DoWork` w klasie nie można wywołać F `DoWork` na D. — klasa W ten sposób klasy abstrakcyjnej można wymusić klas pochodnych zapewnienie nowe implementacje metod dla metod wirtualnych.  
  
## <a name="sealed-classes-and-class-members"></a>Zapieczętowane klasy oraz członkowie klas  
 Klasy mogą być deklarowane jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) ustawiając kluczowego `sealed` przed definicją klasy. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Nie można użyć klasy zapieczętowanej jako klasę podstawową. Z tego powodu nie może być również klasy abstrakcyjnej. Zapieczętowane klasy zapobiec pochodnym. Ponieważ mogą one nigdy nie zostać użyte jako klasę podstawową, niektóre funkcje optymalizacji środowiska wykonawczego wprowadzić wywoływania elementów członkowskich klasy zapieczętowanej nieco większą.  
  
 Metoda, indeksatora, właściwości lub zdarzenia w klasie pochodnej, która zastępuje wirtualnego elementu członkowskiego klasy podstawowej można zadeklarować tego elementu członkowskiego jako sealed. Negacja ten aspekt wirtualnego elementu członkowskiego dla dalszego pochodnej klasy. Jest to osiągane przez umieszczenie `sealed` przed [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe w deklaracji elementu członkowskiego klasy. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Porady: Definiowanie właściwości abstrakcyjnych](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
