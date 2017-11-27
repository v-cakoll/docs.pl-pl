---
title: "Przekazywanie tablic jako argumenty (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="5bdd8-102">Przekazywanie tablic jako argumenty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5bdd8-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="5bdd8-103">Tablice mogą być przekazywane jako argumenty do parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="5bdd8-104">Ponieważ tablice typów referencyjnych, metoda można zmienić wartości elementów.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="5bdd8-105">Tablice jednowymiarowe przekazywanie jako argumentów</span><span class="sxs-lookup"><span data-stu-id="5bdd8-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="5bdd8-106">Zainicjowanej tablicy jednowymiarowej można przekazać do metody.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="5bdd8-107">Na przykład następująca instrukcja wysyła tablicy do metody drukowania.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="5bdd8-108">Poniższy kod przedstawia częściowa implementacja metody drukowania.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="5bdd8-109">Możesz zainicjować i przekazać nowej tablicy w jednym kroku, jak to pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="5bdd8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bdd8-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5bdd8-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5bdd8-111">Description</span></span>  
 <span data-ttu-id="5bdd8-112">W poniższym przykładzie zostanie zainicjowana i przekazany jako argument tablicy ciągów `PrintArray` metody dla ciągów.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="5bdd8-113">Metoda Wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-113">The method displays the elements of the array.</span></span> <span data-ttu-id="5bdd8-114">Następnie metody `ChangeArray` i `ChangeArrayElement` są nazywane wykazać, że wysyłania przez wartość argumentu tablicy nie uniemożliwia zmiany do elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5bdd8-115">Kod</span><span class="sxs-lookup"><span data-stu-id="5bdd8-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="5bdd8-116">Przekazywanie jako argumentów tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="5bdd8-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="5bdd8-117">Zainicjowanej tablicy wielowymiarowej są przekazywane do metody w taki sam sposób, który jest przekazywany jest tablicą jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="5bdd8-118">Poniższy kod przedstawia częściowa deklaracja metody wydruku, która akceptuje jest tablicą dwuwymiarową jako jej argument.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="5bdd8-119">Możesz zainicjować i przekazać nowej tablicy w jednym kroku, jak to pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="5bdd8-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bdd8-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5bdd8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5bdd8-121">Description</span></span>  
 <span data-ttu-id="5bdd8-122">W poniższym przykładzie jest tablicą dwuwymiarową liczb całkowitych zostanie zainicjowana i przekazane do `Print2DArray` metody.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="5bdd8-123">Metoda Wyświetla elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="5bdd8-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5bdd8-124">Kod</span><span class="sxs-lookup"><span data-stu-id="5bdd8-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5bdd8-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bdd8-125">See Also</span></span>  
 [<span data-ttu-id="5bdd8-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5bdd8-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5bdd8-127">Tablice</span><span class="sxs-lookup"><span data-stu-id="5bdd8-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="5bdd8-128">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="5bdd8-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="5bdd8-129">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="5bdd8-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="5bdd8-130">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="5bdd8-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
