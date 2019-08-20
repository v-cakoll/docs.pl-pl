---
title: Tablice jako obiekty — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597362"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)

W C#programie tablice są w rzeczywistości obiektami, a nie tylko w przypadku regionów ciągłej pamięci, jak w C++C i. <xref:System.Array>jest abstrakcyjnym typem podstawowym wszystkich typów tablicowych. Można użyć właściwości i innych elementów członkowskich klasy, które <xref:System.Array> mają. Przykładem może być użycie <xref:System.Array.Length%2A> właściwości w celu uzyskania długości tablicy. Poniższy kod przypisuje długość `numbers` tablicy, `5`czyli do zmiennej o nazwie `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <xref:System.Array> Klasa zawiera wiele innych użytecznych metod i właściwości do sortowania, wyszukiwania i kopiowania tablic.  
  
## <a name="example"></a>Przykład

 Ten przykład używa właściwości <xref:System.Array.Rank%2A> , aby wyświetlić liczbę wymiarów tablicy.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
