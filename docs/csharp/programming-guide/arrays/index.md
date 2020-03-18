---
title: Tablice — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715054"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="d0759-102">Tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d0759-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="d0759-103">Wiele zmiennych tego samego typu można przechowywać w strukturze danych tablicowych.</span><span class="sxs-lookup"><span data-stu-id="d0759-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="d0759-104">Tablica deklaruje, określając typ jej elementów.</span><span class="sxs-lookup"><span data-stu-id="d0759-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="d0759-105">Jeśli macierz ma przechowywać elementy dowolnego typu, `object` można określić jako jej typ.</span><span class="sxs-lookup"><span data-stu-id="d0759-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="d0759-106">W ujednoliconym systemie typów Języka C#wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, <xref:System.Object>typy odwołań i typy wartości dziedziczą bezpośrednio lub pośrednio z .</span><span class="sxs-lookup"><span data-stu-id="d0759-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="d0759-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0759-107">Example</span></span>

<span data-ttu-id="d0759-108">Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i postrzępione:</span><span class="sxs-lookup"><span data-stu-id="d0759-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="d0759-109">Omówienie tablicy</span><span class="sxs-lookup"><span data-stu-id="d0759-109">Array overview</span></span>

<span data-ttu-id="d0759-110">Tablica ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d0759-110">An array has the following properties:</span></span>

- <span data-ttu-id="d0759-111">Tablica może być [jednowymiarowa,](single-dimensional-arrays.md) [wielowymiarowa](multidimensional-arrays.md) lub [postrzępiona.](jagged-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="d0759-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="d0759-112">Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="d0759-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="d0759-113">Tych wartości nie można zmienić w okresie istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0759-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="d0759-114">Wartości domyślne liczbowych elementów tablicy są ustawione na zero, a elementy odwołania są ustawione na null.</span><span class="sxs-lookup"><span data-stu-id="d0759-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="d0759-115">Postrzępiona tablica jest tablicą tablic i dlatego jej elementy `null`są typami odwołań i są inicjowane do .</span><span class="sxs-lookup"><span data-stu-id="d0759-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="d0759-116">Tablice są zerowe: tablica z `n` elementami `0` `n-1`jest indeksowana od do .</span><span class="sxs-lookup"><span data-stu-id="d0759-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="d0759-117">Elementy tablicy mogą być dowolnego typu, w tym typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="d0759-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="d0759-118">Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) <xref:System.Array>wywodzącymi się z abstrakcyjnego typu podstawowego .</span><span class="sxs-lookup"><span data-stu-id="d0759-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="d0759-119">Ponieważ ten typ <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>implementuje i , można użyć [foreach](../../language-reference/keywords/foreach-in.md) iteracji na wszystkich tablicach w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d0759-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d0759-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d0759-120">Related sections</span></span>

- [<span data-ttu-id="d0759-121">Użycie tablic jako obiektów</span><span class="sxs-lookup"><span data-stu-id="d0759-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="d0759-122">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="d0759-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="d0759-123">Przekazywanie tablic jako argumentów</span><span class="sxs-lookup"><span data-stu-id="d0759-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="d0759-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d0759-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d0759-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0759-125">See also</span></span>

- [<span data-ttu-id="d0759-126">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d0759-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d0759-127">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="d0759-127">Collections</span></span>](../concepts/collections.md)
