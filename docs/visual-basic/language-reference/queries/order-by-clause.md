---
title: Order By — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 1d9055796687f828cc173a78feb9918cbf70bbd8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976372"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="cddc0-102">Order By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cddc0-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="cddc0-103">Określa porządek sortowania dla wyniku kwerendy.</span><span class="sxs-lookup"><span data-stu-id="cddc0-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cddc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cddc0-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="cddc0-105">Części</span><span class="sxs-lookup"><span data-stu-id="cddc0-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="cddc0-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cddc0-106">Required.</span></span> <span data-ttu-id="cddc0-107">Co najmniej jednego pola z bieżącego wyniku zapytania określających sposób sortowania wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="cddc0-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="cddc0-108">Nazwy pól muszą być oddzielone przecinkami (,).</span><span class="sxs-lookup"><span data-stu-id="cddc0-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="cddc0-109">Można zidentyfikować każde pole, jak posortowane w kolejności rosnącej lub malejącej, używając `Ascending` lub `Descending` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="cddc0-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="cddc0-110">Jeśli nie `Ascending` lub `Descending` — słowo kluczowe jest określony, domyślna kolejność sortowania jest rosnąca.</span><span class="sxs-lookup"><span data-stu-id="cddc0-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="cddc0-111">Pola kolejności sortowania są podane pierwszeństwa od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="cddc0-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cddc0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cddc0-112">Remarks</span></span>  
 <span data-ttu-id="cddc0-113">Możesz użyć `Order By` klauzuli sortowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="cddc0-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="cddc0-114">`Order By` Klauzuli można sortować tylko wynik, w oparciu o zmiennej zakresu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="cddc0-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="cddc0-115">Na przykład `Select` klauzuli wprowadza nowy zakres w wyrażeniu zapytania przy użyciu nowych zmiennych iteracji dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="cddc0-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="cddc0-116">Zakres zmiennych zdefiniowanych przed `Select` podklauzul nie są dostępne po `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cddc0-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="cddc0-117">W związku z tym jeśli chcesz uporządkować wyniki według pola, która nie jest dostępna w `Select` klauzuli, należy umieścić `Order By` klauzuli przed `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cddc0-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="cddc0-118">Jeden przykład przypadku w tym celu jest posortować według pól, które nie są zwracane jako część wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="cddc0-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="cddc0-119">Kolejności rosnącej i malejącej dla pola jest określane przez implementację <xref:System.IComparable> interfejsu dla typu danych pola.</span><span class="sxs-lookup"><span data-stu-id="cddc0-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="cddc0-120">Jeśli typ danych nie zawiera implementacji <xref:System.IComparable> interfejsu, kolejność sortowania jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="cddc0-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cddc0-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="cddc0-121">Example</span></span>  
 <span data-ttu-id="cddc0-122">Następujące zapytanie używa wyrażenia `From` klauzulę, aby zadeklarować zmienną zakresu `book` dla `books` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cddc0-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="cddc0-123">`Order By` Klauzuli sortowania wyników zapytania cena Rosnąco (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cddc0-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="cddc0-124">Sklepu iBook książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="cddc0-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="cddc0-125">`Select` Wybiera klauzuli `Title` i `Price` właściwości jako wartości zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="cddc0-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="cddc0-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="cddc0-126">Example</span></span>  
 <span data-ttu-id="cddc0-127">Następujące zapytanie używa wyrażenia `Order By` klauzuli sortowania wyników zapytania według ceny w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="cddc0-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="cddc0-128">Sklepu iBook książek z tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="cddc0-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="cddc0-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="cddc0-129">Example</span></span>  
 <span data-ttu-id="cddc0-130">Następujące zapytanie używa wyrażenia `Select` klauzuli wybierz tytuł książki, cen, Data opublikowania i autora.</span><span class="sxs-lookup"><span data-stu-id="cddc0-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="cddc0-131">Następnie wypełnia `Title`, `Price`, `PublishDate`, i `Author` pola zmienna zakresu dla nowego zakresu.</span><span class="sxs-lookup"><span data-stu-id="cddc0-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="cddc0-132">`Order By` Klauzuli porządkuje nowej zmiennej zakresu nazwisko autora, tytuł książki i ceny.</span><span class="sxs-lookup"><span data-stu-id="cddc0-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="cddc0-133">Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).</span><span class="sxs-lookup"><span data-stu-id="cddc0-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="cddc0-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cddc0-134">See also</span></span>
- [<span data-ttu-id="cddc0-135">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cddc0-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="cddc0-136">Zapytania</span><span class="sxs-lookup"><span data-stu-id="cddc0-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="cddc0-137">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="cddc0-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="cddc0-138">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="cddc0-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
