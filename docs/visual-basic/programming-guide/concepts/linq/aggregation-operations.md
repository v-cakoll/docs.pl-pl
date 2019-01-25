---
title: Operacje agregacji (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 7daf4f653d3796eaa3ae426fdbf86a89ebdd2dc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735386"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="e462a-102">Operacje agregacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e462a-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="e462a-103">Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości.</span><span class="sxs-lookup"><span data-stu-id="e462a-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="e462a-104">Przykładem operacji agregacji obliczania średniej temperatury codzienne z miesięcznej codzienne wartości temperatury.</span><span class="sxs-lookup"><span data-stu-id="e462a-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="e462a-105">Poniższa ilustracja przedstawia wyniki dwie operacje różnych agregacji w sekwencji liczb.</span><span class="sxs-lookup"><span data-stu-id="e462a-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="e462a-106">Pierwszą operacją sumuje się liczby.</span><span class="sxs-lookup"><span data-stu-id="e462a-106">The first operation sums the numbers.</span></span> <span data-ttu-id="e462a-107">Druga operacja zwraca maksymalną wartość w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e462a-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="e462a-108">![Operacje agregacji LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="e462a-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="e462a-109">Metody standardowego operatora zapytań, które wykonują operacje agregacji są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e462a-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e462a-110">Metody</span><span class="sxs-lookup"><span data-stu-id="e462a-110">Methods</span></span>  
  
|<span data-ttu-id="e462a-111">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="e462a-111">Method Name</span></span>|<span data-ttu-id="e462a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e462a-112">Description</span></span>|<span data-ttu-id="e462a-113">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e462a-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="e462a-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="e462a-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="e462a-115">Agregowanie</span><span class="sxs-lookup"><span data-stu-id="e462a-115">Aggregate</span></span>|<span data-ttu-id="e462a-116">Wykonuje operację agregacji niestandardowej na podstawie wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e462a-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="e462a-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e462a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e462a-118">Średnia</span><span class="sxs-lookup"><span data-stu-id="e462a-118">Average</span></span>|<span data-ttu-id="e462a-119">Oblicza średnią wartość zbiór wartości.</span><span class="sxs-lookup"><span data-stu-id="e462a-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e462a-120">Licznik</span><span class="sxs-lookup"><span data-stu-id="e462a-120">Count</span></span>|<span data-ttu-id="e462a-121">Liczba elementów w kolekcji, opcjonalnie tylko te elementy, które spełniają wymagania funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="e462a-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e462a-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="e462a-122">LongCount</span></span>|<span data-ttu-id="e462a-123">Liczba elementów w dużych kolekcji, opcjonalnie tylko te elementy, które spełniają wymagania funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="e462a-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e462a-124">Maks.</span><span class="sxs-lookup"><span data-stu-id="e462a-124">Max</span></span>|<span data-ttu-id="e462a-125">Określa maksymalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e462a-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e462a-126">Min.</span><span class="sxs-lookup"><span data-stu-id="e462a-126">Min</span></span>|<span data-ttu-id="e462a-127">Określa minimalną wartość w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e462a-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e462a-128">Suma</span><span class="sxs-lookup"><span data-stu-id="e462a-128">Sum</span></span>|<span data-ttu-id="e462a-129">Oblicza sumę wartości w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e462a-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="e462a-130">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="e462a-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="e462a-131">Średnia</span><span class="sxs-lookup"><span data-stu-id="e462a-131">Average</span></span>  
 <span data-ttu-id="e462a-132">Poniższy przykład kodu wykorzystuje `Aggregate Into Average` klauzuli w języku Visual Basic, aby obliczyć średnią temperaturę w tablicy liczb, które reprezentują temperatury.</span><span class="sxs-lookup"><span data-stu-id="e462a-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a><span data-ttu-id="e462a-133">Licznik</span><span class="sxs-lookup"><span data-stu-id="e462a-133">Count</span></span>  
 <span data-ttu-id="e462a-134">Poniższy przykład kodu wykorzystuje `Aggregate Into Count` klauzuli w Visual Basic, aby określić liczbę wartości w tablicy, które są większe niż lub równy 80.</span><span class="sxs-lookup"><span data-stu-id="e462a-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a><span data-ttu-id="e462a-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="e462a-135">LongCount</span></span>  
 <span data-ttu-id="e462a-136">Poniższy przykład kodu wykorzystuje `Aggregate Into LongCount` klauzuli, aby określić liczbę wartości w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e462a-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a><span data-ttu-id="e462a-137">Maks.</span><span class="sxs-lookup"><span data-stu-id="e462a-137">Max</span></span>  
 <span data-ttu-id="e462a-138">Poniższy przykład kodu wykorzystuje `Aggregate Into Max` klauzuli do obliczania maksymalna temperatura w tablicy liczb, które reprezentują temperatury.</span><span class="sxs-lookup"><span data-stu-id="e462a-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a><span data-ttu-id="e462a-139">Min.</span><span class="sxs-lookup"><span data-stu-id="e462a-139">Min</span></span>  
 <span data-ttu-id="e462a-140">Poniższy przykład kodu wykorzystuje `Aggregate Into Min` klauzuli do obliczania minimalna temperatura w tablicy liczb, które reprezentują temperatury.</span><span class="sxs-lookup"><span data-stu-id="e462a-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a><span data-ttu-id="e462a-141">Suma</span><span class="sxs-lookup"><span data-stu-id="e462a-141">Sum</span></span>  
 <span data-ttu-id="e462a-142">Poniższy przykład kodu wykorzystuje `Aggregate Into Sum` klauzuli w celu obliczania wydatków łączna ilość z tablicy wartości, które reprezentują wydatki.</span><span class="sxs-lookup"><span data-stu-id="e462a-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e462a-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e462a-143">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="e462a-144">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e462a-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e462a-145">Klauzula Aggregate</span><span class="sxs-lookup"><span data-stu-id="e462a-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="e462a-146">Instrukcje: Obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e462a-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="e462a-147">Instrukcje: Liczba, Suma lub średnia danych</span><span class="sxs-lookup"><span data-stu-id="e462a-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="e462a-148">Instrukcje: Znajdowanie wartości minimalnej lub maksymalnej w wyniku zapytania</span><span class="sxs-lookup"><span data-stu-id="e462a-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="e462a-149">Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e462a-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="e462a-150">Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e462a-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
