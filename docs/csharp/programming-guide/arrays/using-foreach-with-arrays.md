---
title: Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="8bd05-102">Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8bd05-102">Using foreach with Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8bd05-103">[Foreach](../../language-reference/keywords/foreach-in.md) instrukcji umożliwia proste, czystej iterowania po elementach tablicy.</span><span class="sxs-lookup"><span data-stu-id="8bd05-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="8bd05-104">Dla tablice jednowymiarowe `foreach` instrukcji przetwarzania elementów w kolejności rosnącej indeksu z indeksem 0 i kończąc indeksu `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="8bd05-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="8bd05-105">Dla wielowymiarowych tablic elementów jest przesunięta w taki sposób, że indeksy po prawej stronie wymiaru są pierwszy zwiększona, a następnie dalej wymiaru po lewej stronie, i tak dalej do lewej strony:</span><span class="sxs-lookup"><span data-stu-id="8bd05-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="8bd05-106">Jednak za pomocą tablice wielowymiarowe przy użyciu zagnieżdżoną [dla](../../language-reference/keywords/for.md) pętli zapewnia większą kontrolę nad w kolejności przetwarzania elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="8bd05-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bd05-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bd05-107">See also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="8bd05-108">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8bd05-108">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="8bd05-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="8bd05-109">Arrays</span></span>](index.md)  
 [<span data-ttu-id="8bd05-110">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="8bd05-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
 [<span data-ttu-id="8bd05-111">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="8bd05-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
 [<span data-ttu-id="8bd05-112">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="8bd05-112">Jagged Arrays</span></span>](jagged-arrays.md)
