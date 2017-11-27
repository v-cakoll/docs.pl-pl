---
title: "Order By — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ee21942b966668a67b14aba72b8f9fc5ee903c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="c32d8-102">Order By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c32d8-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="c32d8-103">Określa porządek sortowania dla wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="c32d8-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c32d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c32d8-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c32d8-105">Części</span><span class="sxs-lookup"><span data-stu-id="c32d8-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="c32d8-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c32d8-106">Required.</span></span> <span data-ttu-id="c32d8-107">Co najmniej jednego pola z bieżącego wyniku zapytania określających kolejność zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="c32d8-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="c32d8-108">Nazwy pól muszą być oddzielone przecinkami (,).</span><span class="sxs-lookup"><span data-stu-id="c32d8-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="c32d8-109">Każde pole można określić jako sortowane w kolejności rosnącej lub malejącej przy użyciu `Ascending` lub `Descending` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="c32d8-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="c32d8-110">Jeśli nie `Ascending` lub `Descending` zostanie określone słowo kluczowe, domyślna kolejność sortowania jest rosnąca.</span><span class="sxs-lookup"><span data-stu-id="c32d8-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="c32d8-111">Pola kolejność sortowania podano pierwszeństwo od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="c32d8-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c32d8-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c32d8-112">Remarks</span></span>  
 <span data-ttu-id="c32d8-113">Można użyć `Order By` klauzuli sortowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="c32d8-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="c32d8-114">`Order By` Klauzuli można sortować tylko wynik oparte na zmienną zakresu dla bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c32d8-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="c32d8-115">Na przykład `Select` klauzuli wprowadzono nowy zakres w wyrażeniu zapytania z nowe zmienne iteracji dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c32d8-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="c32d8-116">Zakres zmienne zdefiniowane przed `Select` podklauzul nie są dostępne po `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c32d8-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="c32d8-117">W związku z tym aby uporządkować wyniki według pola, który nie jest dostępny w `Select` klauzuli, możesz umieścić `Order By` klauzuli przed `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c32d8-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="c32d8-118">Jeden przykład kiedy należy to zrobić to można sortować według pól, które nie są zwracane w ramach wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="c32d8-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="c32d8-119">Rosnąca i malejącej dla pola zależy od implementacji <xref:System.IComparable> interfejs dla typu danych pola.</span><span class="sxs-lookup"><span data-stu-id="c32d8-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="c32d8-120">Jeśli typ danych nie implementuje <xref:System.IComparable> interfejsu, kolejność sortowania jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="c32d8-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c32d8-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c32d8-121">Example</span></span>  
 <span data-ttu-id="c32d8-122">Następujące zapytanie używa wyrażenia `From` klauzuli, aby zadeklarować zmienną zakresu `book` dla `books` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c32d8-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="c32d8-123">`Order By` Klauzuli sortowania wyników zapytania cen Rosnąco (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c32d8-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="c32d8-124">Książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c32d8-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="c32d8-125">`Select` Wybiera klauzuli `Title` i `Price` właściwości jako wartości zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="c32d8-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c32d8-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c32d8-126">Example</span></span>  
 <span data-ttu-id="c32d8-127">Następujące zapytanie używa wyrażenia `Order By` klauzuli sortowania wyników zapytania przez cen w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="c32d8-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="c32d8-128">Książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c32d8-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c32d8-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c32d8-129">Example</span></span>  
 <span data-ttu-id="c32d8-130">Następujące zapytanie używa wyrażenia `Select` klauzuli wybierz tytułu ceny, Opublikuj datę i autora.</span><span class="sxs-lookup"><span data-stu-id="c32d8-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="c32d8-131">Następnie wypełnia `Title`, `Price`, `PublishDate`, i `Author` pola zmienna zakresu dla nowego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c32d8-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="c32d8-132">`Order By` Klauzuli porządkuje zmienną zakresu imię i nazwisko autora, tytuł książki i cenę.</span><span class="sxs-lookup"><span data-stu-id="c32d8-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="c32d8-133">Każda kolumna jest sortowane w kolejności domyślnej (rosnąco).</span><span class="sxs-lookup"><span data-stu-id="c32d8-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c32d8-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c32d8-134">See Also</span></span>  
 [<span data-ttu-id="c32d8-135">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c32d8-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="c32d8-136">Zapytania</span><span class="sxs-lookup"><span data-stu-id="c32d8-136">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="c32d8-137">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="c32d8-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="c32d8-138">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="c32d8-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
