---
title: Wymiary tablicy
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 12e983ae62fa9f9ea762d434ffe5b73873a4a2e8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351909"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="fe380-102">Wymiary tablic w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe380-102">Array Dimensions in Visual Basic</span></span>

<span data-ttu-id="fe380-103">*Wymiar* to kierunek, w którym można zmienić specyfikację elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="fe380-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="fe380-104">Tablica, która przechowuje sumę sprzedaży dla każdego dnia miesiąca, ma jeden wymiar (dzień miesiąca).</span><span class="sxs-lookup"><span data-stu-id="fe380-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="fe380-105">Tablica zawierająca sumę sprzedaży według działu dla każdego dnia miesiąca ma dwa wymiary (numer działu i dzień miesiąca).</span><span class="sxs-lookup"><span data-stu-id="fe380-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="fe380-106">Liczba wymiarów, które tablica ma określać jej *rangę*.</span><span class="sxs-lookup"><span data-stu-id="fe380-106">The number of dimensions an array has is called its *rank*.</span></span>

> [!NOTE]
> <span data-ttu-id="fe380-107">Aby określić, ile wymiarów ma tablica, można użyć właściwości <xref:System.Array.Rank%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe380-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>

## <a name="working-with-dimensions"></a><span data-ttu-id="fe380-108">Praca z wymiarami</span><span class="sxs-lookup"><span data-stu-id="fe380-108">Working with Dimensions</span></span>

<span data-ttu-id="fe380-109">Należy określić element tablicy przez dostarczenie *indeksu lub indeks* *dolny* dla każdego z jego wymiarów.</span><span class="sxs-lookup"><span data-stu-id="fe380-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="fe380-110">Elementy są ciągłe wzdłuż każdego wymiaru od indeksu 0 do najwyższego indeksu dla tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="fe380-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>

<span data-ttu-id="fe380-111">Na poniższych ilustracjach przedstawiono strukturę koncepcyjną tablic o różnych rangach.</span><span class="sxs-lookup"><span data-stu-id="fe380-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="fe380-112">Każdy element na ilustracjach przedstawia wartości indeksu, które uzyskują do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="fe380-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="fe380-113">Na przykład można uzyskać dostęp do pierwszego elementu drugiego wiersza tablicy dwuwymiarowej przez określenie indeksów `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="fe380-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>

![Diagram przedstawiający tablicę jednowymiarową.](./media/array-dimensions/one-dimensional-array.gif)

![Diagram przedstawiający dwuwymiarową tablicę.](./media/array-dimensions/two-dimensional-array.gif)

![Diagram przedstawiający trójwymiarową tablicę.](./media/array-dimensions/three-dimensional-array.gif)

### <a name="one-dimension"></a><span data-ttu-id="fe380-117">Jeden wymiar</span><span class="sxs-lookup"><span data-stu-id="fe380-117">One Dimension</span></span>

<span data-ttu-id="fe380-118">Wiele tablic ma tylko jeden wymiar, taki jak liczba osób każdego wieku.</span><span class="sxs-lookup"><span data-stu-id="fe380-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="fe380-119">Jedynym wymaganiem do określenia elementu jest wiek, dla którego ten element przechowuje liczbę.</span><span class="sxs-lookup"><span data-stu-id="fe380-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="fe380-120">W związku z tym, taka tablica używa tylko jednego indeksu.</span><span class="sxs-lookup"><span data-stu-id="fe380-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="fe380-121">Poniższy przykład deklaruje zmienną do przechowywania *jednowymiarowej tablicy* liczby lat od 0 do 120.</span><span class="sxs-lookup"><span data-stu-id="fe380-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>

```vb
Dim ageCounts(120) As UInteger
```

### <a name="two-dimensions"></a><span data-ttu-id="fe380-122">Dwa wymiary</span><span class="sxs-lookup"><span data-stu-id="fe380-122">Two Dimensions</span></span>

<span data-ttu-id="fe380-123">Niektóre tablice mają dwa wymiary, takie jak liczba biur w poszczególnych piętrach każdego budynku w kampusie.</span><span class="sxs-lookup"><span data-stu-id="fe380-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="fe380-124">Specyfikacja elementu wymaga zarówno numeru budynku, jak i podłogi, a każdy element przechowuje liczbę dla tej kombinacji budynku i piętra.</span><span class="sxs-lookup"><span data-stu-id="fe380-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="fe380-125">W związku z tym, taka tablica używa dwóch indeksów.</span><span class="sxs-lookup"><span data-stu-id="fe380-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="fe380-126">Poniższy przykład deklaruje zmienną do przechowywania *dwuwymiarowej tablicy* liczników pakietu Office dla budynków od 0 do 40 i podłóg 0 – 5.</span><span class="sxs-lookup"><span data-stu-id="fe380-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>

```vb
Dim officeCounts(40, 5) As Byte
```

<span data-ttu-id="fe380-127">Dwuwymiarowa tablica jest również nazywana *tablicą prostokątną*.</span><span class="sxs-lookup"><span data-stu-id="fe380-127">A two-dimensional array is also called a *rectangular array*.</span></span>

### <a name="three-dimensions"></a><span data-ttu-id="fe380-128">Trzy wymiary</span><span class="sxs-lookup"><span data-stu-id="fe380-128">Three Dimensions</span></span>

<span data-ttu-id="fe380-129">Kilka tablic ma trzy wymiary, takie jak wartości w trójwymiarowej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="fe380-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="fe380-130">Taka tablica używa trzech indeksów, co w tym przypadku reprezentuje współrzędne x, y i z miejsca fizycznego.</span><span class="sxs-lookup"><span data-stu-id="fe380-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="fe380-131">Poniższy przykład deklaruje zmienną do przechowywania *trójwymiarowej tablicy* temperatur w różnych punktach na trójwymiarowym woluminie.</span><span class="sxs-lookup"><span data-stu-id="fe380-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>

```vb
Dim airTemperatures(99, 99, 24) As Single
```

### <a name="more-than-three-dimensions"></a><span data-ttu-id="fe380-132">Więcej niż trzy wymiary</span><span class="sxs-lookup"><span data-stu-id="fe380-132">More than Three Dimensions</span></span>

<span data-ttu-id="fe380-133">Chociaż tablica może mieć maksymalnie 32 wymiarów, bardzo rzadko ma więcej niż trzy.</span><span class="sxs-lookup"><span data-stu-id="fe380-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>

> [!NOTE]
> <span data-ttu-id="fe380-134">Po dodaniu wymiarów do tablicy łączny magazyn wymagany przez tablicę jest znacząco zwiększany, więc używaj tablic wielowymiarowych z opieką.</span><span class="sxs-lookup"><span data-stu-id="fe380-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>

## <a name="using-different-dimensions"></a><span data-ttu-id="fe380-135">Korzystanie z różnych wymiarów</span><span class="sxs-lookup"><span data-stu-id="fe380-135">Using Different Dimensions</span></span>

<span data-ttu-id="fe380-136">Załóżmy, że chcesz śledzić kwoty sprzedaży dla każdego dnia bieżącego miesiąca.</span><span class="sxs-lookup"><span data-stu-id="fe380-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="fe380-137">Można zadeklarować tablicę jednowymiarową z 31 elementami, jedną dla każdego dnia miesiąca, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe380-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>

```vb
Dim salesAmounts(30) As Double
```

<span data-ttu-id="fe380-138">Teraz Załóżmy, że chcesz śledzić te same informacje nie tylko dla każdego dnia miesiąca, ale również dla każdego miesiąca roku.</span><span class="sxs-lookup"><span data-stu-id="fe380-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="fe380-139">Można zadeklarować dwuwymiarową tablicę z 12 wierszami (przez miesiące) i 31 kolumn (w dniach), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe380-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>

```vb
Dim salesAmounts(11, 30) As Double
```

<span data-ttu-id="fe380-140">Teraz Załóżmy, że chcesz, aby tablica zawierała informacje przez więcej niż jeden rok.</span><span class="sxs-lookup"><span data-stu-id="fe380-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="fe380-141">Jeśli chcesz śledzić kwoty sprzedaży przez 5 lat, możesz zadeklarować trójwymiarową tablicę z 5 warstwami, 12 wierszami i 31 kolumnami, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fe380-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>

```vb
Dim salesAmounts(4, 11, 30) As Double
```

<span data-ttu-id="fe380-142">Należy pamiętać, że ponieważ każdy indeks różni się od 0 do maksimum, każdy wymiar `salesAmounts` jest zadeklarowany jako jeden mniejszy niż wymagana długość dla tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="fe380-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="fe380-143">Zwróć uwagę na to, że rozmiar tablicy rośnie wraz z każdym nowym wymiarem.</span><span class="sxs-lookup"><span data-stu-id="fe380-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="fe380-144">Trzy powyższe wielkości w powyższych przykładach mają odpowiednio 31, 372 i 1 860 elementów.</span><span class="sxs-lookup"><span data-stu-id="fe380-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="fe380-145">Można utworzyć tablicę bez użycia instrukcji `Dim` lub klauzuli `New`.</span><span class="sxs-lookup"><span data-stu-id="fe380-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="fe380-146">Na przykład można wywołać metodę <xref:System.Array.CreateInstance%2A> lub inny składnik może przekazać kod w ten sposób tablicę utworzoną w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="fe380-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="fe380-147">Taka tablica może mieć dolną granicę inną niż 0.</span><span class="sxs-lookup"><span data-stu-id="fe380-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="fe380-148">Zawsze możesz testować dolną granicę wymiaru przy użyciu metody <xref:System.Array.GetLowerBound%2A> lub funkcji `LBound`.</span><span class="sxs-lookup"><span data-stu-id="fe380-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe380-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe380-149">See also</span></span>

- [<span data-ttu-id="fe380-150">Tablice</span><span class="sxs-lookup"><span data-stu-id="fe380-150">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="fe380-151">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="fe380-151">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
