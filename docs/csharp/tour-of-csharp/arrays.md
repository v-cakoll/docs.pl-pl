---
title: Tablice języka C# — przewodnik po języku Języka C#
description: Tablice są najbardziej podstawowym typem kolekcji w języku C#
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159198"
---
# <a name="arrays"></a><span data-ttu-id="1fba5-103">Tablice</span><span class="sxs-lookup"><span data-stu-id="1fba5-103">Arrays</span></span>

<span data-ttu-id="1fba5-104">***Tablica*** jest strukturą danych, która zawiera szereg zmiennych, które są dostępne za pośrednictwem indeksów obliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="1fba5-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="1fba5-105">Zmienne zawarte w tablicy, nazywane również ***elementy*** tablicy, są tego samego typu, a ten typ jest nazywany ***typem elementu*** tablicy.</span><span class="sxs-lookup"><span data-stu-id="1fba5-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="1fba5-106">Typy tablic są typami odwołań, a deklaracja zmiennej tablicowej po prostu odkłada miejsce na odwołanie do wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="1fba5-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="1fba5-107">Rzeczywiste wystąpienia tablicy są tworzone dynamicznie w czasie wykonywania przy użyciu nowego operatora.</span><span class="sxs-lookup"><span data-stu-id="1fba5-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="1fba5-108">Nowa operacja określa ***długość*** nowego wystąpienia tablicy, która jest następnie ustalona dla okresu istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1fba5-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="1fba5-109">Indeksy elementów tablicy wahają się `0` od `Length - 1`do .</span><span class="sxs-lookup"><span data-stu-id="1fba5-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="1fba5-110">Operator `new` automatycznie inicjuje elementy tablicy do ich wartości domyślnej, która na przykład wynosi `null` zero dla wszystkich typów liczbowych i dla wszystkich typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="1fba5-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="1fba5-111">Poniższy przykład tworzy tablicę `int` elementów, inicjuje tablicy i drukuje zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="1fba5-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="1fba5-112">W tym przykładzie tworzy i działa na ***tablicy jednowymiarowej***.</span><span class="sxs-lookup"><span data-stu-id="1fba5-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="1fba5-113">C# obsługuje również ***tablice wielowymiarowe***.</span><span class="sxs-lookup"><span data-stu-id="1fba5-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="1fba5-114">Liczba wymiarów typu tablicy, znany również jako ***rangi*** typu tablicy, jest jeden plus liczba przecinków zapisanych między nawiasami kwadratowymi typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="1fba5-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="1fba5-115">Poniższy przykład przydziela jednowymiarową, dwuwymiarową i trójwymiarową tablicę.</span><span class="sxs-lookup"><span data-stu-id="1fba5-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="1fba5-116">Tablica `a1` zawiera 10 `a2` elementów, tablica zawiera 50 (10 `a3` × 5) elementów, a tablica zawiera 100 (10 × 5 × 2) elementów.</span><span class="sxs-lookup"><span data-stu-id="1fba5-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="1fba5-117">Typ elementu tablicy może być dowolny typ, w tym typ tablicy.</span><span class="sxs-lookup"><span data-stu-id="1fba5-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="1fba5-118">Tablica z elementami typu tablicy jest czasami ***nazywana tablicą postrzępioną,*** ponieważ długości tablic elementów nie muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="1fba5-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays don't all have to be the same.</span></span> <span data-ttu-id="1fba5-119">W poniższym przykładzie przydziela tablicę `int`tablic:</span><span class="sxs-lookup"><span data-stu-id="1fba5-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="1fba5-120">Pierwszy wiersz tworzy tablicę z trzema `int[]` elementami, każdy typu `null`i każdy z wartością początkową .</span><span class="sxs-lookup"><span data-stu-id="1fba5-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="1fba5-121">Kolejne wiersze następnie zainicjować trzy elementy z odwołaniami do poszczególnych wystąpień tablicy o różnej długości.</span><span class="sxs-lookup"><span data-stu-id="1fba5-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="1fba5-122">Nowy operator zezwala na początkowe wartości elementów tablicy, które mają być określone za pomocą ***inicjatora tablicy***, który jest listą wyrażeń napisanych między ogranicznikami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="1fba5-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="1fba5-123">Poniższy przykład przydziela i inicjuje z `int[]` trzech elementów.</span><span class="sxs-lookup"><span data-stu-id="1fba5-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="1fba5-124">Długość tablicy jest wywnioskowana z liczby wyrażeń między { i }.</span><span class="sxs-lookup"><span data-stu-id="1fba5-124">The length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="1fba5-125">Deklaracje zmiennych lokalnych i pól można dodatkowo skrócić w taki sposób, aby typ tablicy nie musiał być ponownie przekształcany.</span><span class="sxs-lookup"><span data-stu-id="1fba5-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="1fba5-126">Oba poprzednie przykłady są równoważne z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="1fba5-126">Both of the previous examples are equivalent to the following code:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="1fba5-127">[Poprzedni](classes-and-objects.md)
>[następny](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="1fba5-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
