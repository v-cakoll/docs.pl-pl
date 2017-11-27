---
title: "Tablice jako obiekty (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)
W języku C# tablic są faktycznie obiektów, a nie tylko adresowanego regiony pamięci ciągłej jak C i C++. <xref:System.Array>jest podstawowy typ abstrakcyjny typów tablicowych. Można użyć właściwości oraz o innych elementach członkowskich klasy, która <xref:System.Array> ma. Przykładem takiego jak przy użyciu <xref:System.Array.Length%2A> właściwość, aby pobrać długości tablicy. Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, do zmiennej o nazwie `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Klasa udostępnia wiele innych przydatne metody i właściwości sortowanie, wyszukiwanie i kopiowanie tablic.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
