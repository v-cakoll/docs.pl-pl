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
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="6aa9c-102">Korzystanie z foreach z tablicami (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="6aa9c-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="6aa9c-103">[Foreach](../../language-reference/keywords/foreach-in.md) instrukcji zapewnia prosty, czysty sposób iterate za pomocą elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="6aa9c-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="6aa9c-104">W przypadku tablic jednowymiarowych instrukcja `foreach` przetwarza elementy w rosnącej kolejności `Length - 1`indeksu, zaczynając od indeksu 0, a kończąc na indeksie:</span><span class="sxs-lookup"><span data-stu-id="6aa9c-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="6aa9c-105">W przypadku tablic wielowymiarowych elementy są przesuwane w taki sposób, że indeksy wymiaru najbardziej po prawej stronie są najpierw zwiększane, a następnie następny lewy wymiar itd.:</span><span class="sxs-lookup"><span data-stu-id="6aa9c-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="6aa9c-106">Jednak w przypadku tablic wielowymiarowych za pomocą zagnieżdżonego [dla](../../language-reference/keywords/for.md) pętli daje większą kontrolę nad kolejnością przetwarzania elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="6aa9c-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="6aa9c-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6aa9c-107">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="6aa9c-108">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="6aa9c-108">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6aa9c-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="6aa9c-109">Arrays</span></span>](index.md)
- [<span data-ttu-id="6aa9c-110">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="6aa9c-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="6aa9c-111">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="6aa9c-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="6aa9c-112">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="6aa9c-112">Jagged Arrays</span></span>](jagged-arrays.md)
