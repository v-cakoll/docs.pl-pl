---
title: Korzystanie z instrukcji foreach z C# tablicami — Przewodnik programowania
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: bb121b0f5d990ef6e596b34a45606e2abde6811a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705681"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Korzystanie z instrukcji foreach zC# tablicami (Przewodnik programowania)

Instrukcja [foreach](../../language-reference/keywords/foreach-in.md) zawiera prosty, czysty sposób wykonywania iteracji przez elementy tablicy.

W przypadku tablic jednowymiarowych instrukcja `foreach` przetwarza elementy w kolejności rosnącego indeksu, rozpoczynając od indeksu 0 i kończąc na `Length - 1`indeksu:

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

W przypadku tablic wielowymiarowych elementy są przenoszone w taki sposób, że indeksy w wymiarze z prawej strony są najpierw zwiększane, następnie następny lewy wymiar i tak dalej, po lewej stronie:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Jednak w przypadku tablic wielowymiarowych użycie zagnieżdżonej pętli [for](../../language-reference/keywords/for.md) daje większą kontrolę nad kolejnością, w której mają być przetwarzane elementy tablicy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](index.md)
- [Tablice jednowymiarowe](single-dimensional-arrays.md)
- [Tablice wielowymiarowe](multidimensional-arrays.md)
- [Tablice nieregularne](jagged-arrays.md)
