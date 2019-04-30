---
title: C#Tablice — Przewodnik po przykładzie C# języka
description: Tablice są najbardziej podstawowym typem kolekcji w C# języka
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 8685e6ad08eb74534cdad499099b3d12da0a497a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706419"
---
# <a name="arrays"></a><span data-ttu-id="2894d-103">Tablice</span><span class="sxs-lookup"><span data-stu-id="2894d-103">Arrays</span></span>

<span data-ttu-id="2894d-104">***Tablicy*** to struktura danych, która zawiera szereg zmiennych, które są dostępne za pośrednictwem obliczanej indeksów.</span><span class="sxs-lookup"><span data-stu-id="2894d-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="2894d-105">Zmienne zawartych w tablicy, jest określana skrótem ***elementy*** tablicy, są wszystkie tego samego typu, a tego typu jest nazywana ***typ elementu*** tablicy.</span><span class="sxs-lookup"><span data-stu-id="2894d-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="2894d-106">Typy tablicowe są typami odwołań, a deklaracja zmiennej tablicy po prostu rezerwuje miejsce dla odwołania do wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="2894d-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="2894d-107">Wystąpienia bieżącej tablicy są tworzone dynamicznie w czasie wykonywania za pomocą nowego operatora.</span><span class="sxs-lookup"><span data-stu-id="2894d-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="2894d-108">Określa nową operację ***długość*** nowego wystąpienia tablicy naprawiliśmy dla okresu istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2894d-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="2894d-109">Indeksy elementów z zakresu tablicy `0` do `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="2894d-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="2894d-110">`new` Operator automatycznie inicjuje elementy tablicy, aby przywrócić wartości domyślne, na przykład są to wartości zero dla wszystkich typów liczbowych i `null` dla wszystkich typów odniesienia.</span><span class="sxs-lookup"><span data-stu-id="2894d-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="2894d-111">Poniższy przykład tworzy tablicę `int` elementów, inicjuje tablicy i wyświetla zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="2894d-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="2894d-112">W tym przykładzie tworzy i działa na ***tablicy jednowymiarowej***.</span><span class="sxs-lookup"><span data-stu-id="2894d-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="2894d-113">C# obsługuje również ***Wielowymiarowe tablice***.</span><span class="sxs-lookup"><span data-stu-id="2894d-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="2894d-114">Wpisz liczbę wymiarów tablicy, znany także jako ***ranga*** typ tablicy jest jedną przesunięta liczbę przecinkami zapisywane między nawiasami kwadratowymi typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="2894d-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="2894d-115">Poniższy przykład przydziela odpowiednio jednowymiarowe dwuwymiarowym i tablicą trójwymiarową.</span><span class="sxs-lookup"><span data-stu-id="2894d-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="2894d-116">`a1` Tablica zawiera 10 elementów `a2` tablica zawiera 50 (10 x 5) elementów, a `a3` tablica zawiera 100 (10 x 5 x 2) elementów.</span><span class="sxs-lookup"><span data-stu-id="2894d-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="2894d-117">Typ elementu tablicy może być dowolnego typu, w tym typu tablicowego.</span><span class="sxs-lookup"><span data-stu-id="2894d-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="2894d-118">Tablicę z elementami typu tablicowego jest czasami nazywane ***tablicy nieregularnej*** ponieważ długości tablic elementu nie wszystkie muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="2894d-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="2894d-119">Poniższy przykład przydziela tablicy tablic `int`:</span><span class="sxs-lookup"><span data-stu-id="2894d-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="2894d-120">Pierwszy wiersz tworzy tablicę z trzech elementów, z których każdy typ `int[]` , a każdy z wartości początkowej `null`.</span><span class="sxs-lookup"><span data-stu-id="2894d-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="2894d-121">Kolejne wiersze następnie zainicjowanie trzech elementów z odwołaniami do wystąpień poszczególnych tablicy o różnej długości.</span><span class="sxs-lookup"><span data-stu-id="2894d-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="2894d-122">Nowy operator zezwala na wartość początkową elementów tablicy, należy określić przy użyciu ***inicjatora tablicy***, który znajduje się lista wyrażeń zapisywane między ogranicznikami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="2894d-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="2894d-123">Poniższy przykład przydziela i inicjuje `int[]` za pomocą trzech elementów.</span><span class="sxs-lookup"><span data-stu-id="2894d-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="2894d-124">Należy pamiętać, że długość tablicy jest wnioskowany z liczba wyrażeń między {i}.</span><span class="sxs-lookup"><span data-stu-id="2894d-124">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="2894d-125">Zmienna lokalna i deklaracji pól można skrócony dalsze taki sposób, że typ tablicy nie ma być przekształcone.</span><span class="sxs-lookup"><span data-stu-id="2894d-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="2894d-126">W poprzednich przykładach są odpowiednikiem następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="2894d-126">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="2894d-127">[Poprzednie](structs.md)
>[dalej](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="2894d-127">[Previous](structs.md)
[Next](interfaces.md)</span></span>