---
title: Korzystanie z instrukcji foreach z tablicami — Przewodnik programowania w języku C#
description: Instrukcja foreach w języku C# wykonuje iterację przez elementy tablicy. W przypadku tablic jednowymiarowych instrukcja foreach przetwarza elementy w celu zwiększenia kolejności indeksu.
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: d924a3ef3351cbb30b809a1542f35314ee721852
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474543"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="b4216-104">Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b4216-104">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="b4216-105">Instrukcja [foreach](../../language-reference/keywords/foreach-in.md) zawiera prosty, czysty sposób wykonywania iteracji przez elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="b4216-105">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="b4216-106">W przypadku tablic jednowymiarowych `foreach` instrukcja przetwarza elementy w kolejności rosnącego indeksu, rozpoczynając od indeksu 0 i kończąc na indeksie `Length - 1` :</span><span class="sxs-lookup"><span data-stu-id="b4216-106">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

<span data-ttu-id="b4216-107">W przypadku tablic wielowymiarowych elementy są przenoszone w taki sposób, że indeksy w wymiarze z prawej strony są najpierw zwiększane, następnie następny lewy wymiar i tak dalej, po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="b4216-107">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

<span data-ttu-id="b4216-108">Jednak w przypadku tablic wielowymiarowych użycie zagnieżdżonej pętli [for](../../language-reference/keywords/for.md) daje większą kontrolę nad kolejnością, w której mają być przetwarzane elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="b4216-108">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4216-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4216-109">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="b4216-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b4216-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b4216-111">Tablice</span><span class="sxs-lookup"><span data-stu-id="b4216-111">Arrays</span></span>](index.md)
- [<span data-ttu-id="b4216-112">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="b4216-112">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="b4216-113">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="b4216-113">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="b4216-114">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="b4216-114">Jagged Arrays</span></span>](jagged-arrays.md)
