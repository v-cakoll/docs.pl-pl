---
title: Tablice wielowymiarowe — Przewodnik programowania w języku C#
description: Tablice w języku C# mogą mieć więcej niż jeden wymiar. Ta przykładowa deklaracja tworzy dwuwymiarową tablicę czterech wierszy i dwóch kolumn.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475011"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="9b40b-104">Tablice wielowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9b40b-104">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="9b40b-105">Tablice mogą mieć więcej niż jeden wymiar.</span><span class="sxs-lookup"><span data-stu-id="9b40b-105">Arrays can have more than one dimension.</span></span> <span data-ttu-id="9b40b-106">Na przykład następująca deklaracja tworzy dwuwymiarową tablicę czterech wierszy i dwóch kolumn.</span><span class="sxs-lookup"><span data-stu-id="9b40b-106">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="9b40b-107">Poniższa deklaracja tworzy tablicę trzech wymiarów, 4, 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="9b40b-107">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="9b40b-108">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="9b40b-108">Array Initialization</span></span>

 <span data-ttu-id="9b40b-109">Tablicę można zainicjować po deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b40b-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="9b40b-110">Możesz również zainicjować tablicę bez określania rangi.</span><span class="sxs-lookup"><span data-stu-id="9b40b-110">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="9b40b-111">Jeśli zdecydujesz się zadeklarować zmienną tablicową bez inicjalizacji, musisz użyć `new` operatora, aby przypisać tablicę do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9b40b-111">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="9b40b-112">Użycie `new` jest pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b40b-112">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="9b40b-113">Poniższy przykład przypisuje wartość do określonego elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="9b40b-113">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="9b40b-114">Podobnie Poniższy przykład pobiera wartość określonego elementu tablicy i przypisuje go do zmiennej `elementValue` .</span><span class="sxs-lookup"><span data-stu-id="9b40b-114">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="9b40b-115">Poniższy przykład kodu inicjuje elementy tablicy do wartości domyślnych (z wyjątkiem tablic nieregularnych).</span><span class="sxs-lookup"><span data-stu-id="9b40b-115">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="9b40b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b40b-116">See also</span></span>

- [<span data-ttu-id="9b40b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b40b-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9b40b-118">Tablice</span><span class="sxs-lookup"><span data-stu-id="9b40b-118">Arrays</span></span>](./index.md)
- [<span data-ttu-id="9b40b-119">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="9b40b-119">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="9b40b-120">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="9b40b-120">Jagged Arrays</span></span>](./jagged-arrays.md)
