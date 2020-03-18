---
title: Tablice jako obiekty — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715088"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)

W języku C#tablice są faktycznie obiekty, a nie tylko adresowalne regiony pamięci ciągłej, jak w Języku C i C++. <xref:System.Array>jest abstrakcyjnym typem podstawowym wszystkich typów tablic. Można użyć właściwości i innych elementów <xref:System.Array> członkowskich klasy, która ma. Przykładem tego jest za <xref:System.Array.Length%2A> pomocą właściwości, aby uzyskać długość tablicy. Poniższy kod przypisuje długość tablicy, `numbers` która `5`jest , `lengthOfNumbers`do zmiennej o nazwie:

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

Klasa <xref:System.Array> zawiera wiele innych przydatnych metod i właściwości sortowania, wyszukiwania i kopiowania tablic.

## <a name="example"></a>Przykład

W tym <xref:System.Array.Rank%2A> przykładzie użyto właściwości, aby wyświetlić liczbę wymiarów tablicy.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
