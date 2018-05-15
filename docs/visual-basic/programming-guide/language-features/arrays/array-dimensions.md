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
ms.openlocfilehash: cf295288dd034d744dceb71b5c58278be5cc2a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="8c4e0-102">Wymiary tablic w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c4e0-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="8c4e0-103">A *wymiaru* jest kierunek, w którym można wybrać różne specyfikacje elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="8c4e0-104">Tablica, która przechowuje sprzedaży całkowitą dla każdego dnia, miesiąca ma jeden wymiar (dzień miesiąca).</span><span class="sxs-lookup"><span data-stu-id="8c4e0-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="8c4e0-105">Tablica, która przechowuje sprzedaży całkowita przez dział dla każdego dnia, miesiąca ma dwóch wymiarów (numer działu i dzień miesiąca).</span><span class="sxs-lookup"><span data-stu-id="8c4e0-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="8c4e0-106">Nazywa się liczby wymiarów tablicy nie ma jej *rangę*.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c4e0-107">Można użyć <xref:System.Array.Rank%2A> właściwości w celu określenia liczby wymiarów tablicy nie ma.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="8c4e0-108">Praca z wymiarami</span><span class="sxs-lookup"><span data-stu-id="8c4e0-108">Working with Dimensions</span></span>  
 <span data-ttu-id="8c4e0-109">Określ element tablicy podając *indeksu* lub *indeks dolny* dla każdego z jego wymiarów.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="8c4e0-110">Elementy są ciągłe wzdłuż każdego wymiaru z indeksem 0 za pomocą najwyższy indeksu dla tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="8c4e0-111">Na poniższych ilustracjach przedstawiono koncepcyjnej struktury tablic o różnym stopniu.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="8c4e0-112">Każdy element na ilustracjach przedstawiono wartości indeksów, które do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="8c4e0-113">Na przykład można dostępu pierwszym elementem w drugim wierszu tablicą dwuwymiarową określając indeksów `(1, 0)`.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="8c4e0-114">![Graficzny diagram jednego&#45;tablicą wielowymiarową](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="8c4e0-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="8c4e0-115">Jednowymiarowa tablica</span><span class="sxs-lookup"><span data-stu-id="8c4e0-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="8c4e0-116">![Graficzny diagram dwóch&#45;tablicą wielowymiarową](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="8c4e0-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="8c4e0-117">tablicą dwuwymiarową</span><span class="sxs-lookup"><span data-stu-id="8c4e0-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="8c4e0-118">![Graficzny diagram trzech&#45;tablicą wielowymiarową](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="8c4e0-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="8c4e0-119">tablicą trójwymiarową</span><span class="sxs-lookup"><span data-stu-id="8c4e0-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="8c4e0-120">Jeden wymiar</span><span class="sxs-lookup"><span data-stu-id="8c4e0-120">One Dimension</span></span>  
 <span data-ttu-id="8c4e0-121">Wiele tablic mieć tylko jeden wymiar, takie jak liczba osób każdego wieku.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="8c4e0-122">Jedynym wymaganiem, aby określić elementu jest okres ważności, dla którego ten element zawiera wartość licznika.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="8c4e0-123">W związku z tym takie tablicy używa tylko jeden indeks.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="8c4e0-124">Poniższy przykład deklaruje zmienną do przechowywania *jednowymiarową* wieku liczba wieku od 0 do 120.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="8c4e0-125">Dwóch wymiarów</span><span class="sxs-lookup"><span data-stu-id="8c4e0-125">Two Dimensions</span></span>  
 <span data-ttu-id="8c4e0-126">Niektóre tablice zawierają dwóch wymiarów, takich jak liczba oddziałów na każde piętro każdego tworzenia w firmy.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="8c4e0-127">Specyfikacja elementu wymaga zarówno numeru budynku i piętra, a każdy element zawiera liczbę elementów w tym kombinację budynku i piętra.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="8c4e0-128">W związku z tym takie tablicy używa dwóch indeksów.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="8c4e0-129">Poniższy przykład deklaruje zmienną do przechowywania *tablicą dwuwymiarową* liczników pakietu office, budynki 0 za pomocą 40 i piętra od 0 do 5.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="8c4e0-130">Skrót jest tablicą dwuwymiarową *tablicy regularnej*.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="8c4e0-131">Trzy wymiary</span><span class="sxs-lookup"><span data-stu-id="8c4e0-131">Three Dimensions</span></span>  
 <span data-ttu-id="8c4e0-132">Tablice kilka ma trzy wymiarów, takich jak wartości w przestrzeni trójwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="8c4e0-133">Takie tablicy używa trzech indeksów, które reprezentują w takim przypadku x, y oraz współrzędne z fizycznego miejsca.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="8c4e0-134">Poniższy przykład deklaruje zmienną do przechowywania *tablicą trójwymiarową* lotniczego temperatur w różnych miejscach trójwymiarowy woluminu.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="8c4e0-135">Więcej niż trzech wymiarów</span><span class="sxs-lookup"><span data-stu-id="8c4e0-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="8c4e0-136">Mimo że tablica może mieć maksymalnie 32 wymiarów, jest rzadko ma więcej niż trzy.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c4e0-137">Dodaj wymiary do tablicy, całkowita ilość miejsca, które są wymagane przez tablicę zwiększa znacznie, tak tablice wielowymiarowe Użyj ostrożność.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="8c4e0-138">Przy użyciu różnych wymiarach</span><span class="sxs-lookup"><span data-stu-id="8c4e0-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="8c4e0-139">Załóżmy, że chcesz śledzić kwoty sprzedaży dla każdego dnia, miesiąca występuje.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="8c4e0-140">Jednowymiarowa tablica elementów 31, mogą zadeklarować po jednej dla każdego dnia, miesiąca, jak w poniższym przykładzie przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="8c4e0-141">Teraz załóżmy, że chcesz śledzić te same informacje, nie tylko dla każdego dnia, miesiąca, ale też co miesiąc w roku.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="8c4e0-142">Może zadeklarować jest tablicą dwuwymiarową z 12 wierszy (dla miesięcy) i 31 kolumn (dni), jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="8c4e0-143">Teraz załóżmy, że użytkownik chce mieć macierzy przechowywania informacji przez więcej niż jeden rok.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="8c4e0-144">Jeśli chcesz śledzić kwoty sprzedaży 5 lat, można zadeklarować jest tablicą trójwymiarową z warstwy 5, 12 wierszy i kolumn 31, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="8c4e0-145">Należy zauważyć, że każdy indeks różne od 0 do jego maksymalnej każdego wymiaru `salesAmounts` jest zadeklarowany jako jeden mniejszy niż wymagana długość dla tego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="8c4e0-146">Należy pamiętać, że rozmiar tablicy zwiększa się wraz z każdego nowego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="8c4e0-147">Trzy rozmiary w powyższych przykładach są odpowiednio 31, 372 i 1,860 elementów.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c4e0-148">Można utworzyć tablicy bez używania `Dim` instrukcji lub `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="8c4e0-149">Na przykład można wywołać <xref:System.Array.CreateInstance%2A> metody lub innego składnika można przekazać swój kod tablicy utworzonej w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="8c4e0-150">Takie tablicy mogą mieć dolną granicą inną niż 0.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="8c4e0-151">Należy zawsze przetestować dla dolna granica wymiaru przy użyciu <xref:System.Array.GetLowerBound%2A> metody lub `LBound` funkcji.</span><span class="sxs-lookup"><span data-stu-id="8c4e0-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4e0-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c4e0-152">See Also</span></span>  
 [<span data-ttu-id="8c4e0-153">Tablice</span><span class="sxs-lookup"><span data-stu-id="8c4e0-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="8c4e0-154">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="8c4e0-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
