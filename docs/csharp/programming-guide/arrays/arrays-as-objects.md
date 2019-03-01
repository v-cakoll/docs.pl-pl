---
title: Użycie tablic jako obiektów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977183"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)

W języku C# tablice są faktycznie obiektów i nie tylko adresy regionach ciągłej pamięci, tak jak w językach C i C++. <xref:System.Array> jest abstrakcyjna typem podstawowym wszystkich typów tablicowych. Można użyć właściwości i inne elementy członkowskie klasy, która <xref:System.Array> ma. Przykładem takiej jak przy użyciu <xref:System.Array.Length%2A> właściwości, które można pobrać długość tablicy. Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, ze zmienną o nazwie `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <xref:System.Array> Klasa oferuje wiele innych użytecznych metod i właściwości sortowanie, wyszukiwanie i kopiowania tablic.  
  
## <a name="example"></a>Przykład

 W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Tablice](../../../csharp/programming-guide/arrays/index.md)
- [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
