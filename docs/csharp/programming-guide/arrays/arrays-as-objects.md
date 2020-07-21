---
title: Tablice jako obiekty — Przewodnik programowania w języku C#
description: Tablice w języku C# są obiektami abstrakcyjnej tablicy typów podstawowych. Można użyć właściwości i innych elementów członkowskich klasy tablicy, takich jak Właściwość length.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474725"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="4163c-104">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4163c-104">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="4163c-105">W języku C# tablice są w rzeczywistości obiektami, a nie tylko regionami ciągłej pamięci, jak w C i C++.</span><span class="sxs-lookup"><span data-stu-id="4163c-105">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="4163c-106"><xref:System.Array>jest abstrakcyjnym typem podstawowym wszystkich typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="4163c-106"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="4163c-107">Można użyć właściwości i innych elementów członkowskich klasy, które <xref:System.Array> mają.</span><span class="sxs-lookup"><span data-stu-id="4163c-107">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="4163c-108">Przykładem jest użycie <xref:System.Array.Length%2A> właściwości w celu uzyskania długości tablicy.</span><span class="sxs-lookup"><span data-stu-id="4163c-108">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="4163c-109">Poniższy kod przypisuje długość `numbers` tablicy, czyli `5` do zmiennej o nazwie `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="4163c-109">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="4163c-110"><xref:System.Array>Klasa zawiera wiele innych użytecznych metod i właściwości do sortowania, wyszukiwania i kopiowania tablic.</span><span class="sxs-lookup"><span data-stu-id="4163c-110">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="4163c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4163c-111">Example</span></span>

<span data-ttu-id="4163c-112">Ten przykład używa <xref:System.Array.Rank%2A> właściwości, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="4163c-112">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="4163c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4163c-113">See also</span></span>

- [<span data-ttu-id="4163c-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4163c-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4163c-115">Tablice</span><span class="sxs-lookup"><span data-stu-id="4163c-115">Arrays</span></span>](./index.md)
- [<span data-ttu-id="4163c-116">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="4163c-116">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="4163c-117">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="4163c-117">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="4163c-118">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="4163c-118">Jagged Arrays</span></span>](./jagged-arrays.md)
