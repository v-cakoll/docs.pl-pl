---
title: Przekazywanie tablic jako argumentów — C# Przewodnik programowania
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 2e53008910a9062ada25680eb4b8e54a225fd226
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705694"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="ad9a8-102">Przekazywanie tablic jako argumentów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="ad9a8-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="ad9a8-103">Tablice mogą być przekazane jako argumenty do parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="ad9a8-104">Ponieważ tablice są typami odwołań, Metoda może zmienić wartość elementów.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="ad9a8-105">Przekazywanie tablic jednowymiarowych jako argumentów</span><span class="sxs-lookup"><span data-stu-id="ad9a8-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="ad9a8-106">Można przekazać zainicjowaną tablicę jednowymiarową do metody.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="ad9a8-107">Na przykład poniższa instrukcja wysyła tablicę do metody Print.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="ad9a8-108">Poniższy kod przedstawia częściową implementację metody Print.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="ad9a8-109">Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="ad9a8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad9a8-110">Example</span></span>

<span data-ttu-id="ad9a8-111">W poniższym przykładzie tablica ciągów jest inicjowana i przenoszona jako argument do metody `DisplayArray` dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="ad9a8-112">Metoda wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-112">The method displays the elements of the array.</span></span> <span data-ttu-id="ad9a8-113">Następnie Metoda `ChangeArray` odwraca elementy tablicy, a następnie Metoda `ChangeArrayElements` modyfikuje pierwsze trzy elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="ad9a8-114">Po powrocie każdej metody Metoda `DisplayArray` pokazuje, że przekazywanie tablicy przez wartość nie zapobiega zmianom elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="ad9a8-115">Przekazywanie tablic wielowymiarowych jako argumentów</span><span class="sxs-lookup"><span data-stu-id="ad9a8-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="ad9a8-116">Można przekazać zainicjowaną tablicę wielowymiarową do metody w taki sam sposób, w jaki przeszedł tablicę jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="ad9a8-117">Poniższy kod przedstawia częściową deklarację metody Print, która akceptuje tablicę dwuwymiarową jako argument.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="ad9a8-118">Można zainicjować i przekazać nową tablicę w jednym kroku, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ad9a8-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="ad9a8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad9a8-119">Example</span></span>

<span data-ttu-id="ad9a8-120">W poniższym przykładzie jest inicjowana Dwuwymiarowa tablica liczb całkowitych, która jest przenoszona do metody `Print2DArray`.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="ad9a8-121">Metoda wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="ad9a8-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="ad9a8-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad9a8-122">See also</span></span>

- [<span data-ttu-id="ad9a8-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ad9a8-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ad9a8-124">Tablice</span><span class="sxs-lookup"><span data-stu-id="ad9a8-124">Arrays</span></span>](index.md)
- [<span data-ttu-id="ad9a8-125">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="ad9a8-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="ad9a8-126">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="ad9a8-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="ad9a8-127">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="ad9a8-127">Jagged Arrays</span></span>](jagged-arrays.md)
