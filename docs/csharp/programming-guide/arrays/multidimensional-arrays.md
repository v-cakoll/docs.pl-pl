---
title: Tablice wielowymiarowe — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715038"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="66469-102">Tablice wielowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="66469-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="66469-103">Tablice mogą mieć więcej niż jeden wymiar.</span><span class="sxs-lookup"><span data-stu-id="66469-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="66469-104">Na przykład następująca deklaracja tworzy dwuwymiarową tablicę czterech wierszy i dwóch kolumn.</span><span class="sxs-lookup"><span data-stu-id="66469-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="66469-105">Następująca deklaracja tworzy tablicę trzech wymiarów, 4, 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="66469-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="66469-106">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="66469-106">Array Initialization</span></span>

 <span data-ttu-id="66469-107">Tablicę można zainicjować przy deklaracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="66469-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="66469-108">Tablica można również zainicjować bez określania rangi.</span><span class="sxs-lookup"><span data-stu-id="66469-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="66469-109">Jeśli zdecydujesz się zadeklarować zmienną tablicową bez `new` inicjowania, należy użyć operatora, aby przypisać tablicę do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="66469-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="66469-110">Użycie `new` jest pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="66469-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="66469-111">Poniższy przykład przypisuje wartość do określonego elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="66469-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="66469-112">Podobnie w poniższym przykładzie pobiera wartość określonego elementu tablicy `elementValue`i przypisuje go do zmiennej .</span><span class="sxs-lookup"><span data-stu-id="66469-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="66469-113">Poniższy przykład kodu inicjuje elementy tablicy do wartości domyślnych (z wyjątkiem tablic postrzępionych).</span><span class="sxs-lookup"><span data-stu-id="66469-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="66469-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66469-114">See also</span></span>

- [<span data-ttu-id="66469-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="66469-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="66469-116">Tablice</span><span class="sxs-lookup"><span data-stu-id="66469-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="66469-117">Tablice jednowymiarowe</span><span class="sxs-lookup"><span data-stu-id="66469-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="66469-118">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="66469-118">Jagged Arrays</span></span>](./jagged-arrays.md)
