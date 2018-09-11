---
title: Tablice (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e0ed2d678363a29bb870a496846fc6f054769a4b
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268919"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="ec185-102">Tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ec185-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="ec185-103">W strukturze danych tablicy można przechowywać wiele zmiennych tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ec185-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="ec185-104">Można zadeklarować tablicy, określając typ jej elementów.</span><span class="sxs-lookup"><span data-stu-id="ec185-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="ec185-105">Poniższe przykłady tworzą tablice jednowymiarowe, wielowymiarowe i nieregularne:</span><span class="sxs-lookup"><span data-stu-id="ec185-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a><span data-ttu-id="ec185-106">Omówienie macierzy</span><span class="sxs-lookup"><span data-stu-id="ec185-106">Array Overview</span></span>

 <span data-ttu-id="ec185-107">Tablica ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ec185-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="ec185-108">Tablica może być [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) lub [poszarpana](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="ec185-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="ec185-109">Liczba wymiarów i długość każdego wymiaru są określane podczas tworzenia instancji tabeli.</span><span class="sxs-lookup"><span data-stu-id="ec185-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="ec185-110">Te wartości nie można zmienić w trakcie okresu istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ec185-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="ec185-111">Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawiane na wartość null.</span><span class="sxs-lookup"><span data-stu-id="ec185-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="ec185-112">Nieregularna tablica jest tablicy tablic, a zatem jej elementy są typami odwołań i są inicjowane na `null`.</span><span class="sxs-lookup"><span data-stu-id="ec185-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="ec185-113">Tablice są indeksowane zero: tablia z `n` elementami jest indeksowana z `0` do `n-1`.</span><span class="sxs-lookup"><span data-stu-id="ec185-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="ec185-114">Elementy tablicy mogą być dowolnego typu, w tym typu tablicowego.</span><span class="sxs-lookup"><span data-stu-id="ec185-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="ec185-115">Typy tablic mają [typy odwołań](../../../csharp/language-reference/keywords/reference-types.md) pochodzące z abstrakcyjnego typy podstawowego <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="ec185-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="ec185-116">Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, możesz użyć [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteracji na wszystkich tablicach w C#.</span><span class="sxs-lookup"><span data-stu-id="ec185-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec185-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ec185-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="ec185-118">Użycie tablic jako obiektów</span><span class="sxs-lookup"><span data-stu-id="ec185-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="ec185-119">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="ec185-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="ec185-120">Przekazywanie tablic jako argumentów</span><span class="sxs-lookup"><span data-stu-id="ec185-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="ec185-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ec185-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec185-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec185-122">See Also</span></span>

- [<span data-ttu-id="ec185-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ec185-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ec185-124">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="ec185-124">Collections</span></span>](../../../csharp/programming-guide/concepts/collections.md)  
- [<span data-ttu-id="ec185-125">Typ kolekcji tablic</span><span class="sxs-lookup"><span data-stu-id="ec185-125">Array Collection Type</span></span>](https://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
