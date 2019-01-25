---
title: Użycie tablic jako obiektów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0c4b5dcbd9e227e4edd5f549b687e3ded90ee9bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740492"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="f73cc-102">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f73cc-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="f73cc-103">W języku C# tablice są faktycznie obiektów i nie tylko adresy regionach ciągłej pamięci, tak jak w językach C i C++.</span><span class="sxs-lookup"><span data-stu-id="f73cc-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="f73cc-104"><xref:System.Array> jest abstrakcyjna typem podstawowym wszystkich typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="f73cc-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="f73cc-105">Można użyć właściwości i inne elementy członkowskie klasy, która <xref:System.Array> ma.</span><span class="sxs-lookup"><span data-stu-id="f73cc-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="f73cc-106">Przykładem takiej jak przy użyciu <xref:System.Array.Length%2A> właściwości, które można pobrać długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="f73cc-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="f73cc-107">Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, ze zmienną o nazwie `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="f73cc-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="f73cc-108"><xref:System.Array> Klasa oferuje wiele innych użytecznych metod i właściwości sortowanie, wyszukiwanie i kopiowania tablic.</span><span class="sxs-lookup"><span data-stu-id="f73cc-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f73cc-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f73cc-109">Example</span></span>

 <span data-ttu-id="f73cc-110">W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="f73cc-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f73cc-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f73cc-111">See also</span></span>

- [<span data-ttu-id="f73cc-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f73cc-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f73cc-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="f73cc-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="f73cc-114">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="f73cc-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="f73cc-115">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="f73cc-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="f73cc-116">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="f73cc-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
