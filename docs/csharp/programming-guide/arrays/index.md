---
title: Tablice — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597530"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="c0303-102">Tablice (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c0303-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="c0303-103">Można przechowywać wiele zmiennych tego samego typu w strukturze danych tablicy.</span><span class="sxs-lookup"><span data-stu-id="c0303-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="c0303-104">Należy zadeklarować tablicę, określając typ jej elementów.</span><span class="sxs-lookup"><span data-stu-id="c0303-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="c0303-105">Poniższy przykład tworzy tablice jednowymiarowe, wielowymiarowe i nieregularne:</span><span class="sxs-lookup"><span data-stu-id="c0303-105">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a><span data-ttu-id="c0303-106">Przegląd tablicy</span><span class="sxs-lookup"><span data-stu-id="c0303-106">Array Overview</span></span>

 <span data-ttu-id="c0303-107">Tablica ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c0303-107">An array has the following properties:</span></span>  
  
- <span data-ttu-id="c0303-108">Tablica może być Jednowymiarowa, wielowymiarowa lub nieregularna. [](./single-dimensional-arrays.md) [](./multidimensional-arrays.md) [](./jagged-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="c0303-108">An array can be [Single-Dimensional](./single-dimensional-arrays.md), [Multidimensional](./multidimensional-arrays.md) or [Jagged](./jagged-arrays.md).</span></span>  
  
- <span data-ttu-id="c0303-109">Liczba wymiarów i długość każdego wymiaru są ustalane podczas tworzenia wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="c0303-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="c0303-110">Nie można zmienić tych wartości w okresie istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c0303-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
- <span data-ttu-id="c0303-111">Wartości domyślne elementów tablicy liczbowej są ustawiane na zero, a elementy odniesienia są ustawione na wartość null.</span><span class="sxs-lookup"><span data-stu-id="c0303-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
- <span data-ttu-id="c0303-112">Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null`.</span><span class="sxs-lookup"><span data-stu-id="c0303-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
- <span data-ttu-id="c0303-113">Tablice są indeksowane jako zero: tablica z `n` elementami jest indeksowana `0` z `n-1`do.</span><span class="sxs-lookup"><span data-stu-id="c0303-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
- <span data-ttu-id="c0303-114">Elementy tablicy mogą być dowolnego typu, łącznie z typem tablicowym.</span><span class="sxs-lookup"><span data-stu-id="c0303-114">Array elements can be of any type, including an array type.</span></span>  
  
- <span data-ttu-id="c0303-115">Typy tablic są [typami odwołań](../../language-reference/keywords/reference-types.md) pochodzącymi od abstrakcyjnego <xref:System.Array>typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c0303-115">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="c0303-116">Ponieważ ten typ implementuje <xref:System.Collections.IEnumerable> i <xref:System.Collections.Generic.IEnumerable%601>, można użyć iteracji [foreach](../../language-reference/keywords/foreach-in.md) dla wszystkich tablic w C#.</span><span class="sxs-lookup"><span data-stu-id="c0303-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0303-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c0303-117">Related Sections</span></span>  
  
- [<span data-ttu-id="c0303-118">Użycie tablic jako obiektów</span><span class="sxs-lookup"><span data-stu-id="c0303-118">Arrays as Objects</span></span>](./arrays-as-objects.md)  
  
- [<span data-ttu-id="c0303-119">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="c0303-119">Using foreach with Arrays</span></span>](./using-foreach-with-arrays.md)  
  
- [<span data-ttu-id="c0303-120">Przekazywanie tablic jako argumentów</span><span class="sxs-lookup"><span data-stu-id="c0303-120">Passing Arrays as Arguments</span></span>](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="c0303-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c0303-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0303-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0303-122">See also</span></span>

- [<span data-ttu-id="c0303-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c0303-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c0303-124">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="c0303-124">Collections</span></span>](../concepts/collections.md)
