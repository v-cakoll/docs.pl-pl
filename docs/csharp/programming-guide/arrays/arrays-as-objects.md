---
title: Tablice jako obiekty — Przewodnik programowania w języku C#
description: Tablice w języku C# są obiektami abstrakcyjnej tablicy typów podstawowych. Można użyć właściwości i innych elementów członkowskich klasy tablicy, takich jak Właściwość length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474725"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Tablice jako obiekty (Przewodnik programowania w języku C#)

W języku C# tablice są w rzeczywistości obiektami, a nie tylko regionami ciągłej pamięci, jak w C i C++. <xref:System.Array>jest abstrakcyjnym typem podstawowym wszystkich typów tablicowych. Można użyć właściwości i innych elementów członkowskich klasy, które <xref:System.Array> mają. Przykładem jest użycie <xref:System.Array.Length%2A> właściwości w celu uzyskania długości tablicy. Poniższy kod przypisuje długość `numbers` tablicy, czyli `5` do zmiennej o nazwie `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array>Klasa zawiera wiele innych użytecznych metod i właściwości do sortowania, wyszukiwania i kopiowania tablic.

## <a name="example"></a>Przykład

Ten przykład używa <xref:System.Array.Rank%2A> właściwości, aby wyświetlić liczbę wymiarów tablicy.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
