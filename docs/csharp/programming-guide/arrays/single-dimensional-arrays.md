---
title: Tablice jednowymiarowe — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 07c6061bfc66b1640d0eacca217302feff1a390a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715029"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="987ea-102">Tablice jednowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="987ea-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="987ea-103">Można zadeklarować jednowymiarową tablicę składającą się z pięciu liczb całkowitych, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="987ea-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="987ea-104">Ta tablica zawiera elementy `array[0]` do `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="987ea-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="987ea-105">Operator [New](../../language-reference/operators/new-operator.md) jest używany do tworzenia tablicy i inicjowania elementów tablicy do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="987ea-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="987ea-106">W tym przykładzie wszystkie elementy tablicy są inicjowane do zera.</span><span class="sxs-lookup"><span data-stu-id="987ea-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="987ea-107">Tablica, która przechowuje elementy ciągu, może być zadeklarowana w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="987ea-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="987ea-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="987ea-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="987ea-109">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="987ea-109">Array Initialization</span></span>

 <span data-ttu-id="987ea-110">Możliwe jest zainicjowanie tablicy przy użyciu deklaracji, w takim przypadku specyfikator długości nie jest wymagany, ponieważ jest już dostarczany przez liczbę elementów na liście inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="987ea-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="987ea-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="987ea-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="987ea-112">Tablicę ciągów można zainicjować w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="987ea-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="987ea-113">Poniżej znajduje się deklaracja tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:</span><span class="sxs-lookup"><span data-stu-id="987ea-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="987ea-114">Po zainicjowaniu tablicy po zgłoszeniu można użyć następujących skrótów:</span><span class="sxs-lookup"><span data-stu-id="987ea-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="987ea-115">Istnieje możliwość zadeklarować zmienną tablicową bez inicjalizacji, ale należy użyć operatora `new`, gdy przypiszesz tablicę do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="987ea-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="987ea-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="987ea-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="987ea-117">C#3,0 wprowadza niejawnie wpisane tablice.</span><span class="sxs-lookup"><span data-stu-id="987ea-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="987ea-118">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane tablice](./implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="987ea-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="987ea-119">Typ wartości i tablice typów referencyjnych</span><span class="sxs-lookup"><span data-stu-id="987ea-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="987ea-120">Rozważmy następującą deklarację tablicy:</span><span class="sxs-lookup"><span data-stu-id="987ea-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="987ea-121">Wynik tej instrukcji zależy od tego, czy `SomeType` jest typem wartości czy typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="987ea-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="987ea-122">Jeśli jest to typ wartości, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy ma typ `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="987ea-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="987ea-123">Jeśli `SomeType` jest typem referencyjnym, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy jest zainicjowany do odwołania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="987ea-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="987ea-124">Aby uzyskać więcej informacji na temat typów wartości i typów referencyjnych, zobacz [typy wartości](../../language-reference/keywords/value-types.md) i [typy odwołań](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="987ea-124">For more information about value types and reference types, see [Value types](../../language-reference/keywords/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="987ea-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="987ea-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="987ea-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="987ea-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="987ea-127">Tablice</span><span class="sxs-lookup"><span data-stu-id="987ea-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="987ea-128">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="987ea-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="987ea-129">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="987ea-129">Jagged Arrays</span></span>](./jagged-arrays.md)
