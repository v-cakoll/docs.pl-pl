---
title: Tablice jednowymiarowe — Przewodnik programowania w języku C#
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: e189253eedc21fa2d51e16407f04b034610bb57b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410247"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="289f2-102">Tablice jednowymiarowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="289f2-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="289f2-103">Można utworzyć tablicę jednowymiarową przy użyciu operatora [New](../../language-reference/operators/new-operator.md) określającego typ elementu tablicy oraz liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="289f2-103">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="289f2-104">Poniższy przykład deklaruje tablicę pięciu liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="289f2-104">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="289f2-105">Ta tablica zawiera elementy z elementu `array[0]` do `array[4]` .</span><span class="sxs-lookup"><span data-stu-id="289f2-105">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="289f2-106">Elementy tablicy są inicjowane do wartości domyślnej typu elementu, `0` dla liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="289f2-106">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="289f2-107">W tablicach mogą być przechowywane elementy określonego typu, takie jak Poniższy przykład, który deklaruje tablicę ciągów:</span><span class="sxs-lookup"><span data-stu-id="289f2-107">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="289f2-108">Inicjowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="289f2-108">Array Initialization</span></span>

<span data-ttu-id="289f2-109">Można zainicjować elementy tablicy, gdy deklarujesz tablicę.</span><span class="sxs-lookup"><span data-stu-id="289f2-109">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="289f2-110">Specyfikator długości nie jest wymagany, ponieważ jest wywnioskowany przez liczbę elementów na liście inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="289f2-110">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="289f2-111">Przykład:</span><span class="sxs-lookup"><span data-stu-id="289f2-111">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="289f2-112">Poniższy kod przedstawia deklarację tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:</span><span class="sxs-lookup"><span data-stu-id="289f2-112">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="289f2-113">Można uniknąć `new` wyrażenia i typu tablicy podczas inicjowania tablicy po deklaracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="289f2-113">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="289f2-114">Ta nazwa jest nazywana [niejawnie wpisaną tablicą](implicitly-typed-arrays.md):</span><span class="sxs-lookup"><span data-stu-id="289f2-114">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="289f2-115">Można zadeklarować zmienną tablicową bez jej tworzenia, ale należy użyć operatora, `new` gdy przypiszesz nową tablicę do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="289f2-115">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="289f2-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="289f2-116">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="289f2-117">Typ wartości i tablice typów referencyjnych</span><span class="sxs-lookup"><span data-stu-id="289f2-117">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="289f2-118">Rozważmy następującą deklarację tablicy:</span><span class="sxs-lookup"><span data-stu-id="289f2-118">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="289f2-119">Wynik tej instrukcji zależy od tego, czy `SomeType` jest typem wartości czy typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="289f2-119">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="289f2-120">Jeśli jest to typ wartości, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy ma typ `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="289f2-120">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="289f2-121">Jeśli `SomeType` jest typem referencyjnym, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy jest zainicjowany do odwołania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="289f2-121">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="289f2-122">W obu wystąpieniach elementy są inicjowane do wartości domyślnej dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="289f2-122">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="289f2-123">Aby uzyskać więcej informacji na temat typów wartości i typów referencyjnych, zobacz [typy wartości](../../language-reference/builtin-types/value-types.md) i [typy odwołań](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="289f2-123">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="289f2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="289f2-124">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="289f2-125">Tablice</span><span class="sxs-lookup"><span data-stu-id="289f2-125">Arrays</span></span>](./index.md)
- [<span data-ttu-id="289f2-126">Tablice wielowymiarowe</span><span class="sxs-lookup"><span data-stu-id="289f2-126">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="289f2-127">Tablice nieregularne</span><span class="sxs-lookup"><span data-stu-id="289f2-127">Jagged Arrays</span></span>](./jagged-arrays.md)
