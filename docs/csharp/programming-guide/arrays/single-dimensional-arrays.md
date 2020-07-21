---
title: Tablice jednowymiarowe — Przewodnik programowania w języku C#
description: Utwórz tablicę jednowymiarową w języku C# przy użyciu operatora new określającego typ elementu tablicy i liczbę elementów.
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474595"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="cc0e4-103">Tablice jednowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cc0e4-103">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="cc0e4-104">Można utworzyć tablicę jednowymiarową przy użyciu operatora [New](../../language-reference/operators/new-operator.md) określającego typ elementu tablicy oraz liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-104">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="cc0e4-105">Poniższy przykład deklaruje tablicę pięciu liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="cc0e4-105">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="cc0e4-106">Ta tablica zawiera elementy z elementu `array[0]` do `array[4]` .</span><span class="sxs-lookup"><span data-stu-id="cc0e4-106">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="cc0e4-107">Elementy tablicy są inicjowane do wartości domyślnej typu elementu, `0` dla liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-107">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="cc0e4-108">W tablicach mogą być przechowywane elementy określonego typu, takie jak Poniższy przykład, który deklaruje tablicę ciągów:</span><span class="sxs-lookup"><span data-stu-id="cc0e4-108">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="cc0e4-109">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="cc0e4-109">Array Initialization</span></span>

<span data-ttu-id="cc0e4-110">Można zainicjować elementy tablicy, gdy deklarujesz tablicę.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-110">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="cc0e4-111">Specyfikator długości nie jest wymagany, ponieważ jest wywnioskowany przez liczbę elementów na liście inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-111">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="cc0e4-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cc0e4-112">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="cc0e4-113">Poniższy kod przedstawia deklarację tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:</span><span class="sxs-lookup"><span data-stu-id="cc0e4-113">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="cc0e4-114">Można uniknąć `new` wyrażenia i typu tablicy podczas inicjowania tablicy po deklaracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-114">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="cc0e4-115">Ta nazwa jest nazywana [niejawnie wpisaną tablicą](implicitly-typed-arrays.md):</span><span class="sxs-lookup"><span data-stu-id="cc0e4-115">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="cc0e4-116">Można zadeklarować zmienną tablicową bez jej tworzenia, ale należy użyć operatora, `new` gdy przypiszesz nową tablicę do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-116">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="cc0e4-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cc0e4-117">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="cc0e4-118">Typ wartości i tablice typów referencyjnych</span><span class="sxs-lookup"><span data-stu-id="cc0e4-118">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="cc0e4-119">Rozważmy następującą deklarację tablicy:</span><span class="sxs-lookup"><span data-stu-id="cc0e4-119">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="cc0e4-120">Wynik tej instrukcji zależy od tego, czy `SomeType` jest typem wartości czy typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-120">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="cc0e4-121">Jeśli jest to typ wartości, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy ma typ `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="cc0e4-121">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="cc0e4-122">Jeśli `SomeType` jest typem referencyjnym, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy jest zainicjowany do odwołania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-122">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="cc0e4-123">W obu wystąpieniach elementy są inicjowane do wartości domyślnej dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="cc0e4-123">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="cc0e4-124">Aby uzyskać więcej informacji na temat typów wartości i typów referencyjnych, zobacz [typy wartości](../../language-reference/builtin-types/value-types.md) i [typy odwołań](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc0e4-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cc0e4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc0e4-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="cc0e4-126">Tablice</span><span class="sxs-lookup"><span data-stu-id="cc0e4-126">Arrays</span></span>](./index.md)
- [<span data-ttu-id="cc0e4-127">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="cc0e4-127">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="cc0e4-128">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="cc0e4-128">Jagged Arrays</span></span>](./jagged-arrays.md)
