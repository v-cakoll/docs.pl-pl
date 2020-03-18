---
title: Jak zdefiniować właściwości abstrakcyjne - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705616"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Jak zdefiniować właściwości abstrakcyjne (Przewodnik programowania C#)
W poniższym przykładzie pokazano, jak zdefiniować właściwości [abstrakcyjne.](../../language-reference/keywords/abstract.md) Abstrakcyjna deklaracja właściwości nie zapewnia implementacji akcesorów właściwości — deklaruje, że klasa obsługuje właściwości, ale pozostawia implementacji akcesora do klas pochodnych. W poniższym przykładzie pokazano, jak zaimplementować właściwości abstrakcyjne dziedziczone z klasy podstawowej.  
  
 Ten przykład składa się z trzech plików, z których każdy jest kompilowany indywidualnie, a jego wynikowy zestaw odwołuje się do następnej kompilacji:  
  
- abstractshape.cs: `Shape` klasa, która `Area` zawiera właściwość abstrakcyjną.  
  
- shapes.cs: Podklasy `Shape` klasy.  
  
- shapetest.cs: Program testowy do wyświetlania obszarów niektórych `Shape`obiektów pochodnych.  
  
 Aby skompilować przykład, użyj następującego polecenia:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Spowoduje to utworzenie pliku wykonywalnego shapetest.exe.  
  
## <a name="example"></a>Przykład  
 Ten plik deklaruje `Shape` klasę, `Area` która zawiera `double`właściwość typu .  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Modyfikatory na nieruchomości są umieszczane na samym oświadczeniu majątkowym. Przykład:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Podczas deklarowania właściwości abstrakcyjnej `Area` (na przykład w tym przykładzie), wystarczy wskazać, jakie akcesory właściwości są dostępne, ale nie implementują ich. W tym przykładzie dostępna jest tylko akcesor [get,](../../language-reference/keywords/get.md) więc właściwość jest tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia trzy `Shape` podklasy i jak `Area` zastępują właściwość, aby zapewnić własną implementację.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia program testowy, `Shape`który tworzy wiele obiektów pochodnych i drukuje ich obszary.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](./abstract-and-sealed-classes-and-class-members.md)
- [Właściwości](./properties.md)
