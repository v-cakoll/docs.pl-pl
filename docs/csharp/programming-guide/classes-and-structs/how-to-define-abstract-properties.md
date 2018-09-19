---
title: 'Porady: definiowanie właściwości abstrakcyjnych (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 549867cac99784ce885b8fce8a1638c40ad88cec
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002986"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Porady: definiowanie właściwości abstrakcyjnych (Przewodnik programowania w języku C#)
Poniższy przykład pokazuje jak zdefiniować [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md) właściwości. Deklaracja właściwości abstrakcyjne nie zawiera implementacji metody dostępu właściwości, ponieważ relacja ta stwierdza, że obsługuje właściwości klasy, ale pozostawia implementacji metody dostępu dla klasy pochodnej. Poniższy przykład demonstruje sposób implementacji właściwości abstrakcyjnych dziedziczone z klasy podstawowej.  
  
 Ten przykład obejmuje trzy pliki, z których każdy jest kompilowany oddzielnie, a jego Wynikowy zestaw odwołuje się do następnej kompilacji:  
  
-   abstractshape.CS: `Shape` klasę, która zawiera abstrakcyjną `Area` właściwości.  
  
-   Shapes.CS: podklasy `Shape` klasy.  
  
-   shapetest.CS: program test, aby wyświetlić obszary niektórych `Shape`-obiektami wywodzącymi.  
  
 Aby skompilować przykład, użyj następującego polecenia:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Spowoduje to utworzenie shapetest.exe pliku wykonywalnego.  
  
## <a name="example"></a>Przykład  
 Ten plik deklaruje `Shape` klasę, która zawiera `Area` właściwość typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Modyfikatory we właściwości są umieszczane w sama deklaracja właściwości. Na przykład:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   Podczas deklarowania właściwość abstrakcyjną (takie jak `Area` w tym przykładzie), możesz po prostu wskazują, jakie metody dostępu właściwości są dostępne, ale nie ich wdrażania. W tym przykładzie, tylko [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu jest dostępna, więc właściwość jest tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje trzy podklasy `Shape` i jak zastąpić `Area` właściwość zapewniali własną implementację.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia program test, który tworzy szereg `Shape`-pochodnych obiektów i drukuje ich obszarów.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Instrukcje: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
