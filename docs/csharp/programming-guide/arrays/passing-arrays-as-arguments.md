---
title: Przekazywanie tablic jako argumenty (C# Programming Guide)
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: b2e6c0134af3b5814e9c9321e1486820311aa5c6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042429"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="d3b23-102">Przekazywanie tablic jako argumenty (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d3b23-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="d3b23-103">Tablice mogą być przekazywane jako argumenty do parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="d3b23-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="d3b23-104">Ponieważ tablice są typami odwołań, metody można zmienić wartości elementów.</span><span class="sxs-lookup"><span data-stu-id="d3b23-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="d3b23-105">Tablice jednowymiarowe przekazywanie jako argumentów</span><span class="sxs-lookup"><span data-stu-id="d3b23-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="d3b23-106">Można przekazać zainicjowanej tablicy jednowymiarowej, do metody.</span><span class="sxs-lookup"><span data-stu-id="d3b23-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="d3b23-107">Na przykład następująca instrukcja wysyła tablicę do drukowania metody.</span><span class="sxs-lookup"><span data-stu-id="d3b23-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="d3b23-108">Poniższy kod przedstawia częściową implementację metody drukowania.</span><span class="sxs-lookup"><span data-stu-id="d3b23-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="d3b23-109">Możesz zainicjować i przekazywać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d3b23-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="d3b23-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3b23-110">Example</span></span>

<span data-ttu-id="d3b23-111">W poniższym przykładzie tablica ciągów zostanie zainicjowana i przekazywany jako argument do `DisplayArray` metody dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="d3b23-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="d3b23-112">Metoda Wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="d3b23-112">The method displays the elements of the array.</span></span> <span data-ttu-id="d3b23-113">Następnie `ChangeArray` metoda odwraca elementów tablicy, a następnie `ChangeArrayElements` metoda modyfikuje pierwsze trzy elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="d3b23-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="d3b23-114">Po powrocie każdą metodę, `DisplayArray` metoda ma pokazać, że przekazywanie tablicę według wartości nie uniemożliwiają zmiany do elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="d3b23-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="d3b23-115">Przekazywanie tablic wielowymiarowych jako argumentów</span><span class="sxs-lookup"><span data-stu-id="d3b23-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="d3b23-116">Zainicjowanej tablicy wielowymiarowej są przekazywane do metody w taki sam sposób, jak przekazać tablicę jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="d3b23-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="d3b23-117">Poniższy kod przedstawia częściowa deklaracja metody drukowania, która akceptuje dwuwymiarową tablicę jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="d3b23-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="d3b23-118">Możesz zainicjować i przekazywać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d3b23-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="d3b23-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3b23-119">Example</span></span>

<span data-ttu-id="d3b23-120">W poniższym przykładzie zostanie zainicjowana i przekazywane do tablicę dwuwymiarową liczb całkowitych `Print2DArray` metody.</span><span class="sxs-lookup"><span data-stu-id="d3b23-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="d3b23-121">Metoda Wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="d3b23-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="d3b23-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3b23-122">See also</span></span>

- [<span data-ttu-id="d3b23-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d3b23-123">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="d3b23-124">Tablice</span><span class="sxs-lookup"><span data-stu-id="d3b23-124">Arrays</span></span>](index.md)  
- [<span data-ttu-id="d3b23-125">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="d3b23-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="d3b23-126">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="d3b23-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="d3b23-127">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="d3b23-127">Jagged Arrays</span></span>](jagged-arrays.md)  