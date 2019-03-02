---
title: Tablice jednowymiarowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 719e4463806c9c7e8b5407f2494c3b548ffa43e8
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200783"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="fe844-102">Tablice jednowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fe844-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="fe844-103">Można zadeklarować tablicy jednowymiarowej pięciu liczb całkowitych, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fe844-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="fe844-104">Ta tablica zawiera elementy z `array[0]` do `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="fe844-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="fe844-105">[Nowe](../../../csharp/language-reference/keywords/new.md) operator jest używany do utworzenia tablicy i Inicjowanie elementów tablicy, do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="fe844-105">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="fe844-106">W tym przykładzie wszystkie elementy tablicy są inicjowane od zera.</span><span class="sxs-lookup"><span data-stu-id="fe844-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="fe844-107">Tablica, która przechowuje elementami typu ciąg może być zadeklarowana w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="fe844-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="fe844-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe844-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="fe844-109">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="fe844-109">Array Initialization</span></span>

 <span data-ttu-id="fe844-110">Istnieje możliwość zainicjowania tablicy po zgłoszeniu, w którym to przypadku specyfikator długości nie jest potrzebna, ponieważ jest już podana przez liczbę elementów listy inicjowania.</span><span class="sxs-lookup"><span data-stu-id="fe844-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="fe844-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe844-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="fe844-112">Tablica ciągów mogą być inicjowane w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="fe844-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="fe844-113">Poniżej przedstawiono deklaracją tablicy ciągów gdzie każdy element tablicy jest inicjowany przez nazwę dnia:</span><span class="sxs-lookup"><span data-stu-id="fe844-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="fe844-114">Podczas inicjowania tablicy po deklaracji, można użyć następujących skrótów klawiaturowych:</span><span class="sxs-lookup"><span data-stu-id="fe844-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="fe844-115">Można zadeklarować zmiennej tablicy bez inicjowania, ale muszą używać `new` operator podczas przypisywania tablicy do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fe844-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="fe844-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe844-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="fe844-117">C# 3.0 wprowadzono niejawnie wpisane tablice.</span><span class="sxs-lookup"><span data-stu-id="fe844-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="fe844-118">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="fe844-118">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="fe844-119">Typ wartości i tablicami typu odwołania</span><span class="sxs-lookup"><span data-stu-id="fe844-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="fe844-120">Rozważmy następującą deklarację tablicy:</span><span class="sxs-lookup"><span data-stu-id="fe844-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="fe844-121">Wynikiem tej instrukcji jest zależna od tego, czy `SomeType` jest typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="fe844-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="fe844-122">Jeśli jest to typ wartości, instrukcja tworzy tablicę 10 elementów, z których każdy ma typ `SomeType`.</span><span class="sxs-lookup"><span data-stu-id="fe844-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="fe844-123">Jeśli `SomeType` jest typem referencyjnym instrukcja tworzy tablicę o 10 elementów, z których każdy jest zainicjowany na odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="fe844-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="fe844-124">Aby uzyskać więcej informacji dotyczących typów wartości i typami odwołania, zobacz [typy](../../../csharp/language-reference/keywords/types.md).</span><span class="sxs-lookup"><span data-stu-id="fe844-124">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe844-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe844-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="fe844-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fe844-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fe844-127">Tablice</span><span class="sxs-lookup"><span data-stu-id="fe844-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="fe844-128">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="fe844-128">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="fe844-129">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="fe844-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
