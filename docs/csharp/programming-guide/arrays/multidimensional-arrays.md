---
title: Tablice wielowymiarowe — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 63b8729a14e4c309e85a588c5cddc692fb6a6fad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597409"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="3a772-102">Tablice wielowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3a772-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="3a772-103">Tablice mogą mieć więcej niż jeden wymiar.</span><span class="sxs-lookup"><span data-stu-id="3a772-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="3a772-104">Na przykład następująca deklaracja tworzy dwuwymiarową tablicę czterech wierszy i dwóch kolumn.</span><span class="sxs-lookup"><span data-stu-id="3a772-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="3a772-105">Poniższa deklaracja tworzy tablicę trzech wymiarów, 4, 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="3a772-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="3a772-106">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="3a772-106">Array Initialization</span></span>

 <span data-ttu-id="3a772-107">Tablicę można zainicjować po deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3a772-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="3a772-108">Można również zainicjować tablicę bez określania rangi.</span><span class="sxs-lookup"><span data-stu-id="3a772-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="3a772-109">Jeśli zdecydujesz się zadeklarować zmienną tablicową bez inicjalizacji, musisz użyć operatora `new` , aby przypisać tablicę do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3a772-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="3a772-110">Użycie `new` jest pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3a772-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="3a772-111">Poniższy przykład przypisuje wartość do określonego elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="3a772-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="3a772-112">Podobnie Poniższy przykład pobiera wartość określonego elementu tablicy i przypisuje go do zmiennej `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="3a772-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="3a772-113">Poniższy przykład kodu inicjuje elementy tablicy do wartości domyślnych (z wyjątkiem tablic nieregularnych).</span><span class="sxs-lookup"><span data-stu-id="3a772-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="3a772-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a772-114">See also</span></span>

- [<span data-ttu-id="3a772-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3a772-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3a772-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="3a772-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="3a772-117">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="3a772-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="3a772-118">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="3a772-118">Jagged Arrays</span></span>](./jagged-arrays.md)
