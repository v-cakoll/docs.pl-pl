---
title: Dynamicznie określaj filtry predykatu w czasie wykonywania (LINQ w języku C#)
description: Dowiedz się, jak dynamicznie określać filtry predykatu w czasie wykonywania przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659946"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="8ee93-103">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="8ee93-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="8ee93-104">W niektórych przypadkach nie wiesz, aż do czasu wykonywania, ile predykatów `where` trzeba zastosować do elementów źródłowych w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8ee93-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="8ee93-105">Jednym ze sposobów dynamicznego określania wielu filtrów <xref:System.Linq.Enumerable.Contains%2A> predykatu jest użycie metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8ee93-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="8ee93-106">Przykład jest skonstruowany na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="8ee93-106">The example is constructed in two ways.</span></span> <span data-ttu-id="8ee93-107">Po pierwsze projekt jest uruchamiany przez filtrowanie wartości, które są dostarczane w programie.</span><span class="sxs-lookup"><span data-stu-id="8ee93-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="8ee93-108">Następnie projekt jest uruchamiany ponownie przy użyciu danych wejściowych dostarczonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8ee93-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="8ee93-109">Aby filtrować za pomocą metody Contains</span><span class="sxs-lookup"><span data-stu-id="8ee93-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="8ee93-110">Otwórz nową aplikację konsoli `PredicateFilters`i najmiej nazwę .</span><span class="sxs-lookup"><span data-stu-id="8ee93-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="8ee93-111">Skopiuj `StudentClass` klasę z [query kolekcji obiektów](query-a-collection-of-objects.md) `PredicateFilters` i wklej ją do obszaru nazw pod klasą `Program`.</span><span class="sxs-lookup"><span data-stu-id="8ee93-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="8ee93-112">`StudentClass`zawiera listę `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="8ee93-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="8ee93-113">Skomentuj `Main` metodę `StudentClass`w pliku .</span><span class="sxs-lookup"><span data-stu-id="8ee93-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="8ee93-114">Zamień klasę `Program` na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="8ee93-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="8ee93-115">Dodaj następujący wiersz `Main` do metody `DynamicPredicates`w klasie `ids`, pod deklaracją .</span><span class="sxs-lookup"><span data-stu-id="8ee93-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="8ee93-116">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="8ee93-116">Run the project.</span></span>

7. <span data-ttu-id="8ee93-117">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8ee93-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="8ee93-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="8ee93-118">Garcia: 114</span></span>

     <span data-ttu-id="8ee93-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="8ee93-119">O'Donnell: 112</span></span>

     <span data-ttu-id="8ee93-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="8ee93-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="8ee93-121">Następnym krokiem jest ponowne uruchomienie projektu, tym razem przy użyciu `ids`danych wejściowych wprowadzonych w czasie wykonywania zamiast tablicy .</span><span class="sxs-lookup"><span data-stu-id="8ee93-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="8ee93-122">Zmień `QueryByID(ids)` `QueryByID(args)` na `Main` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="8ee93-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="8ee93-123">Uruchom projekt z argumentami `122 117 120 115`wiersza polecenia .</span><span class="sxs-lookup"><span data-stu-id="8ee93-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="8ee93-124">Po uruchomieniu projektu te wartości `args`stają się elementami `Main` parametru metody.</span><span class="sxs-lookup"><span data-stu-id="8ee93-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method.</span></span>

10. <span data-ttu-id="8ee93-125">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="8ee93-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="8ee93-126">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="8ee93-126">Adams: 120</span></span>

     <span data-ttu-id="8ee93-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="8ee93-127">Feng: 117</span></span>

     <span data-ttu-id="8ee93-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="8ee93-128">Garcia: 115</span></span>

     <span data-ttu-id="8ee93-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="8ee93-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="8ee93-130">Aby filtrować przy użyciu instrukcji switch</span><span class="sxs-lookup"><span data-stu-id="8ee93-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="8ee93-131">Instrukcja służy `switch` do wybierania spośród wstępnie określonych kwerend alternatywnych.</span><span class="sxs-lookup"><span data-stu-id="8ee93-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="8ee93-132">W poniższym `studentQuery` przykładzie używa `where` innej klauzuli w zależności od poziomu klasy lub roku, jest określony w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8ee93-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="8ee93-133">Skopiuj następującą `DynamicPredicates`metodę i wklej ją do klasy .</span><span class="sxs-lookup"><span data-stu-id="8ee93-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="8ee93-134">W `Main` metodzie zastąp wywołanie `QueryByID` następujące wywołanie, które `args` wysyła pierwszy `QueryByYear(args[0])`element z tablicy jako jego argument: .</span><span class="sxs-lookup"><span data-stu-id="8ee93-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="8ee93-135">Uruchom projekt z argumentem wiersza polecenia o wartości całkowitej z wartością od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="8ee93-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ee93-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ee93-136">See also</span></span>

- [<span data-ttu-id="8ee93-137">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8ee93-137">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="8ee93-138">gdzie klauzula</span><span class="sxs-lookup"><span data-stu-id="8ee93-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
