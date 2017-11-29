---
title: "Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="67c83-102">Używanie instrukcji foreach z tablicami (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="67c83-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="67c83-103">C# są także [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="67c83-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="67c83-104">Ta instrukcja oferuje prosty, jasny sposób wykonywania iteracji elementów tablicy lub dowolnej kolekcji, którą można wyliczać.</span><span class="sxs-lookup"><span data-stu-id="67c83-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="67c83-105">`foreach` Instrukcji przetwarzania elementów w kolejności zwrócony przez typ tablicy lub kolekcji moduł wyliczający, który zazwyczaj znajduje się w elemencie 0th do ostatniego.</span><span class="sxs-lookup"><span data-stu-id="67c83-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="67c83-106">Na przykład poniższy kod tworzy tablicę `numbers` i iteruje go przy użyciu `foreach` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="67c83-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 <span data-ttu-id="67c83-107">Tej samej metody można też używać do wykonywania iteracji elementów w tablicach wielowymiarowych, na przykład:</span><span class="sxs-lookup"><span data-stu-id="67c83-107">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 <span data-ttu-id="67c83-108">Jednak za pomocą tablice wielowymiarowe przy użyciu zagnieżdżoną [dla](../../../csharp/language-reference/keywords/for.md) pętli zapewnia większą kontrolę nad elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="67c83-108">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c83-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67c83-109">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="67c83-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="67c83-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="67c83-111">Tablice</span><span class="sxs-lookup"><span data-stu-id="67c83-111">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="67c83-112">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="67c83-112">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="67c83-113">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="67c83-113">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="67c83-114">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="67c83-114">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
