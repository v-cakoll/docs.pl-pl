---
title: "Tablice jako obiekty (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="001a9-102">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="001a9-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="001a9-103">W języku C# tablic są faktycznie obiektów, a nie tylko adresowanego regiony pamięci ciągłej jak C i C++.</span><span class="sxs-lookup"><span data-stu-id="001a9-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="001a9-104"><xref:System.Array>jest podstawowy typ abstrakcyjny typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="001a9-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="001a9-105">Można użyć właściwości oraz o innych elementach członkowskich klasy, która <xref:System.Array> ma.</span><span class="sxs-lookup"><span data-stu-id="001a9-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="001a9-106">Przykładem takiego jak przy użyciu <xref:System.Array.Length%2A> właściwość, aby pobrać długości tablicy.</span><span class="sxs-lookup"><span data-stu-id="001a9-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="001a9-107">Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, do zmiennej o nazwie `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="001a9-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="001a9-108"><xref:System.Array> Klasa udostępnia wiele innych przydatne metody i właściwości sortowanie, wyszukiwanie i kopiowanie tablic.</span><span class="sxs-lookup"><span data-stu-id="001a9-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="001a9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="001a9-109">Example</span></span>  
 <span data-ttu-id="001a9-110">W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="001a9-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="001a9-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="001a9-111">See Also</span></span>  
 [<span data-ttu-id="001a9-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="001a9-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="001a9-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="001a9-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="001a9-114">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="001a9-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="001a9-115">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="001a9-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="001a9-116">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="001a9-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
