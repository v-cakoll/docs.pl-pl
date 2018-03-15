---
title: "Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f76f63aee0100c6af6bde73c8543b4e7136b1954
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="b7764-102">Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b7764-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="b7764-103">Takich jak wszystkie [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów `out` parametr typu tablicy musi być przypisany, zanim zostanie on użyty; oznacza to, musi być przypisany przez funkcję wywołującą.</span><span class="sxs-lookup"><span data-stu-id="b7764-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="b7764-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b7764-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="b7764-105">Takich jak wszystkie [ref](../../../csharp/language-reference/keywords/ref.md) parametry, `ref` parametr typu tablicy musi być ostatecznie przypisany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="b7764-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="b7764-106">Dlatego też nie musi być zdecydowanie przypisywany przez obiekt wywoływany.</span><span class="sxs-lookup"><span data-stu-id="b7764-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="b7764-107">A `ref` parametr typu tablicy mogą ulec zmianie w wyniku wywołania.</span><span class="sxs-lookup"><span data-stu-id="b7764-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="b7764-108">Na przykład można przypisać tablicy [null](../../../csharp/language-reference/keywords/null.md) wartość lub mogą być inicjowane do innej tablicy.</span><span class="sxs-lookup"><span data-stu-id="b7764-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="b7764-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b7764-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="b7764-110">W poniższych dwóch przykładach pokazano różnicę między `out` i `ref` w przekazywanie tablic metod.</span><span class="sxs-lookup"><span data-stu-id="b7764-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7764-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7764-111">Example</span></span>  
 <span data-ttu-id="b7764-112">W tym przykładzie tablicy `theArray` jest zadeklarowana w wywołującego ( `Main` — metoda) i została zainicjowana w `FillArray` metody.</span><span class="sxs-lookup"><span data-stu-id="b7764-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="b7764-113">Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b7764-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="b7764-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7764-114">Example</span></span>  
 <span data-ttu-id="b7764-115">W tym przykładzie tablicy `theArray` został zainicjowany w wywołującego ( `Main` — metoda) i przekazywane do `FillArray` metody przy użyciu `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="b7764-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="b7764-116">Niektóre elementy tablicy są aktualizowane w `FillArray` metody.</span><span class="sxs-lookup"><span data-stu-id="b7764-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="b7764-117">Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b7764-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b7764-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7764-118">See Also</span></span>  
 [<span data-ttu-id="b7764-119">ref</span><span class="sxs-lookup"><span data-stu-id="b7764-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="b7764-120">out — modyfikator parametrów</span><span class="sxs-lookup"><span data-stu-id="b7764-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [<span data-ttu-id="b7764-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b7764-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b7764-122">Tablice</span><span class="sxs-lookup"><span data-stu-id="b7764-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="b7764-123">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="b7764-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="b7764-124">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="b7764-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="b7764-125">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="b7764-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
