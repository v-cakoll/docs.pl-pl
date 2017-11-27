---
title: "Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym"
description: "Jak dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 06bc594ac1357e7dca6c182fa28310559a79875c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="46bf9-104">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="46bf9-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="46bf9-105">W niektórych przypadkach nie wiadomo, do czasu wykonywania ile predykaty ma być stosowany do elementów źródła w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="46bf9-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="46bf9-106">Jednym ze sposobów dynamiczne określanie filtrów predykatów wielu jest użycie <xref:System.Linq.Enumerable.Contains%2A> metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="46bf9-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="46bf9-107">Przykładzie jest tworzony na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="46bf9-107">The example is constructed in two ways.</span></span> <span data-ttu-id="46bf9-108">Po pierwsze projekt jest uruchamiany przez filtrowanie wartości, które znajdują się w programie.</span><span class="sxs-lookup"><span data-stu-id="46bf9-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="46bf9-109">Projekt jest następnie uruchom ponownie przy użyciu danych wejściowych dostarczonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="46bf9-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="46bf9-110">Aby filtrować przy użyciu metody zawiera</span><span class="sxs-lookup"><span data-stu-id="46bf9-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="46bf9-111">Otwórz nową aplikację konsoli i nadaj mu nazwę `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="46bf9-112">Kopiuj `StudentClass` klasę z [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md) i wklej go do obszaru nazw `PredicateFilters` poniżej klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="46bf9-113">`StudentClass`zawiera listę `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="46bf9-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="46bf9-114">Komentarz `Main` metoda `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="46bf9-115">Zastąp klasę `Program` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="46bf9-115">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="46bf9-116">Dodaj następujący wiersz do `Main` metody w klasie `DynamicPredicates`, w obszarze deklaracja `ids`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-116">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="46bf9-117">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="46bf9-117">Run the project.</span></span>  
  
7.  <span data-ttu-id="46bf9-118">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="46bf9-118">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="46bf9-119">Kowalski: 114</span><span class="sxs-lookup"><span data-stu-id="46bf9-119">Garcia: 114</span></span>  
  
     <span data-ttu-id="46bf9-120">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="46bf9-120">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="46bf9-121">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="46bf9-121">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="46bf9-122">Następnym krokiem jest ponowne uruchomienie projektu, teraz przy użyciu danych wejściowych wprowadzona w czasie wykonywania, zamiast tablicy `ids`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-122">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="46bf9-123">Zmień `QueryByID(ids)` do `QueryByID(args)` w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="46bf9-123">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="46bf9-124">Uruchom projekt z argumenty wiersza polecenia `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-124">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="46bf9-125">Po uruchomieniu projektu, te wartości stają się elementami `args`, parametr `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="46bf9-125">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="46bf9-126">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="46bf9-126">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="46bf9-127">Zawadzki: 120</span><span class="sxs-lookup"><span data-stu-id="46bf9-127">Adams: 120</span></span>  
  
     <span data-ttu-id="46bf9-128">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="46bf9-128">Feng: 117</span></span>  
  
     <span data-ttu-id="46bf9-129">Kowalski: 115</span><span class="sxs-lookup"><span data-stu-id="46bf9-129">Garcia: 115</span></span>  
  
     <span data-ttu-id="46bf9-130">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="46bf9-130">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="46bf9-131">Aby filtrować za pomocą instrukcji switch</span><span class="sxs-lookup"><span data-stu-id="46bf9-131">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="46bf9-132">Można użyć `switch` instrukcji, aby wybrać spośród wstępnie określone alternatywne zapytania.</span><span class="sxs-lookup"><span data-stu-id="46bf9-132">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="46bf9-133">W poniższym przykładzie `studentQuery` używa innej `where` klauzuli w zależności od tego, które klasy poziom lub rok, jest określona w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="46bf9-133">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="46bf9-134">Skopiuj następujące metody i wklej go do klasy `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-134">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="46bf9-135">W `Main` metody, Zastąp wywołanie `QueryByID` następujące wywołanie, który wysyła pierwszego elementu z `args` tablicy jako jej argument: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="46bf9-135">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="46bf9-136">Uruchom projekt z argumentem wiersza polecenia liczbę całkowitą z przedziału od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="46bf9-136">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="46bf9-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46bf9-137">See Also</span></span>  
 [<span data-ttu-id="46bf9-138">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="46bf9-138">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="46bf9-139">gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="46bf9-139">where clause</span></span>](../language-reference/keywords/where-clause.md)
