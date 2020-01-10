---
title: Tablice — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715054"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="bc79c-102">Tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bc79c-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="bc79c-103">Można przechowywać wiele zmiennych tego samego typu w strukturze danych tablicy.</span><span class="sxs-lookup"><span data-stu-id="bc79c-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="bc79c-104">Należy zadeklarować tablicę, określając typ jej elementów.</span><span class="sxs-lookup"><span data-stu-id="bc79c-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="bc79c-105">Jeśli chcesz, aby tablica była przechowywana elementów dowolnego typu, jako typ można określić `object`.</span><span class="sxs-lookup"><span data-stu-id="bc79c-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="bc79c-106">W ujednoliconym systemie typów systemu C#, wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub pośrednio z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="bc79c-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="bc79c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc79c-107">Example</span></span>

<span data-ttu-id="bc79c-108">Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i nieregularne:</span><span class="sxs-lookup"><span data-stu-id="bc79c-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="bc79c-109">Przegląd tablicy</span><span class="sxs-lookup"><span data-stu-id="bc79c-109">Array overview</span></span>

<span data-ttu-id="bc79c-110">Tablica ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bc79c-110">An array has the following properties:</span></span>

- <span data-ttu-id="bc79c-111">Tablica może być [Jednowymiarowa](single-dimensional-arrays.md), [wielowymiarowa](multidimensional-arrays.md) lub [nieregularna](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bc79c-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="bc79c-112">Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="bc79c-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="bc79c-113">Nie można zmienić tych wartości w okresie istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="bc79c-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="bc79c-114">Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawione na wartość null.</span><span class="sxs-lookup"><span data-stu-id="bc79c-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="bc79c-115">Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null`.</span><span class="sxs-lookup"><span data-stu-id="bc79c-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="bc79c-116">Tablice są indeksowane jako zero: tablica z elementami `n` jest indeksowana z `0` do `n-1`.</span><span class="sxs-lookup"><span data-stu-id="bc79c-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="bc79c-117">Elementy tablicy mogą być dowolnego typu, łącznie z typem tablicowym.</span><span class="sxs-lookup"><span data-stu-id="bc79c-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="bc79c-118">Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) pochodnymi od abstrakcyjnego typu podstawowego <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="bc79c-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="bc79c-119">Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, można użyć iteracji [foreach](../../language-reference/keywords/foreach-in.md) dla wszystkich tablic w C#.</span><span class="sxs-lookup"><span data-stu-id="bc79c-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="bc79c-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bc79c-120">Related sections</span></span>

- [<span data-ttu-id="bc79c-121">Użycie tablic jako obiektów</span><span class="sxs-lookup"><span data-stu-id="bc79c-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="bc79c-122">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="bc79c-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="bc79c-123">Przekazywanie tablic jako argumentów</span><span class="sxs-lookup"><span data-stu-id="bc79c-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="bc79c-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bc79c-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bc79c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc79c-125">See also</span></span>

- [<span data-ttu-id="bc79c-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bc79c-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bc79c-127">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="bc79c-127">Collections</span></span>](../concepts/collections.md)
