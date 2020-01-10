---
title: Tablice nieregularne — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705707"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="8f64b-102">Tablice nieregularne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8f64b-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="8f64b-103">Nieregularna tablica to ta, której elementy są tablicami.</span><span class="sxs-lookup"><span data-stu-id="8f64b-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="8f64b-104">Elementy tablicy nieregularnej mogą mieć różne wymiary i rozmiary.</span><span class="sxs-lookup"><span data-stu-id="8f64b-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="8f64b-105">Tablica nieregularna jest czasami nazywana "tablicą tablic."</span><span class="sxs-lookup"><span data-stu-id="8f64b-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="8f64b-106">W poniższych przykładach pokazano, jak deklarować, inicjować i uzyskiwać dostęp do tablic nieregularnych.</span><span class="sxs-lookup"><span data-stu-id="8f64b-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="8f64b-107">Poniżej znajduje się deklaracja jednowymiarowej tablicy, która składa się z trzech elementów, z których każdy jest jednowymiarową tablicą liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="8f64b-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 <span data-ttu-id="8f64b-108">Aby można było używać `jaggedArray`, jego elementy muszą zostać zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="8f64b-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="8f64b-109">Można inicjować następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="8f64b-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 <span data-ttu-id="8f64b-110">Każdy element jest jednowymiarową tablicą liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="8f64b-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="8f64b-111">Pierwszy element jest tablicą 5 liczb całkowitych, a druga jest tablicą 4 liczb całkowitych, a trzecia jest tablicą 2 liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="8f64b-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="8f64b-112">Istnieje również możliwość użycia inicjatorów do wypełnienia elementów tablicy wartościami, w tym przypadku nie jest potrzebny rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="8f64b-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="8f64b-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8f64b-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 <span data-ttu-id="8f64b-114">Możesz również zainicjować tablicę w przypadku deklaracji takich jak:</span><span class="sxs-lookup"><span data-stu-id="8f64b-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 <span data-ttu-id="8f64b-115">Możesz użyć następującej formy skróconej.</span><span class="sxs-lookup"><span data-stu-id="8f64b-115">You can use the following shorthand form.</span></span> <span data-ttu-id="8f64b-116">Należy zauważyć, że nie można pominąć operatora `new` z inicjowania elementów, ponieważ nie ma domyślnego inicjowania dla elementów:</span><span class="sxs-lookup"><span data-stu-id="8f64b-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 <span data-ttu-id="8f64b-117">Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null`.</span><span class="sxs-lookup"><span data-stu-id="8f64b-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="8f64b-118">Można uzyskać dostęp do poszczególnych elementów tablicy, takich jak następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="8f64b-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 <span data-ttu-id="8f64b-119">Możliwe jest mieszanie tablic nieregularnych i wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="8f64b-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="8f64b-120">Poniżej znajduje się deklaracja i Inicjalizacja jednowymiarowej tablicy nieregularnej, która zawiera 3 2-wymiarowe elementy tablicy o różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="8f64b-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="8f64b-121">Aby uzyskać więcej informacji na temat tablic dwuwymiarowych, zobacz [wielowymiarowe tablice](./multidimensional-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8f64b-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 <span data-ttu-id="8f64b-122">Można uzyskać dostęp do poszczególnych elementów, jak pokazano w tym przykładzie, który wyświetla wartość `[1,0]` elementu pierwszej tablicy (wartość `5`):</span><span class="sxs-lookup"><span data-stu-id="8f64b-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 <span data-ttu-id="8f64b-123">Metoda `Length` zwraca liczbę tablic zawartych w tablicy nieregularnej.</span><span class="sxs-lookup"><span data-stu-id="8f64b-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="8f64b-124">Na przykład przy założeniu, że zadeklarowano poprzednią tablicę, ten wiersz:</span><span class="sxs-lookup"><span data-stu-id="8f64b-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 <span data-ttu-id="8f64b-125">Zwraca wartość 3.</span><span class="sxs-lookup"><span data-stu-id="8f64b-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f64b-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f64b-126">Example</span></span>

 <span data-ttu-id="8f64b-127">Ten przykład kompiluje tablicę, której elementy same są tablicami.</span><span class="sxs-lookup"><span data-stu-id="8f64b-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="8f64b-128">Każdy jeden z elementów tablicy ma inny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="8f64b-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a><span data-ttu-id="8f64b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f64b-129">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="8f64b-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8f64b-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f64b-131">Tablice</span><span class="sxs-lookup"><span data-stu-id="8f64b-131">Arrays</span></span>](./index.md)
- [<span data-ttu-id="8f64b-132">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="8f64b-132">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="8f64b-133">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="8f64b-133">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
