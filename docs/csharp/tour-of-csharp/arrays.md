---
title: C#Tablice — Przewodnik po C# języku
description: Tablice są najbardziej podstawowym typem kolekcji w C# języku
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159198"
---
# <a name="arrays"></a><span data-ttu-id="54e1b-103">Tablice</span><span class="sxs-lookup"><span data-stu-id="54e1b-103">Arrays</span></span>

<span data-ttu-id="54e1b-104">***Tablica*** to struktura danych zawierająca wiele zmiennych, do których można uzyskać dostęp za pomocą obliczanych indeksów.</span><span class="sxs-lookup"><span data-stu-id="54e1b-104">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="54e1b-105">Zmienne zawarte w tablicy, nazywane również ***elementami*** tablicy, są tego samego typu, a ten typ jest nazywany ***typem elementu*** tablicy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-105">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="54e1b-106">Typy tablic są typami odwołań, a deklaracja zmiennej tablicowej po prostu ustawia miejsce na odwołanie do wystąpienia tablicy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-106">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="54e1b-107">Rzeczywiste wystąpienia tablicy są tworzone dynamicznie w czasie wykonywania przy użyciu operatora new.</span><span class="sxs-lookup"><span data-stu-id="54e1b-107">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="54e1b-108">Nowa operacja określa ***Długość*** nowego wystąpienia tablicy, które jest następnie naprawione dla okresu istnienia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-108">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="54e1b-109">Indeksy elementów z zakresu tablicy od `0` do `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-109">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="54e1b-110">Operator `new` automatycznie inicjuje elementy tablicy do ich wartości domyślnej, co na przykład ma wartość zero dla wszystkich typów liczbowych i `null` dla wszystkich typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="54e1b-110">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="54e1b-111">Poniższy przykład tworzy tablicę elementów `int`, Inicjuje tablicę i drukuje zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-111">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="54e1b-112">Ten przykład tworzy i działa na ***tablicy jednowymiarowej***.</span><span class="sxs-lookup"><span data-stu-id="54e1b-112">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="54e1b-113">C#obsługuje również ***tablice***wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="54e1b-113">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="54e1b-114">Liczba wymiarów typu tablicy, znana również jako ***ranga*** typu tablicy, jest taka, a liczba przecinkiów zapisywana między nawiasami kwadratowymi typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-114">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="54e1b-115">Poniższy przykład przydziela odpowiednio jednowymiarowe, dwuwymiarowe i trójwymiarowe tablice.</span><span class="sxs-lookup"><span data-stu-id="54e1b-115">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="54e1b-116">Tablica `a1` zawiera 10 elementów, tablica `a2` zawiera 50 (10 × 5) elementów, a tablica `a3` zawiera 100 (10 × 5 × 2) elementów.</span><span class="sxs-lookup"><span data-stu-id="54e1b-116">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="54e1b-117">Typ elementu tablicy może być dowolnego typu, łącznie z typem tablicy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-117">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="54e1b-118">Tablica z elementami typu tablicy jest czasami nazywana ***tablicą nieregularną*** , ponieważ długości tablic elementów nie wszystkie muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="54e1b-118">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays don't all have to be the same.</span></span> <span data-ttu-id="54e1b-119">W poniższym przykładzie przypisuje tablicę tablic `int`:</span><span class="sxs-lookup"><span data-stu-id="54e1b-119">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="54e1b-120">Pierwszy wiersz tworzy tablicę z trzema elementami, każdy z typów `int[]` i każdy z początkową wartością `null`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-120">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="54e1b-121">Kolejne wiersze inicjują następnie trzy elementy z odwołaniami do poszczególnych wystąpień tablicy o różnej długości.</span><span class="sxs-lookup"><span data-stu-id="54e1b-121">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="54e1b-122">Operator new pozwala na określenie początkowych wartości elementów tablicy przy użyciu ***inicjatora tablicy***, który jest listą wyrażeń pisanych między ogranicznikami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-122">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="54e1b-123">Poniższy przykład przydziela i inicjuje `int[]` z trzema elementami.</span><span class="sxs-lookup"><span data-stu-id="54e1b-123">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="54e1b-124">Długość tablicy jest wywnioskowana na podstawie liczby wyrażeń między {i}.</span><span class="sxs-lookup"><span data-stu-id="54e1b-124">The length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="54e1b-125">Deklaracje zmiennej lokalnej i pola mogą być skrócone w taki sposób, aby nie trzeba było przestawiać tego typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-125">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="54e1b-126">Oba poprzednie przykłady są równoważne następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="54e1b-126">Both of the previous examples are equivalent to the following code:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
><span data-ttu-id="54e1b-127">[Poprzednie](classes-and-objects.md)
>[dalej](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="54e1b-127">[Previous](classes-and-objects.md)
[Next](interfaces.md)</span></span>
