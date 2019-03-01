---
title: Użycie tablic jako obiektów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977183"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="7532a-102">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7532a-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="7532a-103">W języku C# tablice są faktycznie obiektów i nie tylko adresy regionach ciągłej pamięci, tak jak w językach C i C++.</span><span class="sxs-lookup"><span data-stu-id="7532a-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="7532a-104"><xref:System.Array> jest abstrakcyjna typem podstawowym wszystkich typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="7532a-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="7532a-105">Można użyć właściwości i inne elementy członkowskie klasy, która <xref:System.Array> ma.</span><span class="sxs-lookup"><span data-stu-id="7532a-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="7532a-106">Przykładem takiej jak przy użyciu <xref:System.Array.Length%2A> właściwości, które można pobrać długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="7532a-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="7532a-107">Poniższy kod przypisuje długość `numbers` tablicy, która jest `5`, ze zmienną o nazwie `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="7532a-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="7532a-108"><xref:System.Array> Klasa oferuje wiele innych użytecznych metod i właściwości sortowanie, wyszukiwanie i kopiowania tablic.</span><span class="sxs-lookup"><span data-stu-id="7532a-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7532a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="7532a-109">Example</span></span>

 <span data-ttu-id="7532a-110">W tym przykładzie użyto <xref:System.Array.Rank%2A> właściwość, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="7532a-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7532a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7532a-111">See also</span></span>

- [<span data-ttu-id="7532a-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7532a-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7532a-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="7532a-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="7532a-114">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="7532a-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="7532a-115">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="7532a-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="7532a-116">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="7532a-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
