---
title: Order By, klauzula
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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359751"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="523b2-102">Order By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="523b2-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="523b2-103">Określa kolejność sortowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="523b2-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="523b2-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="523b2-105">Części</span><span class="sxs-lookup"><span data-stu-id="523b2-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="523b2-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="523b2-106">Required.</span></span> <span data-ttu-id="523b2-107">Co najmniej jedno pole z wyniku bieżącego zapytania, które określa sposób uporządkowania zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="523b2-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="523b2-108">Nazwy pól muszą być oddzielone przecinkami (,).</span><span class="sxs-lookup"><span data-stu-id="523b2-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="523b2-109">Można zidentyfikować każde pole jako posortowane w kolejności rosnącej lub malejącej za `Ascending` pomocą `Descending` słowa kluczowego or.</span><span class="sxs-lookup"><span data-stu-id="523b2-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="523b2-110">Jeśli nie `Ascending` `Descending` określono słowa kluczowego or, domyślna kolejność sortowania to Ascending.</span><span class="sxs-lookup"><span data-stu-id="523b2-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="523b2-111">Pola porządku sortowania mają pierwszeństwo od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="523b2-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="523b2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="523b2-112">Remarks</span></span>  
 <span data-ttu-id="523b2-113">Można użyć klauzuli, `Order By` Aby posortować wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="523b2-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="523b2-114">`Order By`Klauzula może sortować wynik tylko na podstawie zmiennej zakresu dla bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="523b2-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="523b2-115">Na przykład `Select` klauzula wprowadza nowy zakres w wyrażeniu zapytania z nowymi zmiennymi iteracji dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="523b2-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="523b2-116">Zmienne zakresu zdefiniowane przed `Select` klauzulą w zapytaniu nie są dostępne po `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="523b2-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="523b2-117">W związku z tym, jeśli chcesz zamówić wyniki według pola, które nie jest dostępne w `Select` klauzuli, należy umieścić `Order By` klauzulę przed `Select` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="523b2-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="523b2-118">Przykładem, gdy trzeba to zrobić, jest sortowanie zapytania według pól, które nie są zwracane jako część wyniku.</span><span class="sxs-lookup"><span data-stu-id="523b2-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="523b2-119">Porządek rosnący i malejący dla pola jest określany przez implementację <xref:System.IComparable> interfejsu dla typu danych pola.</span><span class="sxs-lookup"><span data-stu-id="523b2-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="523b2-120">Jeśli typ danych nie implementuje <xref:System.IComparable> interfejsu, porządek sortowania jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="523b2-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="523b2-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="523b2-121">Example</span></span>  
 <span data-ttu-id="523b2-122">Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `book` dla `books` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="523b2-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="523b2-123">`Order By`Klauzula sortuje wyniki zapytania według ceny w kolejności rosnącej (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="523b2-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="523b2-124">Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="523b2-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="523b2-125">`Select`Klauzula służy do wybierania `Title` `Price` właściwości i jako wartości zwracanych przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="523b2-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="523b2-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="523b2-126">Example</span></span>  
 <span data-ttu-id="523b2-127">Poniższe wyrażenie zapytania używa `Order By` klauzuli do sortowania wyników zapytania według ceny w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="523b2-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="523b2-128">Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="523b2-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="523b2-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="523b2-129">Example</span></span>  
 <span data-ttu-id="523b2-130">Poniższe wyrażenie zapytania używa `Select` klauzuli, aby wybrać tytuł książki, cenę, datę publikacji i autora.</span><span class="sxs-lookup"><span data-stu-id="523b2-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="523b2-131">Następnie wypełnia `Title` `Price` pola,, `PublishDate` , i `Author` zmiennej zakresu dla nowego zakresu.</span><span class="sxs-lookup"><span data-stu-id="523b2-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="523b2-132">`Order By`Klauzula porządkuje nową zmienną zakresu według nazwy autora, tytułu książki, a następnie ceny.</span><span class="sxs-lookup"><span data-stu-id="523b2-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="523b2-133">Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).</span><span class="sxs-lookup"><span data-stu-id="523b2-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="523b2-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="523b2-134">See also</span></span>

- [<span data-ttu-id="523b2-135">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="523b2-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="523b2-136">Zapytania</span><span class="sxs-lookup"><span data-stu-id="523b2-136">Queries</span></span>](index.md)
- [<span data-ttu-id="523b2-137">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="523b2-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="523b2-138">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="523b2-138">From Clause</span></span>](from-clause.md)
