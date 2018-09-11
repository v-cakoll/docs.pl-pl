---
title: Tablice wielowymiarowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a1d7a0a014c330682316e869f6727082fa3b31ef
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266021"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="fe5f6-102">Tablice wielowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fe5f6-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="fe5f6-103">Tablice mogą mieć więcej niż jeden wymiar.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="fe5f6-104">Na przykład następująca deklaracja tworzy dwuwymiarową tablicę cztery wiersze i dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 <span data-ttu-id="fe5f6-105">Następująca deklaracja tworzy tablicę o trzech wymiarów, 4, 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="fe5f6-106">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="fe5f6-106">Array Initialization</span></span>

 <span data-ttu-id="fe5f6-107">Można zainicjować tablicy po zgłoszeniu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 <span data-ttu-id="fe5f6-108">Możesz również zainicjować tablicy bez określania rangi.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 <span data-ttu-id="fe5f6-109">Jeśli zdecydujesz się zadeklarować zmiennej tablicy bez inicjowania, należy użyć `new` operatora, aby przypisać tablicę do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="fe5f6-110">Korzystanie z `new` przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 <span data-ttu-id="fe5f6-111">Poniższy przykład przypisuje wartość do elementu określonej tablicy.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 <span data-ttu-id="fe5f6-112">Podobnie poniższy przykład pobiera wartość elementu określonego tablicy i przypisuje go do zmiennej `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="fe5f6-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 <span data-ttu-id="fe5f6-113">Poniższy przykład kodu inicjuje elementy tablicy, do wartości domyślnych (z wyjątkiem tablic nieregularnych).</span><span class="sxs-lookup"><span data-stu-id="fe5f6-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fe5f6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe5f6-114">See Also</span></span>

- [<span data-ttu-id="fe5f6-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fe5f6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fe5f6-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="fe5f6-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="fe5f6-117">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="fe5f6-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="fe5f6-118">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="fe5f6-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
