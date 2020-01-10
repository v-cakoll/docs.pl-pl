---
title: Tablice jako obiekty — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715088"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)

W C#programie tablice są w rzeczywistości obiektami, a nie tylko w przypadku regionów ciągłej pamięci, jak w C++C i. <xref:System.Array> jest abstrakcyjnym typem podstawowym wszystkich typów tablicowych. Można użyć właściwości i innych elementów członkowskich klasy, które <xref:System.Array> ma. Przykładem jest użycie właściwości <xref:System.Array.Length%2A>, aby uzyskać długość tablicy. Poniższy kod przypisuje długość tablicy `numbers`, która jest `5`, do zmiennej o nazwie `lengthOfNumbers`:

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

Klasa <xref:System.Array> udostępnia wiele innych użytecznych metod i właściwości do sortowania, wyszukiwania i kopiowania tablic.

## <a name="example"></a>Przykład

Ten przykład używa właściwości <xref:System.Array.Rank%2A>, aby wyświetlić liczbę wymiarów tablicy.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
