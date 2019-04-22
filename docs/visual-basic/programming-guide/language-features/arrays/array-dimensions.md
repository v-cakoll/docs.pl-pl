---
title: Wymiary tablic w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 0b4e7c9e253f94e1e28700c8669d28799ab69d91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836938"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="d9c52-102">Wymiary tablic w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9c52-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="d9c52-103">A *wymiaru* jest kierunek, w którym mogą się różnić specyfikację elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="d9c52-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="d9c52-104">Tablica, która przechowuje Sprzedaż całkowita za każdy dzień miesiąca ma jeden wymiar (dzień miesiąca).</span><span class="sxs-lookup"><span data-stu-id="d9c52-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="d9c52-105">Tablica, która przechowuje Sprzedaż całkowita przez dział za każdy dzień miesiąca, ma dwa wymiary (numer działu i dzień miesiąca).</span><span class="sxs-lookup"><span data-stu-id="d9c52-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="d9c52-106">Nosi nazwę liczbę wymiarów tablicy zawierającej jej *ranga*.</span><span class="sxs-lookup"><span data-stu-id="d9c52-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9c52-107">Możesz użyć <xref:System.Array.Rank%2A> właściwości w celu określenia, ile wymiary tablicy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="d9c52-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="d9c52-108">Praca z wymiarami</span><span class="sxs-lookup"><span data-stu-id="d9c52-108">Working with Dimensions</span></span>  
 <span data-ttu-id="d9c52-109">Określenie elementu tablicy, podając *indeksu* lub *indeks dolny* dla wszystkich jej wymiarów.</span><span class="sxs-lookup"><span data-stu-id="d9c52-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="d9c52-110">Elementy są ciągłe wzdłuż każdego wymiaru z indeksu od 0 do najwyższego indeksu dla tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="d9c52-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="d9c52-111">Na poniższych ilustracjach przedstawiono koncepcyjny struktury tablic o różnym stopniu.</span><span class="sxs-lookup"><span data-stu-id="d9c52-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="d9c52-112">Każdy element na ilustracjach przedstawiono wartości indeksu, mających do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="d9c52-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="d9c52-113">Na przykład, możesz uzyskać dostęp pierwszego elementu w drugim wierszu dwuwymiarowej tablicy, określając indeksów `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="d9c52-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 ![Diagram przedstawiający Jednowymiarowa tablica.](./media/array-dimensions/one-dimensional-array.gif)  
  
 ![Diagram przedstawia dwuwymiarową tablicę.](./media/array-dimensions/two-dimensional-array.gif)  
  
 ![Diagram przedstawiający tablicę trójwymiarową.](./media/array-dimensions/three-dimensional-array.gif)  
  
### <a name="one-dimension"></a><span data-ttu-id="d9c52-117">Jeden wymiar</span><span class="sxs-lookup"><span data-stu-id="d9c52-117">One Dimension</span></span>  
 <span data-ttu-id="d9c52-118">Wiele macierzy mają tylko jeden wymiar, takie jak liczba osób w każdym wieku.</span><span class="sxs-lookup"><span data-stu-id="d9c52-118">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="d9c52-119">Jedynym wymaganiem, aby określić element jest okres ważności, dla którego ten element zawiera liczbę.</span><span class="sxs-lookup"><span data-stu-id="d9c52-119">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="d9c52-120">W związku z tym takiej tablicy używa tylko jednego indeksu.</span><span class="sxs-lookup"><span data-stu-id="d9c52-120">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="d9c52-121">Poniższy przykład deklaruje zmienną do przechowywania *jednowymiarową* wieku liczba w wieku od 0 do 120.</span><span class="sxs-lookup"><span data-stu-id="d9c52-121">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="d9c52-122">Dwa wymiary</span><span class="sxs-lookup"><span data-stu-id="d9c52-122">Two Dimensions</span></span>  
 <span data-ttu-id="d9c52-123">Niektórych tablic ma dwa wymiary, takie jak liczba urzędy każdego piętra każdego tworzenia na uczelniach.</span><span class="sxs-lookup"><span data-stu-id="d9c52-123">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="d9c52-124">Specyfikacja elementu wymaga numeru budynku i piętra, a każdy element przechowuje liczbę dla tej kombinacji budynku i piętra.</span><span class="sxs-lookup"><span data-stu-id="d9c52-124">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="d9c52-125">W związku z tym takiej tablicy wykorzystuje dwa indeksy.</span><span class="sxs-lookup"><span data-stu-id="d9c52-125">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="d9c52-126">Poniższy przykład deklaruje zmienną do przechowywania *dwuwymiarową tablicę* liczby office budynkach 0 za pomocą 40 i podłogi od 0 do 5.</span><span class="sxs-lookup"><span data-stu-id="d9c52-126">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="d9c52-127">Tablicy dwuwymiarowej jest również nazywany *prostokątny tablicy*.</span><span class="sxs-lookup"><span data-stu-id="d9c52-127">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="d9c52-128">Trzy wymiary</span><span class="sxs-lookup"><span data-stu-id="d9c52-128">Three Dimensions</span></span>  
 <span data-ttu-id="d9c52-129">Kilka tablic ma trzy wymiary, takie jak wartości w przestrzeni trójwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="d9c52-129">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="d9c52-130">Takie tablicy używa trzech indeksów, w tym przypadku reprezentujących x, y i z współrzędne przestrzeni fizycznej.</span><span class="sxs-lookup"><span data-stu-id="d9c52-130">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="d9c52-131">Poniższy przykład deklaruje zmienną do przechowywania *tablicy trójwymiarowej* air temperatur w różnych punktach trójwymiarowej woluminu.</span><span class="sxs-lookup"><span data-stu-id="d9c52-131">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="d9c52-132">Więcej niż trzech wymiarów</span><span class="sxs-lookup"><span data-stu-id="d9c52-132">More than Three Dimensions</span></span>  
 <span data-ttu-id="d9c52-133">Mimo że tablica może mieć maksymalnie 32 wymiarów, to rzadkość, aby mieć więcej niż trzy.</span><span class="sxs-lookup"><span data-stu-id="d9c52-133">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9c52-134">Po dodaniu wymiary tablicy, całkowita ilość miejsca, które są wymagane przez tablicę zwiększa znacznie, więc tablic wielowymiarowych użycie z rozwagą.</span><span class="sxs-lookup"><span data-stu-id="d9c52-134">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="d9c52-135">Przy użyciu różnych wymiarach</span><span class="sxs-lookup"><span data-stu-id="d9c52-135">Using Different Dimensions</span></span>  
 <span data-ttu-id="d9c52-136">Załóżmy, że chcesz śledzić kwot sprzedaży dla każdego dnia miesiąca obecne.</span><span class="sxs-lookup"><span data-stu-id="d9c52-136">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="d9c52-137">Jednowymiarowa tablica elementów 31 może deklarować jeden na każdy dzień miesiąca, w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="d9c52-137">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="d9c52-138">Teraz załóżmy, że chcesz śledzić te same informacje, nie tylko dla każdego dnia, miesiąca, ale także do każdego miesiąca w roku.</span><span class="sxs-lookup"><span data-stu-id="d9c52-138">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="d9c52-139">Może deklarować dwuwymiarową tablicę z 12 wierszy (w przypadku miesięcy) i 31 kolumn (dni), co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="d9c52-139">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="d9c52-140">Teraz załóżmy, że możesz zdecydować, że macierz przechowywać informacje o więcej niż jeden rok.</span><span class="sxs-lookup"><span data-stu-id="d9c52-140">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="d9c52-141">Jeśli chcesz śledzić kwot sprzedaży na 5 lat, można zadeklarować tablicy trójwymiarowej z warstwy 5, 12 wierszy i kolumn 31, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="d9c52-141">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="d9c52-142">Należy zauważyć, że ponieważ każdy indeks różni się od 0 do jego maksymalnej każdego wymiaru `salesAmounts` jest zadeklarowany jako jeden mniejsza niż wymagana długość danego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="d9c52-142">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="d9c52-143">Należy zauważyć, że rozmiar tablicy zwiększa się wraz z każdego nowego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="d9c52-143">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="d9c52-144">Trzy rozmiary w powyższych przykładach są odpowiednio 31, 372 i 1,860 elementów.</span><span class="sxs-lookup"><span data-stu-id="d9c52-144">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9c52-145">Można utworzyć tablicę, bez używania `Dim` instrukcji lub `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d9c52-145">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="d9c52-146">Na przykład, można wywołać <xref:System.Array.CreateInstance%2A> metody lub innego składnika można przekazać swój kod tablica utworzona w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="d9c52-146">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="d9c52-147">Takie tablica ma dolną granicę niż 0.</span><span class="sxs-lookup"><span data-stu-id="d9c52-147">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="d9c52-148">Można zawsze sprawdzić, dolna granica wymiaru przy użyciu <xref:System.Array.GetLowerBound%2A> metody lub `LBound` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9c52-148">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c52-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9c52-149">See also</span></span>

- [<span data-ttu-id="d9c52-150">Tablice</span><span class="sxs-lookup"><span data-stu-id="d9c52-150">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d9c52-151">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="d9c52-151">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
