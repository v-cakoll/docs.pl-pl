---
title: Klasy abstrakcyjne i zapieczętowane oraz członkowie klas - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 3257d365bb9816f4cb41d354f78c88ad4fa0f567
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523834"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Klasy abstrakcyjne i zapieczętowane oraz członkowie klas (Przewodnik programowania w języku C#)
[Abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md) — słowo kluczowe pozwala na tworzenie klas i [klasy](../../../csharp/language-reference/keywords/class.md) elementów członkowskich, które są niekompletne i muszą być zaimplementowane w klasie pochodnej.  
  
 [Zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) — słowo kluczowe pozwala zapobiegać dziedziczeniu klasy lub niektórych członków klasy, które zostały wcześniej oznaczone [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Klasy abstrakcyjne i elementy członkowskie klas  
 Klasy mogą być deklarowane jako abstrakcyjne poprzez umieszczenie słowa kluczowego `abstract` przed definicją klasy. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Nie można utworzyć wystąpienia klasy abstrakcyjnej. Celem klasy abstrakcyjnej jest zapewnienie wspólnej definicji klasy podstawowej, można współdzielić wiele klas pochodnych. Na przykład biblioteka klas może zdefiniować klasę abstrakcyjną, która jest używana jako parametr do wielu swoich funkcji i wymaga, aby programiści stosujący tę bibliotekę, aby zapewnić zapewniali własną implementację klasy, tworząc klasę pochodną.  
  
 Klasy abstrakcyjne mogą również definiować metody abstrakcyjne. Jest to osiągane przez dodanie słowa kluczowego `abstract` przed zwracanym typem metody. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Metody abstrakcyjne nie mają implementacji, dzięki czemu definicji metody następuje średnik zamiast zwykłego bloku metody. Klasy pochodne klasy abstrakcyjnej muszą implementować wszystkie metody abstrakcyjne. Gdy klasa abstrakcyjna dziedziczy metodę wirtualną klasy bazowej, klasa abstrakcyjna może zastąpić metodę wirtualną przez metodę abstrakcyjną. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Jeśli `virtual` metoda jest zadeklarowana `abstract`, nadal jest wirtualna dla każdej klasy dziedziczącej z klasy abstrakcyjnej. Klasa dziedzicząca metodę abstrakcyjną nie ma dostępu do oryginalnej implementacji metody — w poprzednim przykładzie `DoWork` w klasie F nie może wywołać `DoWork` w klasie D. W ten sposób klasa abstrakcyjna może wymusić na klasach pochodnych dostarczanie nowych implementacji metody dla metod wirtualnych.  
  
## <a name="sealed-classes-and-class-members"></a>Zapieczętowane klasy i członkowie klas  
 Klasy mogą być deklarowane jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) poprzez umieszczenie słowa kluczowego `sealed` przed definicją klasy. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Klasa zapieczętowana nie może służyć jako klasę bazową. Z tego powodu nie może być również klasy abstrakcyjnej. Zapieczętowane klasy uniemożliwiają wyprowadzanie. Ponieważ nigdy nie, nie można ich używać jako klasa bazowa, niektóre optymalizacje w czasie wykonywania można wprowadzić wywoływania zapieczętowanych elementów członkowskich klas trochę szybszy.  
  
 Metoda, indeksator, właściwość lub zdarzenie w klasie pochodnej, która zastępuje wirtualny element członkowski klasy podstawowej, można zadeklarować ten element jako zapieczętowany. To neguje wirtualny aspekt elementu członkowskiego dla dalszych klas pochodnych. Jest to realizowane poprzez umieszczenie `sealed` — słowo kluczowe przed [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe w deklaracji członka klasy. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)
- [Instrukcje: Definiowanie właściwości abstrakcyjnych](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
