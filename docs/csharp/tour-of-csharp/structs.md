---
title: "C# struktury — samouczek języka C#"
description: "Dowiedz się, że typy, o nazwie struktury wartości podstawy języka C#"
keywords: "Typ wartości .NET, C#, struktury,"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="structs"></a><span data-ttu-id="aa492-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="aa492-104">Structs</span></span>

<span data-ttu-id="aa492-105">Takich jak klasy, ***struktury*** są struktur danych, które mogą zawierać elementów członkowskich danych i członkowie funkcji, ale w przeciwieństwie do klasy, struktury są typy wartości i nie wymagają alokacji sterty.</span><span class="sxs-lookup"><span data-stu-id="aa492-105">Like classes, ***structs*** are data structures that can contain data members and function members, but unlike classes, structs are value types and do not require heap allocation.</span></span> <span data-ttu-id="aa492-106">Zmienna typu struct bezpośrednio przechowuje dane struktury, natomiast zmienna typu klasy przechowuje odwołanie do dynamicznie przydzielonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa492-106">A variable of a struct type directly stores the data of the struct, whereas a variable of a class type stores a reference to a dynamically allocated object.</span></span> <span data-ttu-id="aa492-107">Typy struktur nie obsługują określone przez użytkownika dziedziczenia, a wszystkie typy struktur niejawnie dziedziczyć z typu <xref:System.ValueType>, który z kolei niejawnie dziedziczy `object`.</span><span class="sxs-lookup"><span data-stu-id="aa492-107">Struct types do not support user-specified inheritance, and all struct types implicitly inherit from type <xref:System.ValueType>, which in turn implicitly inherits from `object`.</span></span>

<span data-ttu-id="aa492-108">Struktury są szczególnie przydatne w strukturach niewielkie zbiory danych, które ma wartość semantyki.</span><span class="sxs-lookup"><span data-stu-id="aa492-108">Structs are particularly useful for small data structures that have value semantics.</span></span> <span data-ttu-id="aa492-109">Liczby złożone, punkty w układzie współrzędnych lub pary klucz wartość ze słownika są dobrym przykładem struktury.</span><span class="sxs-lookup"><span data-stu-id="aa492-109">Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs.</span></span> <span data-ttu-id="aa492-110">Używanie struktur, zamiast klasy dla struktury danych w małych ułatwia duża różnica w liczbie alokacji pamięci aplikacji wykonuje.</span><span class="sxs-lookup"><span data-stu-id="aa492-110">The use of structs rather than classes for small data structures can make a large difference in the number of memory allocations an application performs.</span></span> <span data-ttu-id="aa492-111">Na przykład następujący program tworzy i inicjuje tablicę 100 punktów.</span><span class="sxs-lookup"><span data-stu-id="aa492-111">For example, the following program creates and initializes an array of 100 points.</span></span> <span data-ttu-id="aa492-112">Z `Point` wystąpienia zaimplementowane jako klasa, 101 oddzielnych obiektów — jeden dla tablicy i jeden dla każdej 100 elementów.</span><span class="sxs-lookup"><span data-stu-id="aa492-112">With `Point` implemented as a class, 101 separate objects are instantiated—one for the array and one each for the 100 elements.</span></span>

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

<span data-ttu-id="aa492-113">Alternatywą jest zapewnienie punktu struktury.</span><span class="sxs-lookup"><span data-stu-id="aa492-113">An alternative is to make Point a struct.</span></span>

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

<span data-ttu-id="aa492-114">Teraz, zostanie uruchomiony tylko jeden obiekt — jeden dla tablicy — i `Point` wystąpienia są przechowywane w wierszu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="aa492-114">Now, only one object is instantiated—the one for the array—and the `Point` instances are stored in-line in the array.</span></span>

<span data-ttu-id="aa492-115">Struct — Konstruktorzy są wywoływane z operatora new, ale który nie oznacza, że pamięć jest przydzielane.</span><span class="sxs-lookup"><span data-stu-id="aa492-115">Struct constructors are invoked with the new operator, but that does not imply that memory is being allocated.</span></span> <span data-ttu-id="aa492-116">Zamiast dynamiczne przydzielanie obiektu i zwraca odwołanie do niej konstruktora struktury po prostu zwraca wartość — Struktura (zwykle w tymczasowej lokalizacji na stosie), a ta wartość jest następnie skopiowana niezbędne.</span><span class="sxs-lookup"><span data-stu-id="aa492-116">Instead of dynamically allocating an object and returning a reference to it, a struct constructor simply returns the struct value itself (typically in a temporary location on the stack), and this value is then copied as necessary.</span></span>

<span data-ttu-id="aa492-117">W przypadku klas jest możliwe dwie zmienne odwołać się do tego samego obiektu i w związku z tym możliwe w dla operacji na jedną zmienną, która wpływa na obiekt odwołuje się innej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="aa492-117">With classes, it is possible for two variables to reference the same object and thus possible for operations on one variable to affect the object referenced by the other variable.</span></span> <span data-ttu-id="aa492-118">Ze struktury zmienne każdego mają własne kopię danych, a nie jest możliwe w dla operacji na jednym wpłynąć na innych.</span><span class="sxs-lookup"><span data-stu-id="aa492-118">With structs, the variables each have their own copy of the data, and it is not possible for operations on one to affect the other.</span></span> <span data-ttu-id="aa492-119">Na przykład dane wyjściowe, generowane przez następujący fragment kodu zależy od tego, czy punkt znajduje się w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="aa492-119">For example, the output produced by the following code fragment depends on whether Point is a class or a struct.</span></span>

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

<span data-ttu-id="aa492-120">Jeśli `Point` jest klasą, dane wyjściowe wynosi 20, ponieważ i b odwołuje się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa492-120">If `Point` is a class, the output is 20 because a and b reference the same object.</span></span> <span data-ttu-id="aa492-121">Jeśli punkt jest strukturą, dane wyjściowe to 10, ponieważ przypisanie `a` do `b` tworzy kopię wartości, i nie mają wpływu kolejne przypisanie do tej kopii `a.x`.</span><span class="sxs-lookup"><span data-stu-id="aa492-121">If Point is a struct, the output is 10 because the assignment of `a` to `b` creates a copy of the value, and this copy is unaffected by the subsequent assignment to `a.x`.</span></span>

<span data-ttu-id="aa492-122">Poprzedni przykład przedstawia dwa ograniczenia struktury.</span><span class="sxs-lookup"><span data-stu-id="aa492-122">The previous example highlights two of the limitations of structs.</span></span> <span data-ttu-id="aa492-123">Po pierwsze skopiowanie całej struktury jest zazwyczaj są mniej wydajne niż kopiowanie odwołania do obiektu, więc przekazywanie przypisania i wartość parametru może być droższe z struktury niż z typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="aa492-123">First, copying an entire struct is typically less efficient than copying an object reference, so assignment and value parameter passing can be more expensive with structs than with reference types.</span></span> <span data-ttu-id="aa492-124">Drugi, z wyjątkiem `ref` i `out` parametrów nie jest możliwe do tworzenia odwołań do struktury, która wyklucza ich użycia w różnych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="aa492-124">Second, except for `ref` and `out` parameters, it is not possible to create references to structs, which rules out their usage in a number of situations.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="aa492-125">[Poprzednie](classes-and-objects.md)
[dalej](arrays.md)</span><span class="sxs-lookup"><span data-stu-id="aa492-125">[Previous](classes-and-objects.md)
[Next](arrays.md)</span></span>
