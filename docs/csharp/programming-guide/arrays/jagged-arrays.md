---
title: Postrzępione tablice — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705707"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="ad59c-102">Tablice nieregularne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ad59c-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="ad59c-103">Nieregularna tablica to ta, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="ad59c-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="ad59c-104">Elementy postrzępionej tablicy mogą mieć różne wymiary i rozmiary.</span><span class="sxs-lookup"><span data-stu-id="ad59c-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="ad59c-105">Postrzępiona tablica jest czasami nazywana "tablicą tablic".</span><span class="sxs-lookup"><span data-stu-id="ad59c-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="ad59c-106">W poniższych przykładach przedstawiono sposób deklarowania, inicjowania i uzyskiwania dostępu do tablic postrzępionych.</span><span class="sxs-lookup"><span data-stu-id="ad59c-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="ad59c-107">Poniżej przedstawiono deklarację tablicy jednowymiarowej, która ma trzy elementy, z których każdy jest jednowymiarową tablicą liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="ad59c-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="ad59c-108">Przed użyciem, `jaggedArray`jego elementy muszą zostać zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="ad59c-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="ad59c-109">Można zainicjować elementy w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="ad59c-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="ad59c-110">Każdy z elementów jest jednowymiarową tablicą liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ad59c-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="ad59c-111">Pierwszy element jest tablicą 5 liczb całkowitych, drugi jest tablicą 4 liczb całkowitych, a trzeci jest tablicą 2 liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="ad59c-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="ad59c-112">Możliwe jest również użycie inicjatorów do wypełnienia elementów tablicy wartościami, w którym to przypadku nie jest potrzebny rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad59c-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="ad59c-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ad59c-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="ad59c-114">Tablicę można również zainicjować przy deklaracji w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="ad59c-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="ad59c-115">Można użyć następującego skróconego formularza.</span><span class="sxs-lookup"><span data-stu-id="ad59c-115">You can use the following shorthand form.</span></span> <span data-ttu-id="ad59c-116">Należy zauważyć, że `new` nie można pominąć operatora z inicjowania elementów, ponieważ nie ma domyślnej inicjalizacji dla elementów:</span><span class="sxs-lookup"><span data-stu-id="ad59c-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="ad59c-117">Postrzępiona tablica jest tablicą tablic i dlatego jej elementy `null`są typami odwołań i są inicjowane do .</span><span class="sxs-lookup"><span data-stu-id="ad59c-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="ad59c-118">Można uzyskać dostęp do poszczególnych elementów tablicy, takich jak te przykłady:</span><span class="sxs-lookup"><span data-stu-id="ad59c-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="ad59c-119">Możliwe jest mieszanie postrzępionych i wielowymiarowych tablic.</span><span class="sxs-lookup"><span data-stu-id="ad59c-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="ad59c-120">Poniżej przedstawiono deklarację i inicjowanie jednowymiarowej tablicy postrzępionej, która zawiera trzy dwuwymiarowe elementy tablicy o różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="ad59c-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="ad59c-121">Aby uzyskać więcej informacji na temat tablic dwuwymiarowych, zobacz [Tablice wielowymiarowe](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="ad59c-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="ad59c-122">Można uzyskać dostęp do poszczególnych elementów, jak pokazano `[1,0]` w tym przykładzie, `5`który wyświetla wartość elementu pierwszej tablicy (wartość):</span><span class="sxs-lookup"><span data-stu-id="ad59c-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="ad59c-123">Metoda `Length` zwraca liczbę tablic zawartych w tablicy postrzępionej.</span><span class="sxs-lookup"><span data-stu-id="ad59c-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="ad59c-124">Na przykład przy założeniu, że zadeklarowano poprzednią tablicę, ten wiersz:</span><span class="sxs-lookup"><span data-stu-id="ad59c-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="ad59c-125">zwraca wartość 3.</span><span class="sxs-lookup"><span data-stu-id="ad59c-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad59c-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad59c-126">Example</span></span>

 <span data-ttu-id="ad59c-127">W tym przykładzie tworzy tablicy, których elementy są same tablice.</span><span class="sxs-lookup"><span data-stu-id="ad59c-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="ad59c-128">Każdy z elementów tablicy ma inny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="ad59c-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="ad59c-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad59c-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="ad59c-130">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ad59c-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ad59c-131">Tablice</span><span class="sxs-lookup"><span data-stu-id="ad59c-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="ad59c-132">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="ad59c-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="ad59c-133">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="ad59c-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
