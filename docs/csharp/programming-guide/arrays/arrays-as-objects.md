---
title: Tablice jako obiekty — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 9905168662496c46d20f191c04f21d8630d02fa2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772112"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="2bdcf-102">Tablice jako obiekty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2bdcf-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="2bdcf-103">W C#programie tablice są w rzeczywistości obiektami, a nie tylko w przypadku regionów ciągłej pamięci, jak w C++C i.</span><span class="sxs-lookup"><span data-stu-id="2bdcf-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="2bdcf-104"><xref:System.Array> jest abstrakcyjnym typem podstawowym wszystkich typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="2bdcf-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="2bdcf-105">Można użyć właściwości i innych elementów członkowskich klasy, które <xref:System.Array> ma.</span><span class="sxs-lookup"><span data-stu-id="2bdcf-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="2bdcf-106">Przykładem jest użycie właściwości <xref:System.Array.Length%2A>, aby uzyskać długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="2bdcf-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="2bdcf-107">Poniższy kod przypisuje długość tablicy `numbers`, która jest `5`, do zmiennej o nazwie `lengthOfNumbers`:</span><span class="sxs-lookup"><span data-stu-id="2bdcf-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="2bdcf-108">Klasa <xref:System.Array> udostępnia wiele innych użytecznych metod i właściwości do sortowania, wyszukiwania i kopiowania tablic.</span><span class="sxs-lookup"><span data-stu-id="2bdcf-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="2bdcf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2bdcf-109">Example</span></span>

<span data-ttu-id="2bdcf-110">Ten przykład używa właściwości <xref:System.Array.Rank%2A>, aby wyświetlić liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="2bdcf-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="2bdcf-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bdcf-111">See also</span></span>

- [<span data-ttu-id="2bdcf-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2bdcf-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2bdcf-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="2bdcf-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="2bdcf-114">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="2bdcf-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="2bdcf-115">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="2bdcf-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="2bdcf-116">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="2bdcf-116">Jagged Arrays</span></span>](./jagged-arrays.md)
