---
title: Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym
description: Jak dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: fa3426a513758d8c30bf381ec480b9b8d12a5f81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287943"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="83c15-103">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="83c15-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="83c15-104">W niektórych przypadkach nie wiadomo, do czasu wykonywania ile predykaty ma być stosowany do elementów źródła w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="83c15-104">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="83c15-105">Jednym ze sposobów dynamiczne określanie filtrów predykatów wielu jest użycie <xref:System.Linq.Enumerable.Contains%2A> metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="83c15-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="83c15-106">Przykładzie jest tworzony na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="83c15-106">The example is constructed in two ways.</span></span> <span data-ttu-id="83c15-107">Po pierwsze projekt jest uruchamiany przez filtrowanie wartości, które znajdują się w programie.</span><span class="sxs-lookup"><span data-stu-id="83c15-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="83c15-108">Projekt jest następnie uruchom ponownie przy użyciu danych wejściowych dostarczonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83c15-108">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="83c15-109">Aby filtrować przy użyciu metody zawiera</span><span class="sxs-lookup"><span data-stu-id="83c15-109">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="83c15-110">Otwórz nową aplikację konsoli i nadaj mu nazwę `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="83c15-110">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="83c15-111">Kopiuj `StudentClass` klasę z [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md) i wklej go do obszaru nazw `PredicateFilters` poniżej klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="83c15-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="83c15-112">`StudentClass` zawiera listę `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="83c15-112">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="83c15-113">Komentarz `Main` metoda `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="83c15-113">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="83c15-114">Zastąp klasę `Program` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="83c15-114">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="83c15-115">Dodaj następujący wiersz do `Main` metody w klasie `DynamicPredicates`, w obszarze deklaracja `ids`.</span><span class="sxs-lookup"><span data-stu-id="83c15-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="83c15-116">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="83c15-116">Run the project.</span></span>  
  
7.  <span data-ttu-id="83c15-117">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="83c15-117">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="83c15-118">Kowalski: 114</span><span class="sxs-lookup"><span data-stu-id="83c15-118">Garcia: 114</span></span>  
  
     <span data-ttu-id="83c15-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="83c15-119">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="83c15-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="83c15-120">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="83c15-121">Następnym krokiem jest ponowne uruchomienie projektu, teraz przy użyciu danych wejściowych wprowadzona w czasie wykonywania, zamiast tablicy `ids`.</span><span class="sxs-lookup"><span data-stu-id="83c15-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="83c15-122">Zmień `QueryByID(ids)` do `QueryByID(args)` w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="83c15-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="83c15-123">Uruchom projekt z argumenty wiersza polecenia `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="83c15-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="83c15-124">Po uruchomieniu projektu, te wartości stają się elementami `args`, parametr `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="83c15-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="83c15-125">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="83c15-125">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="83c15-126">Zawadzki: 120</span><span class="sxs-lookup"><span data-stu-id="83c15-126">Adams: 120</span></span>  
  
     <span data-ttu-id="83c15-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="83c15-127">Feng: 117</span></span>  
  
     <span data-ttu-id="83c15-128">Kowalski: 115</span><span class="sxs-lookup"><span data-stu-id="83c15-128">Garcia: 115</span></span>  
  
     <span data-ttu-id="83c15-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="83c15-129">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="83c15-130">Aby filtrować za pomocą instrukcji switch</span><span class="sxs-lookup"><span data-stu-id="83c15-130">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="83c15-131">Można użyć `switch` instrukcji, aby wybrać spośród wstępnie określone alternatywne zapytania.</span><span class="sxs-lookup"><span data-stu-id="83c15-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="83c15-132">W poniższym przykładzie `studentQuery` używa innej `where` klauzuli w zależności od tego, które klasy poziom lub rok, jest określona w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="83c15-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="83c15-133">Skopiuj następujące metody i wklej go do klasy `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="83c15-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="83c15-134">W `Main` metody, Zastąp wywołanie `QueryByID` następujące wywołanie, który wysyła pierwszego elementu z `args` tablicy jako jej argument: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="83c15-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="83c15-135">Uruchom projekt z argumentem wiersza polecenia liczbę całkowitą z przedziału od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="83c15-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="83c15-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83c15-136">See Also</span></span>  
 [<span data-ttu-id="83c15-137">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="83c15-137">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="83c15-138">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="83c15-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
