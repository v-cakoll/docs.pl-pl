---
title: 'Instrukcje: Definiowanie właściwości abstrakcyjnych C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: fae526f5dcd452fbc381ee86c892b72e61956f0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596868"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Instrukcje: Definiowanie właściwości abstrakcyjnychC# (Przewodnik programowania)
Poniższy przykład pokazuje, jak definiować właściwości [abstrakcyjne](../../language-reference/keywords/abstract.md) . Deklaracja właściwości abstrakcyjnej nie zapewnia implementacji metod dostępu do właściwości — deklaruje, że Klasa obsługuje właściwości, ale pozostawia implementację metody dostępu do klas pochodnych. W poniższym przykładzie pokazano, jak zaimplementować właściwości abstrakcyjne dziedziczone z klasy bazowej.  
  
 Ten przykład składa się z trzech plików, z których każdy jest kompilowany indywidualnie, a jego wynikający z nich zestaw jest przywoływany przez następną kompilację:  
  
- abstractshape.cs: `Shape` Klasa, która zawiera właściwość abstrakcyjną `Area` .  
  
- shapes.cs: Podklasy `Shape` klasy.  
  
- shapetest.cs: Program testowy do wyświetlania obszarów niektórych `Shape`obiektów pochodnych.  
  
 Aby skompilować przykład, użyj następującego polecenia:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Spowoduje to utworzenie pliku wykonywalnego shapetest. exe.  
  
## <a name="example"></a>Przykład  
 Ten plik deklaruje `Shape` klasę, która `Area` zawiera właściwość typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Modyfikatory we właściwości są umieszczane na samej deklaracji właściwości. Na przykład:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Podczas deklarowania właściwości abstrakcyjnej ( `Area` na przykład w tym przykładzie) można po prostu wskazać, jakie metody dostępu do właściwości są dostępne, ale nie należy ich wdrażać. W tym przykładzie dostępna jest tylko metoda dostępu [Get](../../language-reference/keywords/get.md) , więc właściwość jest tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia trzy podklasy `Shape` i sposób, w jaki `Area` zastępują właściwość w celu zapewnienia własnej implementacji.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia program testowy, który tworzy wiele `Shape`obiektów pochodnych i drukuje ich obszary.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](./abstract-and-sealed-classes-and-class-members.md)
- [Właściwości](./properties.md)
- [Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
