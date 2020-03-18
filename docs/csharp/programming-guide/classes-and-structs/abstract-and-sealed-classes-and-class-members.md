---
title: Abstrakcyjne i zapieczętowane klasy i elementy członkowskie klasy - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715006"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Klasy abstrakcyjne i zapieczętowane oraz członkowie klas (Przewodnik programowania w języku C#)
[Abstrakcyjne](../../language-reference/keywords/abstract.md) słowo kluczowe umożliwia tworzenie klas i elementów członkowskich [klasy,](../../language-reference/keywords/class.md) które są niekompletne i muszą być implementowane w klasie pochodnej.  
  
 [Zapieczętowane](../../language-reference/keywords/sealed.md) słowo kluczowe umożliwia zapobieganie dziedziczeniu klasy lub niektórych elementów członkowskich klasy, które zostały wcześniej oznaczone [jako wirtualne.](../../language-reference/keywords/virtual.md)  
  
## <a name="abstract-classes-and-class-members"></a>Klasy abstrakcyjne i elementy członkowskie klasy  
 Klasy mogą być zadeklarowane jako `abstract` abstrakcyjne, umieszczając słowo kluczowe przed definicją klasy. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 Nie można utworzyć wystąpienia klasy abstrakcyjnej. Celem klasy abstrakcyjnej jest zapewnienie wspólnej definicji klasy podstawowej, które można udostępnić wiele klas pochodnych. Na przykład biblioteka klas może zdefiniować klasę abstrakcyjną, która jest używana jako parametr do wielu jego funkcji i wymagać programistów przy użyciu tej biblioteki, aby zapewnić własną implementację klasy, tworząc klasę pochodną.  
  
 Klasy abstrakcyjne mogą również definiować metody abstrakcyjne. Jest to realizowane przez `abstract` dodanie słowa kluczowego przed zwracanym typem metody. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 Metody abstrakcyjne nie mają implementacji, więc po definicji metody następuje średnik zamiast normalnego bloku metody. Klasy pochodne klasy abstrakcyjnej musi implementować wszystkie metody abstrakcyjne. Gdy klasa abstrakcyjna dziedziczy metodę wirtualną z klasy podstawowej, klasa abstrakcyjna może zastąpić metodę wirtualną metodą abstrakcyjną. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 Jeśli `virtual` metoda jest `abstract`zadeklarowana , nadal jest wirtualny dla każdej klasy dziedziczącej z klasy abstrakcyjnej. Klasa dziedzicząca metodę abstrakcyjną nie może uzyskać dostępu `DoWork` do oryginalnej `DoWork` implementacji metody — w poprzednim przykładzie na klasie F nie można wywołać klasy D. W ten sposób klasy abstrakcyjne może wymusić klasy pochodne, aby zapewnić implementacje nowych metod dla metod wirtualnych.  
  
## <a name="sealed-classes-and-class-members"></a>Zapieczętowane klasy i członkowie klasy  
 Klasy mogą być [zadeklarowane](../../language-reference/keywords/sealed.md) jako `sealed` zapieczętowane przez umieszczenie słowa kluczowego przed definicją klasy. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 Klasa zapieczętowana nie może być używana jako klasa podstawowa. Z tego powodu nie może być również klasą abstrakcyjną. Zapieczętowane klasy uniemożliwiają wyprowadzenie. Ponieważ nigdy nie mogą być używane jako klasa podstawowa, niektóre optymalizacje w czasie wykonywania może wywołać zapieczętowane elementy członkowskie klasy nieco szybciej.  
  
 Metoda, indeksator, właściwość lub zdarzenie w klasie pochodnej, która jest zastępowanie wirtualnego elementu członkowskiego klasy podstawowej można zadeklarować, że element członkowski jako zapieczętowane. To neguje wirtualny aspekt elementu członkowskiego dla wszelkich dalszych klasy pochodnej. Jest to realizowane przez `sealed` umieszczenie słowa kluczowego przed [override](../../language-reference/keywords/override.md) słowa kluczowego w deklaracji elementu członkowskiego klasy. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Dziedziczenie](./inheritance.md)
- [Metody](./methods.md)
- [Pola](./fields.md)
- [Jak zdefiniować właściwości abstrakcyjne](./how-to-define-abstract-properties.md)
