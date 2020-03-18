---
title: Korzystanie z foreach z tablicami - Przewodnik programowania C#
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705681"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Korzystanie z foreach z tablicami (C# Programming Guide)

[Foreach](../../language-reference/keywords/foreach-in.md) instrukcji zapewnia prosty, czysty sposób iterate za pomocą elementów tablicy.

W przypadku tablic jednowymiarowych instrukcja `foreach` przetwarza elementy w rosnącej kolejności `Length - 1`indeksu, zaczynając od indeksu 0, a kończąc na indeksie:

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

W przypadku tablic wielowymiarowych elementy są przesuwane w taki sposób, że indeksy wymiaru najbardziej po prawej stronie są najpierw zwiększane, a następnie następny lewy wymiar itd.:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Jednak w przypadku tablic wielowymiarowych za pomocą zagnieżdżonego [dla](../../language-reference/keywords/for.md) pętli daje większą kontrolę nad kolejnością przetwarzania elementów tablicy.

## <a name="see-also"></a>Zobacz też

- <xref:System.Array>
- [Przewodnik programowania języka C#](../index.md)
- [Tablice](index.md)
- [Tablice jednowymiarowe](single-dimensional-arrays.md)
- [Tablice wielowymiarowe](multidimensional-arrays.md)
- [Tablice nieregularne](jagged-arrays.md)
