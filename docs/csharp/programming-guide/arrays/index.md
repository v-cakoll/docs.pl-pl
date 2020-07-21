---
title: Tablice — Przewodnik programowania w języku C#
description: Przechowuj wiele zmiennych tego samego typu w strukturze danych tablicy w języku C#. Zadeklaruj tablicę, określając typ lub Określ obiekt do przechowywania dowolnego typu.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474738"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="1df4f-104">Tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1df4f-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="1df4f-105">Można przechowywać wiele zmiennych tego samego typu w strukturze danych tablicy.</span><span class="sxs-lookup"><span data-stu-id="1df4f-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="1df4f-106">Należy zadeklarować tablicę, określając typ jej elementów.</span><span class="sxs-lookup"><span data-stu-id="1df4f-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="1df4f-107">Jeśli chcesz, aby tablica była przechowywana elementów dowolnego typu, możesz określić `object` jako jej typ.</span><span class="sxs-lookup"><span data-stu-id="1df4f-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="1df4f-108">W systemie ujednoliconego typu języka C# wszystkie typy, wstępnie zdefiniowane i zdefiniowane przez użytkownika, typy odwołań i typy wartości, dziedziczą bezpośrednio lub pośrednio z <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="1df4f-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="1df4f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1df4f-109">Example</span></span>

<span data-ttu-id="1df4f-110">Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i nieregularne:</span><span class="sxs-lookup"><span data-stu-id="1df4f-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="1df4f-111">Przegląd tablicy</span><span class="sxs-lookup"><span data-stu-id="1df4f-111">Array overview</span></span>

<span data-ttu-id="1df4f-112">Tablica ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1df4f-112">An array has the following properties:</span></span>

- <span data-ttu-id="1df4f-113">Tablica może być [Jednowymiarowa](single-dimensional-arrays.md), [wielowymiarowa](multidimensional-arrays.md) lub [nieregularna](jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1df4f-113">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="1df4f-114">Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="1df4f-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="1df4f-115">Nie można zmienić tych wartości w okresie istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1df4f-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="1df4f-116">Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawione na wartość null.</span><span class="sxs-lookup"><span data-stu-id="1df4f-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="1df4f-117">Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null` .</span><span class="sxs-lookup"><span data-stu-id="1df4f-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="1df4f-118">Tablice są indeksowane jako zero: tablica z `n` elementami jest indeksowana z `0` do `n-1` .</span><span class="sxs-lookup"><span data-stu-id="1df4f-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="1df4f-119">Elementy tablicy mogą być dowolnego typu, łącznie z typem tablicowym.</span><span class="sxs-lookup"><span data-stu-id="1df4f-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="1df4f-120">Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) pochodzącymi od abstrakcyjnego typu podstawowego <xref:System.Array> .</span><span class="sxs-lookup"><span data-stu-id="1df4f-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="1df4f-121">Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601> , można użyć iteracji [foreach](../../language-reference/keywords/foreach-in.md) dla wszystkich tablic w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1df4f-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1df4f-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1df4f-122">Related sections</span></span>

- [<span data-ttu-id="1df4f-123">Użycie tablic jako obiektów</span><span class="sxs-lookup"><span data-stu-id="1df4f-123">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="1df4f-124">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="1df4f-124">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="1df4f-125">Przekazywanie tablic jako argumentów</span><span class="sxs-lookup"><span data-stu-id="1df4f-125">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="1df4f-126">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1df4f-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1df4f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1df4f-127">See also</span></span>

- [<span data-ttu-id="1df4f-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1df4f-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1df4f-129">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="1df4f-129">Collections</span></span>](../concepts/collections.md)
