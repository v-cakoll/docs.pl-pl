---
title: Tablice nieregularne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: c1825e1a731c40a5945060f8085bd612b5d62008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297371"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="6d051-102">Tablice nieregularne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6d051-102">Jagged Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="6d051-103">Nieregularna tablica to ta, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="6d051-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="6d051-104">Elementy tablicy nieregularnej mogą być różne wymiary i rozmiary.</span><span class="sxs-lookup"><span data-stu-id="6d051-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="6d051-105">Tablicy nieregularnej jest czasami nazywany "tablicy tablic."</span><span class="sxs-lookup"><span data-stu-id="6d051-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="6d051-106">Poniższe przykłady pokazują, jak zadeklarować, zainicjować i tablice nieregularne dostępu.</span><span class="sxs-lookup"><span data-stu-id="6d051-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="6d051-107">Poniżej przedstawiono deklaracji jednowymiarowej tablicy, która ma trzy elementy, z których każdy jest tablicy jednowymiarowej liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="6d051-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 <span data-ttu-id="6d051-108">Przed użyciem `jaggedArray`, jego elementy muszą zostać zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="6d051-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="6d051-109">Można zainicjować elementy następująco:</span><span class="sxs-lookup"><span data-stu-id="6d051-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 <span data-ttu-id="6d051-110">Każdy z elementów jest tablicy jednowymiarowej liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="6d051-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="6d051-111">Pierwszy element jest tablica liczb całkowitych 5, drugi jest tablica liczb całkowitych 4, a trzeci jest tablica liczb całkowitych 2.</span><span class="sxs-lookup"><span data-stu-id="6d051-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="6d051-112">Istnieje również możliwość użycia inicjatory umożliwia wypełnienie elementów tablicy wartości, w którym to przypadku nie trzeba rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="6d051-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="6d051-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d051-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 <span data-ttu-id="6d051-114">Można również zainicjować tablicy po deklaracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6d051-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 <span data-ttu-id="6d051-115">Można użyć w następującej formie skrótu.</span><span class="sxs-lookup"><span data-stu-id="6d051-115">You can use the following shorthand form.</span></span> <span data-ttu-id="6d051-116">Należy zauważyć, że nie można pominąć `new` operatora z inicjowania elementów ponieważ nie istnieje żadne inicjowanie domyślnych elementów:</span><span class="sxs-lookup"><span data-stu-id="6d051-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 <span data-ttu-id="6d051-117">Nieregularna tablica jest tablicy tablic, a w związku z tym jej elementy są typy referencyjne i są inicjowane na `null`.</span><span class="sxs-lookup"><span data-stu-id="6d051-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="6d051-118">Aby dostęp do tablicy poszczególnych elementów, takich jak te przykłady:</span><span class="sxs-lookup"><span data-stu-id="6d051-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 <span data-ttu-id="6d051-119">Istnieje możliwość mieszać Tablice nieregularne i wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="6d051-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="6d051-120">Poniżej znajduje się deklaracji i inicjowania jednowymiarowej tablicy nieregularnej, który zawiera trzy elementy tablicą dwuwymiarową o różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="6d051-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="6d051-121">Aby uzyskać więcej informacji dotyczących dwuwymiarowa tablic, zobacz [tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="6d051-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 <span data-ttu-id="6d051-122">Można uzyskać dostępu do poszczególne elementy, jak pokazano w przykładzie wyświetla wartość elementu `[1,0]` pierwszy tablicy (wartość `5`):</span><span class="sxs-lookup"><span data-stu-id="6d051-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 <span data-ttu-id="6d051-123">Metoda `Length` zwraca liczbę tablice zawartych w tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="6d051-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="6d051-124">Na przykład przy założeniu, że zadeklarowaniu poprzedniej macierzy, ten wiersz:</span><span class="sxs-lookup"><span data-stu-id="6d051-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 <span data-ttu-id="6d051-125">Zwraca wartość 3.</span><span class="sxs-lookup"><span data-stu-id="6d051-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d051-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d051-126">Example</span></span>  
 <span data-ttu-id="6d051-127">W tym przykładzie kompilacje tablicy, której elementy są tablic.</span><span class="sxs-lookup"><span data-stu-id="6d051-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="6d051-128">Każda z nich elementów tablicy ma inny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="6d051-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d051-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d051-129">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="6d051-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6d051-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d051-131">Tablice</span><span class="sxs-lookup"><span data-stu-id="6d051-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="6d051-132">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="6d051-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="6d051-133">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="6d051-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
