---
title: "C# tablice — samouczek języka C#"
description: "Tablice są najbardziej podstawowa typ kolekcji w języku C#"
keywords: ".NET, csharp, tablicę, kolekcji"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a><span data-ttu-id="8e1ee-104">Tablice</span><span class="sxs-lookup"><span data-stu-id="8e1ee-104">Arrays</span></span>

<span data-ttu-id="8e1ee-105">***Tablicy*** jest strukturą danych, która zawiera szereg zmiennych, które są udostępniane przez obliczoną indeksów.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-105">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="8e1ee-106">Zmienne zawartych w tablicy, nazywany również ***elementy*** tablicy, znajdują się tego samego typu, a tego typu jest nazywana ***typ elementu*** tablicy.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-106">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="8e1ee-107">Typy tablicy są typy referencyjne i deklaracja zmiennej tablicy po prostu rezerwuje miejsca dla odwołania do wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-107">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="8e1ee-108">Wystąpienia bieżącej tablicy są tworzone dynamicznie w czasie wykonywania za pomocą operatora new.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-108">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="8e1ee-109">Określa nową operację ***długość*** nowego wystąpienia tablicy, która jest następnie u okresu istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-109">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="8e1ee-110">Indeksów elementów zakresu tablicy z `0` do `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-110">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="8e1ee-111">`new` Operator automatycznie inicjuje elementy tablicy można przywrócić wartości domyślne, czyli, na przykład zero dla wszystkich typów numerycznych i `null` dla wszystkich typów odniesienia.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-111">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="8e1ee-112">Poniższy przykład tworzy tablicę `int` elementów inicjuje tablicy, a następnie do drukowania zawartości tablicy.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-112">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="8e1ee-113">W tym przykładzie tworzy i działa na ***tablicy jednowymiarowej***.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-113">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="8e1ee-114">C# obsługuje również ***tablic wielowymiarowych***.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-114">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="8e1ee-115">Wpisz liczbę wymiarów tablicy, znanej także jako ***rangę*** typu tablicy jest jeden oraz liczbę przecinkami zapisywane między nawiasami kwadratowymi typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-115">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="8e1ee-116">Poniższy przykład przydziela odpowiednio jednowymiarowe dwuwymiarowa i jest tablicą trójwymiarową.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-116">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="8e1ee-117">`a1` Tablica zawiera 10 elementów `a2` tablica zawiera 50 (10 x 5) elementów i `a3` 100 (10 x 5 x 2) zawiera tablicę elementów.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-117">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="8e1ee-118">Typ elementu tablicy mogą być dowolnego typu, łącznie z typem tablicy.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-118">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="8e1ee-119">Tablica elementami typu tablicy jest czasami nazywany ***tablicy nieregularnej*** ponieważ długości tablic elementu nie wszystkie muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-119">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="8e1ee-120">Poniższy przykład przydziela tablicy tablic `int`:</span><span class="sxs-lookup"><span data-stu-id="8e1ee-120">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="8e1ee-121">Pierwszy wiersz tworzy tablicę z trzech elementów, dla każdego typu `int[]` i każde z nich wartość początkową `null`.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-121">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="8e1ee-122">Kolejne wiersze zainicjować następnie trzy elementy o odwołań do tablicy pojedynczych wystąpień różne długości.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-122">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="8e1ee-123">New operator zezwala na wartości początkowe elementy tablicy można określić za pomocą ***inicjatora tablicy***, który znajduje się lista wyrażeń zapisywane między ograniczniki `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-123">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="8e1ee-124">W poniższym przykładzie przydziela i inicjuje `int[]` z trzech elementów.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-124">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="8e1ee-125">Należy pamiętać, że długość tablicy jest wywnioskowany na podstawie liczba wyrażeń między {i}.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-125">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="8e1ee-126">Zmienna lokalna i deklaracje pól można skrócony dalsze tak, aby typ tablicy nie ma zostać przekształcone.</span><span class="sxs-lookup"><span data-stu-id="8e1ee-126">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="8e1ee-127">Poprzednich przykładach są równoważne z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8e1ee-127">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
<span data-ttu-id="8e1ee-128">[Poprzednie](structs.md)
[dalej](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="8e1ee-128">[Previous](structs.md)
[Next](interfaces.md)</span></span>
