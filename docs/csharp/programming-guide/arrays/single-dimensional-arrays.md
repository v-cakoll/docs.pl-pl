---
title: Tablice jednowymiarowe — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170354"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="2100c-102">Tablice jednowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2100c-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="2100c-103">Można zadeklarować jednowymiarową tablicę pięciu liczb całkowitych, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2100c-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="2100c-104">Ta tablica zawiera `array[0]` `array[4]`elementy od do .</span><span class="sxs-lookup"><span data-stu-id="2100c-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="2100c-105">[Nowy](../../language-reference/operators/new-operator.md) operator jest używany do tworzenia tablicy i inicjowania elementów tablicy do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="2100c-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="2100c-106">W tym przykładzie wszystkie elementy tablicy są inicjowane do zera.</span><span class="sxs-lookup"><span data-stu-id="2100c-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="2100c-107">Tablica, która przechowuje elementy ciągu mogą być zadeklarowane w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="2100c-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="2100c-108">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2100c-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="2100c-109">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="2100c-109">Array Initialization</span></span>

 <span data-ttu-id="2100c-110">Istnieje możliwość zainicjowania tablicy na deklarację, w którym to przypadku specyfikator długości nie jest potrzebny, ponieważ jest już dostarczany przez liczbę elementów na liście inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="2100c-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="2100c-111">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2100c-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="2100c-112">Tablica ciągów może być inicjowana w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="2100c-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="2100c-113">Poniżej przedstawiono deklarację tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:</span><span class="sxs-lookup"><span data-stu-id="2100c-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="2100c-114">Podczas inicjowania tablicy na deklarację, można użyć następujących skrótów:</span><span class="sxs-lookup"><span data-stu-id="2100c-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="2100c-115">Istnieje możliwość zadeklarowania zmiennej tablicy bez inicjowania, ale należy użyć `new` operatora podczas przypisywania tablicy do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2100c-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="2100c-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2100c-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="2100c-117">C# 3.0 wprowadza niejawnie wpisane tablice.</span><span class="sxs-lookup"><span data-stu-id="2100c-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="2100c-118">Aby uzyskać więcej informacji, zobacz [Tablice wpisane niejawnie](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="2100c-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="2100c-119">Tablice typów wartości i typów odwołań</span><span class="sxs-lookup"><span data-stu-id="2100c-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="2100c-120">Należy wziąć pod uwagę następującą deklarację tablicy:</span><span class="sxs-lookup"><span data-stu-id="2100c-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="2100c-121">Wynik tej instrukcji zależy `SomeType` od tego, czy jest typem wartości, czy typem odwołania.</span><span class="sxs-lookup"><span data-stu-id="2100c-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="2100c-122">Jeśli jest typem wartości, instrukcja tworzy tablicę 10 elementów, `SomeType`z których każdy ma typ .</span><span class="sxs-lookup"><span data-stu-id="2100c-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="2100c-123">Jeśli `SomeType` jest typem odwołania, instrukcja tworzy tablicę 10 elementów, z których każdy jest inicjowany do odwołania null.</span><span class="sxs-lookup"><span data-stu-id="2100c-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="2100c-124">Aby uzyskać więcej informacji na temat typów wartości i typów odwołań, zobacz [Typy wartości](../../language-reference/builtin-types/value-types.md) i [Typy odwołań](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="2100c-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2100c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2100c-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="2100c-126">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="2100c-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2100c-127">Tablice</span><span class="sxs-lookup"><span data-stu-id="2100c-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="2100c-128">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="2100c-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="2100c-129">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="2100c-129">Jagged Arrays</span></span>](./jagged-arrays.md)
