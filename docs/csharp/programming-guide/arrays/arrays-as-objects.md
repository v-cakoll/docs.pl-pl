---
title: Użycie tablic jako obiektów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0bbbf7ecc5eff650f7a2edc73546833afd2be094
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242337"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)

W języku C# tablice są faktycznie obiektów i nie tylko adresy regionach ciągłej pamięci, tak jak w językach C i C++. <xref:System.Array> jest abstrakcyjna typem podstawowym wszystkich typów tablicowych. Można użyć właściwości i inne elementy członkowskie klasy, która <xref:System.Array> ma. Przykładem takiej jak przy użyciu <xref:System.Array.Length%2A> właściwości, które można pobrać długość tablicy. Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, ze zmienną o nazwie `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Klasa oferuje wiele innych użytecznych metod i właściwości sortowanie, wyszukiwanie i kopiowania tablic.  
  
## <a name="example"></a>Przykład

 W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Tablice](../../../csharp/programming-guide/arrays/index.md)  
- [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
