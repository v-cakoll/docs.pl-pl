---
title: Nierówne tablic - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 9fc05c8bdebf9c1c6b613db0b6a121e06765ac00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61652003"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="52d84-102">Tablice nieregularne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="52d84-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="52d84-103">Nieregularna tablica to ta, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="52d84-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="52d84-104">Elementy tablicy nieregularnej może być inny wymiarów i rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="52d84-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="52d84-105">Nieregularna tablica jest czasami nazywane "tablicy tablic."</span><span class="sxs-lookup"><span data-stu-id="52d84-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="52d84-106">W poniższych przykładach pokazano sposób deklarowania, zainicjować i dostępu nierówne tablic.</span><span class="sxs-lookup"><span data-stu-id="52d84-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="52d84-107">Deklaracja tablicy jednowymiarowej, która ma trzy elementy, w każdej z nich jest Jednowymiarowa tablica liczb całkowitych jest następująca:</span><span class="sxs-lookup"><span data-stu-id="52d84-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="52d84-108">Przed użyciem `jaggedArray`, jego elementów musi być zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="52d84-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="52d84-109">Można zainicjować elementy następująco:</span><span class="sxs-lookup"><span data-stu-id="52d84-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="52d84-110">Każdy z elementów to Jednowymiarowa tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="52d84-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="52d84-111">Pierwszy element jest tablica liczb całkowitych, 5, drugą jest wartość tablicy liczb całkowitych 4, a trzecia będzie tablicy liczb całkowitych 2.</span><span class="sxs-lookup"><span data-stu-id="52d84-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="52d84-112">Istnieje również możliwość użycia inicjatorów do wypełniania elementów tablicy przy użyciu wartości, w którym to przypadku nie trzeba rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="52d84-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="52d84-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="52d84-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="52d84-114">Można również zainicjować tablicy po deklaracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="52d84-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="52d84-115">Można użyć następujących skrócone formy.</span><span class="sxs-lookup"><span data-stu-id="52d84-115">You can use the following shorthand form.</span></span> <span data-ttu-id="52d84-116">Należy zauważyć, że nie można pominąć `new` operator od inicjowania elementów ponieważ nie istnieje żadne inicjowanie domyślne elementy:</span><span class="sxs-lookup"><span data-stu-id="52d84-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="52d84-117">Nieregularna tablica jest tablicy tablic, a zatem jej elementy są typami odwołań i są inicjowane na `null`.</span><span class="sxs-lookup"><span data-stu-id="52d84-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="52d84-118">Aby uzyskać dostęp tablicy poszczególnych elementów, takich jak te przykłady:</span><span class="sxs-lookup"><span data-stu-id="52d84-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="52d84-119">Istnieje możliwość mieszać nieregularnej i tablice wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="52d84-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="52d84-120">Poniżej przedstawiono deklaracji i inicjowania jednowymiarowej tablicy nieregularnej, która zawiera trzy elementy dwuwymiarową tablicę o różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="52d84-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="52d84-121">Aby uzyskać więcej informacji na temat tablice dwuwymiarowe, zobacz [tablic wielowymiarowych](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="52d84-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="52d84-122">Można uzyskać dostęp do poszczególnych elementów, przedstawione w tym przykładzie, który wyświetla wartość elementu `[1,0]` tablicy pierwszy (wartość `5`):</span><span class="sxs-lookup"><span data-stu-id="52d84-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="52d84-123">Metoda `Length` zwraca liczbę tablicami, zawarte w tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="52d84-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="52d84-124">Na przykład, przy założeniu, że zostały zadeklarowane poprzednią tablicę ten wiersz:</span><span class="sxs-lookup"><span data-stu-id="52d84-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="52d84-125">Zwraca wartość 3.</span><span class="sxs-lookup"><span data-stu-id="52d84-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52d84-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="52d84-126">Example</span></span>

 <span data-ttu-id="52d84-127">W tym przykładzie tworzy tablicę, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="52d84-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="52d84-128">Każdy z elementów tablicy ma inny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="52d84-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="52d84-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52d84-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="52d84-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="52d84-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="52d84-131">Tablice</span><span class="sxs-lookup"><span data-stu-id="52d84-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="52d84-132">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="52d84-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="52d84-133">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="52d84-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
