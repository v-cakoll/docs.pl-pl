---
title: Przekazywanie tablic jako argumentów — Przewodnik programowania w języku C#
description: Tablice w języku C# mogą być przekazane jako argumenty do parametrów metody. Ponieważ tablice są typami odwołań, Metoda może zmienić wartość elementów.
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 68f174421e56e2cf082fe670f93c4f6627d7c17b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474634"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="24fb6-104">Przekazywanie tablic jako argumentów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="24fb6-104">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="24fb6-105">Tablice mogą być przekazane jako argumenty do parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="24fb6-105">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="24fb6-106">Ponieważ tablice są typami odwołań, Metoda może zmienić wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="24fb6-106">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="24fb6-107">Przekazywanie tablic jednowymiarowych jako argumentów</span><span class="sxs-lookup"><span data-stu-id="24fb6-107">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="24fb6-108">Można przekazać zainicjowaną tablicę jednowymiarową do metody.</span><span class="sxs-lookup"><span data-stu-id="24fb6-108">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="24fb6-109">Na przykład poniższa instrukcja wysyła tablicę do metody Print.</span><span class="sxs-lookup"><span data-stu-id="24fb6-109">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="24fb6-110">Poniższy kod przedstawia częściową implementację metody Print.</span><span class="sxs-lookup"><span data-stu-id="24fb6-110">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="24fb6-111">Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="24fb6-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="24fb6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="24fb6-112">Example</span></span>

<span data-ttu-id="24fb6-113">W poniższym przykładzie tablica ciągów jest inicjowana i przenoszona jako argument do `DisplayArray` metody dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="24fb6-113">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="24fb6-114">Metoda wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="24fb6-114">The method displays the elements of the array.</span></span> <span data-ttu-id="24fb6-115">`ChangeArray`Następnie Metoda odwraca elementy tablicy, a następnie `ChangeArrayElements` modyfikuje pierwsze trzy elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="24fb6-115">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="24fb6-116">Po powrocie każdej metody `DisplayArray` Metoda pokazuje, że przekazywanie tablicy przez wartość nie zapobiega zmianom elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="24fb6-116">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="24fb6-117">Przekazywanie tablic wielowymiarowych jako argumentów</span><span class="sxs-lookup"><span data-stu-id="24fb6-117">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="24fb6-118">Można przekazać zainicjowaną tablicę wielowymiarową do metody w taki sam sposób, w jaki przeszedł tablicę jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="24fb6-118">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="24fb6-119">Poniższy kod przedstawia częściową deklarację metody Print, która akceptuje tablicę dwuwymiarową jako argument.</span><span class="sxs-lookup"><span data-stu-id="24fb6-119">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="24fb6-120">Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="24fb6-120">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="24fb6-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="24fb6-121">Example</span></span>

<span data-ttu-id="24fb6-122">W poniższym przykładzie jest inicjowana Dwuwymiarowa tablica liczb całkowitych, która jest przenoszona do `Print2DArray` metody.</span><span class="sxs-lookup"><span data-stu-id="24fb6-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="24fb6-123">Metoda wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="24fb6-123">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="24fb6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24fb6-124">See also</span></span>

- [<span data-ttu-id="24fb6-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="24fb6-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="24fb6-126">Tablice</span><span class="sxs-lookup"><span data-stu-id="24fb6-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="24fb6-127">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="24fb6-127">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="24fb6-128">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="24fb6-128">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="24fb6-129">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="24fb6-129">Jagged Arrays</span></span>](jagged-arrays.md)
