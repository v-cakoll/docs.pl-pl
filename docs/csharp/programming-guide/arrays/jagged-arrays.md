---
title: Nierówne tablic - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: f517a9a6d6e10f04df70729fb9e641c1f955f28a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237863"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="0902e-102">Tablice nieregularne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0902e-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="0902e-103">Nieregularna tablica to ta, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="0902e-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="0902e-104">Elementy tablicy nieregularnej może być inny wymiarów i rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="0902e-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="0902e-105">Nieregularna tablica jest czasami nazywane "tablicy tablic."</span><span class="sxs-lookup"><span data-stu-id="0902e-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="0902e-106">W poniższych przykładach pokazano sposób deklarowania, zainicjować i dostępu nierówne tablic.</span><span class="sxs-lookup"><span data-stu-id="0902e-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="0902e-107">Deklaracja tablicy jednowymiarowej, która ma trzy elementy, w każdej z nich jest Jednowymiarowa tablica liczb całkowitych jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0902e-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 <span data-ttu-id="0902e-108">Przed użyciem `jaggedArray`, jego elementów musi być zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="0902e-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="0902e-109">Można zainicjować elementy następująco:</span><span class="sxs-lookup"><span data-stu-id="0902e-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 <span data-ttu-id="0902e-110">Każdy z elementów to Jednowymiarowa tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="0902e-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="0902e-111">Pierwszy element jest tablica liczb całkowitych, 5, drugą jest wartość tablicy liczb całkowitych 4, a trzecia będzie tablicy liczb całkowitych 2.</span><span class="sxs-lookup"><span data-stu-id="0902e-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="0902e-112">Istnieje również możliwość użycia inicjatorów do wypełniania elementów tablicy przy użyciu wartości, w którym to przypadku nie trzeba rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="0902e-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="0902e-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0902e-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 <span data-ttu-id="0902e-114">Można również zainicjować tablicy po deklaracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0902e-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 <span data-ttu-id="0902e-115">Można użyć następujących skrócone formy.</span><span class="sxs-lookup"><span data-stu-id="0902e-115">You can use the following shorthand form.</span></span> <span data-ttu-id="0902e-116">Należy zauważyć, że nie można pominąć `new` operator od inicjowania elementów ponieważ nie istnieje żadne inicjowanie domyślne elementy:</span><span class="sxs-lookup"><span data-stu-id="0902e-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 <span data-ttu-id="0902e-117">Nieregularna tablica jest tablicy tablic, a zatem jej elementy są typami odwołań i są inicjowane na `null`.</span><span class="sxs-lookup"><span data-stu-id="0902e-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="0902e-118">Aby uzyskać dostęp tablicy poszczególnych elementów, takich jak te przykłady:</span><span class="sxs-lookup"><span data-stu-id="0902e-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 <span data-ttu-id="0902e-119">Istnieje możliwość mieszać nieregularnej i tablice wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="0902e-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="0902e-120">Poniżej przedstawiono deklaracji i inicjowania jednowymiarowej tablicy nieregularnej, która zawiera trzy elementy dwuwymiarową tablicę o różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="0902e-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="0902e-121">Aby uzyskać więcej informacji na temat tablice dwuwymiarowe, zobacz [tablic wielowymiarowych](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="0902e-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 <span data-ttu-id="0902e-122">Można uzyskać dostęp do poszczególnych elementów, przedstawione w tym przykładzie, który wyświetla wartość elementu `[1,0]` tablicy pierwszy (wartość `5`):</span><span class="sxs-lookup"><span data-stu-id="0902e-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 <span data-ttu-id="0902e-123">Metoda `Length` zwraca liczbę tablicami, zawarte w tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="0902e-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="0902e-124">Na przykład, przy założeniu, że zostały zadeklarowane poprzednią tablicę ten wiersz:</span><span class="sxs-lookup"><span data-stu-id="0902e-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 <span data-ttu-id="0902e-125">Zwraca wartość 3.</span><span class="sxs-lookup"><span data-stu-id="0902e-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0902e-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="0902e-126">Example</span></span>

 <span data-ttu-id="0902e-127">W tym przykładzie tworzy tablicę, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="0902e-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="0902e-128">Każdy z elementów tablicy ma inny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="0902e-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0902e-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0902e-129">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="0902e-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0902e-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0902e-131">Tablice</span><span class="sxs-lookup"><span data-stu-id="0902e-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="0902e-132">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="0902e-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="0902e-133">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="0902e-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
