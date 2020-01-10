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
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="0de2d-102">Korzystanie z instrukcji foreach zC# tablicami (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="0de2d-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="0de2d-103">Instrukcja [foreach](../../language-reference/keywords/foreach-in.md) zawiera prosty, czysty sposób wykonywania iteracji przez elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="0de2d-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="0de2d-104">W przypadku tablic jednowymiarowych instrukcja `foreach` przetwarza elementy w kolejności rosnącego indeksu, rozpoczynając od indeksu 0 i kończąc na `Length - 1`indeksu:</span><span class="sxs-lookup"><span data-stu-id="0de2d-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="0de2d-105">W przypadku tablic wielowymiarowych elementy są przenoszone w taki sposób, że indeksy w wymiarze z prawej strony są najpierw zwiększane, następnie następny lewy wymiar i tak dalej, po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="0de2d-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="0de2d-106">Jednak w przypadku tablic wielowymiarowych użycie zagnieżdżonej pętli [for](../../language-reference/keywords/for.md) daje większą kontrolę nad kolejnością, w której mają być przetwarzane elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="0de2d-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="0de2d-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0de2d-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="0de2d-108">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0de2d-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0de2d-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="0de2d-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="0de2d-110">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="0de2d-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="0de2d-111">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="0de2d-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="0de2d-112">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="0de2d-112">Jagged Arrays</span></span>](jagged-arrays.md)
