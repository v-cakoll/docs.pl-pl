---
title: Tablice jako obiekty — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715088"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="804fa-102">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="804fa-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="804fa-103">W języku C#tablice są faktycznie obiekty, a nie tylko adresowalne regiony pamięci ciągłej, jak w Języku C i C++.</span><span class="sxs-lookup"><span data-stu-id="804fa-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="804fa-104"><xref:System.Array>jest abstrakcyjnym typem podstawowym wszystkich typów tablic.</span><span class="sxs-lookup"><span data-stu-id="804fa-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="804fa-105">Można użyć właściwości i innych elementów <xref:System.Array> członkowskich klasy, która ma.</span><span class="sxs-lookup"><span data-stu-id="804fa-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="804fa-106">Przykładem tego jest za <xref:System.Array.Length%2A> pomocą właściwości, aby uzyskać długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="804fa-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="804fa-107">Poniższy kod przypisuje długość tablicy, `numbers` która `5`jest , `lengthOfNumbers`do zmiennej o nazwie:</span><span class="sxs-lookup"><span data-stu-id="804fa-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="804fa-108">Klasa <xref:System.Array> zawiera wiele innych przydatnych metod i właściwości sortowania, wyszukiwania i kopiowania tablic.</span><span class="sxs-lookup"><span data-stu-id="804fa-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="804fa-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="804fa-109">Example</span></span>

<span data-ttu-id="804fa-110">W tym <xref:System.Array.Rank%2A> przykładzie użyto właściwości, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="804fa-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="804fa-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="804fa-111">See also</span></span>

- [<span data-ttu-id="804fa-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="804fa-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="804fa-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="804fa-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="804fa-114">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="804fa-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="804fa-115">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="804fa-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="804fa-116">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="804fa-116">Jagged Arrays</span></span>](./jagged-arrays.md)
