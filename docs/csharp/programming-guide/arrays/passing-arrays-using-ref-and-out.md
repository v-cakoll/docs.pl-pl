---
title: Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
ms.openlocfilehash: 8da3bf9f8eede72a7bc3cf8380eab66ca2b56e86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526768"
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="fcdba-102">Przekazywanie tablic za pomocą ref i out (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fcdba-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>

<span data-ttu-id="fcdba-103">Podobnie jak wszystkie [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów, `out` parametr typu tablicowego musi być przypisany, zanim zostaną one użyte; oznacza to, musi zostać przypisany przez obiekt wywoływany.</span><span class="sxs-lookup"><span data-stu-id="fcdba-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="fcdba-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fcdba-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="fcdba-105">Podobnie jak wszystkie [ref](../../../csharp/language-reference/keywords/ref.md) parametrów, `ref` parametr typu tablicowego musi zostać zdecydowanie przypisany przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="fcdba-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="fcdba-106">Dlatego też nie musi być zdecydowanie przypisywany przez obiekt wywoływany.</span><span class="sxs-lookup"><span data-stu-id="fcdba-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="fcdba-107">A `ref` parametr typu tablicowego może zostać zmieniony w wyniku wywołania.</span><span class="sxs-lookup"><span data-stu-id="fcdba-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="fcdba-108">Na przykład tablicy może zostać przypisana [null](../../../csharp/language-reference/keywords/null.md) wartość albo może zostać zainicjowana do innej tablicy.</span><span class="sxs-lookup"><span data-stu-id="fcdba-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="fcdba-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fcdba-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="fcdba-110">Dwa poniższe przykłady pokazują różnicę między `out` i `ref` , gdy używane do przekazywania tablic do metod.</span><span class="sxs-lookup"><span data-stu-id="fcdba-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcdba-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcdba-111">Example</span></span>

 <span data-ttu-id="fcdba-112">W tym przykładzie tablica `theArray` jest zadeklarowany w obiekcie wywołującym ( `Main` metoda) i inicjowana w `FillArray` metody.</span><span class="sxs-lookup"><span data-stu-id="fcdba-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="fcdba-113">Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="fcdba-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]

## <a name="example"></a><span data-ttu-id="fcdba-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcdba-114">Example</span></span>

 <span data-ttu-id="fcdba-115">W tym przykładzie tablica `theArray` jest inicjowany w obiekcie wywołującym ( `Main` metoda) i przekazywane do `FillArray` metody, używając `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="fcdba-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="fcdba-116">Niektóre elementy tablicy są aktualizowane w `FillArray` metody.</span><span class="sxs-lookup"><span data-stu-id="fcdba-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="fcdba-117">Następnie elementy tablicy są zwracane do obiektu wywołującego i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="fcdba-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fcdba-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcdba-118">See Also</span></span>

- [<span data-ttu-id="fcdba-119">ref</span><span class="sxs-lookup"><span data-stu-id="fcdba-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
- [<span data-ttu-id="fcdba-120">out — modyfikator parametrów</span><span class="sxs-lookup"><span data-stu-id="fcdba-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
- [<span data-ttu-id="fcdba-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fcdba-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fcdba-122">Tablice</span><span class="sxs-lookup"><span data-stu-id="fcdba-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="fcdba-123">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="fcdba-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="fcdba-124">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="fcdba-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="fcdba-125">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="fcdba-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
