---
title: Tablice jako obiekty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 07e824d21ffc02ba7a3c33507d22d1dc7a1ac638
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="5cdb0-102">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5cdb0-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="5cdb0-103">W języku C# tablic są faktycznie obiektów, a nie tylko adresowanego regiony pamięci ciągłej jak C i C++.</span><span class="sxs-lookup"><span data-stu-id="5cdb0-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="5cdb0-104"><xref:System.Array> jest podstawowy typ abstrakcyjny typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="5cdb0-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="5cdb0-105">Można użyć właściwości oraz o innych elementach członkowskich klasy, która <xref:System.Array> ma.</span><span class="sxs-lookup"><span data-stu-id="5cdb0-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="5cdb0-106">Przykładem takiego jak przy użyciu <xref:System.Array.Length%2A> właściwość, aby pobrać długości tablicy.</span><span class="sxs-lookup"><span data-stu-id="5cdb0-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="5cdb0-107">Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, do zmiennej o nazwie `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="5cdb0-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="5cdb0-108"><xref:System.Array> Klasa udostępnia wiele innych przydatne metody i właściwości sortowanie, wyszukiwanie i kopiowanie tablic.</span><span class="sxs-lookup"><span data-stu-id="5cdb0-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cdb0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cdb0-109">Example</span></span>  
 <span data-ttu-id="5cdb0-110">W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="5cdb0-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5cdb0-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cdb0-111">See Also</span></span>  
 [<span data-ttu-id="5cdb0-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5cdb0-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5cdb0-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="5cdb0-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="5cdb0-114">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="5cdb0-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="5cdb0-115">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="5cdb0-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="5cdb0-116">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="5cdb0-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
