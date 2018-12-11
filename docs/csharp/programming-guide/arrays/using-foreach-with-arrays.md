---
title: Używanie instrukcji foreach z tablicami - C# Programming Guide
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a290cd709dd6491981658f467fa0163011290128
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238471"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="e965f-102">Używanie instrukcji foreach z tablicami (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e965f-102">Using foreach with arrays (C# Programming Guide)</span></span>

<span data-ttu-id="e965f-103">[Foreach](../../language-reference/keywords/foreach-in.md) instrukcja oferuje prosty, jasny sposób iterowania po elementach tablicy.</span><span class="sxs-lookup"><span data-stu-id="e965f-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="e965f-104">Aby uzyskać tablice jednowymiarowe `foreach` instrukcji przetwarza elementy w kolejności rosnącej indeksu począwszy od indeksu 0, a kończąc na indeks `Length - 1`:</span><span class="sxs-lookup"><span data-stu-id="e965f-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="e965f-105">Dla wielowymiarowych tablic elementów jest przesunięta w taki sposób, że indeksy po prawej stronie wymiaru są pierwszy zwiększona, a następnie dalej wymiaru po lewej stronie, i tak dalej, aby po lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="e965f-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="e965f-106">Jednak przy użyciu tablic wielowymiarowych użycie zagnieżdżonej [dla](../../language-reference/keywords/for.md) pętli daje większą kontrolę nad kolejność, w której ma być przetwarzane elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="e965f-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="e965f-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e965f-107">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="e965f-108">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e965f-108">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="e965f-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="e965f-109">Arrays</span></span>](index.md)  
- [<span data-ttu-id="e965f-110">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="e965f-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="e965f-111">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="e965f-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="e965f-112">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="e965f-112">Jagged Arrays</span></span>](jagged-arrays.md)
