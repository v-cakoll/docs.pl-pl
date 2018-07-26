---
title: Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym (LINQ w C#)
description: Dowiedz się, jak i dynamiczne określanie filtrów predykatów w czasie wykonywania za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 7051d7c754a0db29771a2e03a3b624c0e434eecd
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404093"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="e6eff-103">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="e6eff-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="e6eff-104">W niektórych przypadkach nie wiesz, do czasu wykonywania ile predykaty, należy zastosować do elementów źródła w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e6eff-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="e6eff-105">Jednym ze sposobów dynamiczne określanie filtrów predykatów wielu jest użycie <xref:System.Linq.Enumerable.Contains%2A> metodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e6eff-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="e6eff-106">Przykład jest tworzona na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="e6eff-106">The example is constructed in two ways.</span></span> <span data-ttu-id="e6eff-107">Po pierwsze projekt jest uruchamiane przez filtrowanie według wartości, które znajdują się w programie.</span><span class="sxs-lookup"><span data-stu-id="e6eff-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="e6eff-108">Projekt jest następnie uruchom ponownie przy użyciu danych wejściowych dostarczonych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e6eff-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="e6eff-109">Aby filtrować przy użyciu metody zawiera</span><span class="sxs-lookup"><span data-stu-id="e6eff-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="e6eff-110">Otwórz nową aplikację konsolową i nadaj mu nazwę `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="e6eff-111">Kopiuj `StudentClass` klasy z [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md) i wklej go do obszaru nazw `PredicateFilters` poniżej klasy `Program`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="e6eff-112">`StudentClass` zawiera listę `Student` obiektów.</span><span class="sxs-lookup"><span data-stu-id="e6eff-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="e6eff-113">Komentarz `Main` method in Class metoda `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="e6eff-114">Zastąp klasę `Program` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="e6eff-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="e6eff-115">Dodaj następujący wiersz do `Main` metody w klasie `DynamicPredicates`, w ramach deklaracji `ids`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="e6eff-116">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="e6eff-116">Run the project.</span></span>

7. <span data-ttu-id="e6eff-117">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e6eff-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="e6eff-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="e6eff-118">Garcia: 114</span></span>

     <span data-ttu-id="e6eff-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="e6eff-119">O'Donnell: 112</span></span>

     <span data-ttu-id="e6eff-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="e6eff-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="e6eff-121">Następnym krokiem jest, aby ponownie uruchomić projekt, tym razem przy użyciu danych wejściowych wprowadzić w czasie wykonywania, zamiast tablicy `ids`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="e6eff-122">Zmiana `QueryByID(ids)` do `QueryByID(args)` w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="e6eff-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="e6eff-123">Uruchom projekt z argumentami wiersza polecenia `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="e6eff-124">Po uruchomieniu projektu, te wartości stają się elementy `args`, parametr `Main` metody...</span><span class="sxs-lookup"><span data-stu-id="e6eff-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>

10. <span data-ttu-id="e6eff-125">W oknie konsoli wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="e6eff-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="e6eff-126">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="e6eff-126">Adams: 120</span></span>

     <span data-ttu-id="e6eff-127">We Feng: 117</span><span class="sxs-lookup"><span data-stu-id="e6eff-127">Feng: 117</span></span>

     <span data-ttu-id="e6eff-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="e6eff-128">Garcia: 115</span></span>

     <span data-ttu-id="e6eff-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="e6eff-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="e6eff-130">Aby filtrować przy użyciu instrukcji switch</span><span class="sxs-lookup"><span data-stu-id="e6eff-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="e6eff-131">Możesz użyć `switch` instrukcję, aby wybrać wśród uprzednio określonym alternatywnych zapytań.</span><span class="sxs-lookup"><span data-stu-id="e6eff-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="e6eff-132">W poniższym przykładzie `studentQuery` używa innego `where` klauzuli zależności od tego, w którym klasy korporacyjnej poziom lub roku, jest określony w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e6eff-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="e6eff-133">Kopiuj następującą metodę i wkleić go do klasy `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="e6eff-134">W `Main` metody, Zastąp wywołanie `QueryByID` przy użyciu następującego wywołania, które wysyła pierwszego elementu z `args` tablicę jako jej argument: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="e6eff-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="e6eff-135">Uruchom projekt z argumentem wiersza polecenia z wartością całkowitą z zakresu od 1 do 4.</span><span class="sxs-lookup"><span data-stu-id="e6eff-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6eff-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6eff-136">See also</span></span>

[<span data-ttu-id="e6eff-137">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e6eff-137">Language Integrated Query (LINQ)</span></span>](index.md)  
[<span data-ttu-id="e6eff-138">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="e6eff-138">where clause</span></span>](../language-reference/keywords/where-clause.md)  