---
title: Tablice wielowymiarowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: df9063d0616b72ad15c9c48fa4459a6dc98b77c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972615"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="f651b-102">Tablice wielowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f651b-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="f651b-103">Tablice mogą mieć więcej niż jeden wymiar.</span><span class="sxs-lookup"><span data-stu-id="f651b-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="f651b-104">Na przykład następująca deklaracja tworzy dwuwymiarową tablicę cztery wiersze i dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="f651b-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="f651b-105">Następująca deklaracja tworzy tablicę o trzech wymiarów, 4, 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="f651b-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="f651b-106">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="f651b-106">Array Initialization</span></span>

 <span data-ttu-id="f651b-107">Można zainicjować tablicy po zgłoszeniu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f651b-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="f651b-108">Możesz również zainicjować tablicy bez określania rangi.</span><span class="sxs-lookup"><span data-stu-id="f651b-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="f651b-109">Jeśli zdecydujesz się zadeklarować zmiennej tablicy bez inicjowania, należy użyć `new` operatora, aby przypisać tablicę do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f651b-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="f651b-110">Korzystanie z `new` przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f651b-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="f651b-111">Poniższy przykład przypisuje wartość do elementu określonej tablicy.</span><span class="sxs-lookup"><span data-stu-id="f651b-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="f651b-112">Podobnie poniższy przykład pobiera wartość elementu określonego tablicy i przypisuje go do zmiennej `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="f651b-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="f651b-113">Poniższy przykład kodu inicjuje elementy tablicy, do wartości domyślnych (z wyjątkiem tablic nieregularnych).</span><span class="sxs-lookup"><span data-stu-id="f651b-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f651b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f651b-114">See also</span></span>

- [<span data-ttu-id="f651b-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f651b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f651b-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="f651b-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="f651b-117">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="f651b-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="f651b-118">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="f651b-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
