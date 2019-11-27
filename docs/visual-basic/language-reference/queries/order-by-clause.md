---
title: Order By — Klauzula
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
ms.openlocfilehash: a7104e3dd82ff2dde2911861ce98a7367faf3b25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350418"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="19af7-102">Order By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19af7-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="19af7-103">Określa kolejność sortowania wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="19af7-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19af7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19af7-104">Syntax</span></span>  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="19af7-105">Części</span><span class="sxs-lookup"><span data-stu-id="19af7-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="19af7-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="19af7-106">Required.</span></span> <span data-ttu-id="19af7-107">Co najmniej jedno pole z wyniku bieżącego zapytania, które określa sposób uporządkowania zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="19af7-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="19af7-108">Nazwy pól muszą być oddzielone przecinkami (,).</span><span class="sxs-lookup"><span data-stu-id="19af7-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="19af7-109">Każde pole można zidentyfikować jako posortowane w kolejności rosnącej lub malejącej przy użyciu słów kluczowych `Ascending` lub `Descending`.</span><span class="sxs-lookup"><span data-stu-id="19af7-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="19af7-110">Jeśli nie określono `Ascending` ani `Descending` słowa kluczowego, domyślną kolejnością sortowania jest rosnąco.</span><span class="sxs-lookup"><span data-stu-id="19af7-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="19af7-111">Pola porządku sortowania mają pierwszeństwo od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="19af7-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19af7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19af7-112">Remarks</span></span>  
 <span data-ttu-id="19af7-113">Można użyć klauzuli `Order By`, aby posortować wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="19af7-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="19af7-114">Klauzula `Order By` może sortować wynik tylko na podstawie zmiennej zakresu dla bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="19af7-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="19af7-115">Na przykład klauzula `Select` wprowadza nowy zakres w wyrażeniu zapytania z nowymi zmiennymi iteracji dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="19af7-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="19af7-116">Zmienne zakresu zdefiniowane przed klauzulą `Select` w zapytaniu nie są dostępne po klauzuli `Select`.</span><span class="sxs-lookup"><span data-stu-id="19af7-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="19af7-117">W związku z tym, jeśli chcesz zamówić wyniki według pola, które nie jest dostępne w klauzuli `Select`, należy umieścić klauzulę `Order By` przed klauzulą `Select`.</span><span class="sxs-lookup"><span data-stu-id="19af7-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="19af7-118">Przykładem, gdy trzeba to zrobić, jest sortowanie zapytania według pól, które nie są zwracane jako część wyniku.</span><span class="sxs-lookup"><span data-stu-id="19af7-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="19af7-119">Porządek rosnący i malejący dla pola jest określany przez implementację interfejsu <xref:System.IComparable> dla typu danych pola.</span><span class="sxs-lookup"><span data-stu-id="19af7-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="19af7-120">Jeśli typ danych nie implementuje interfejsu <xref:System.IComparable>, porządek sortowania jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="19af7-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19af7-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="19af7-121">Example</span></span>  
 <span data-ttu-id="19af7-122">Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `book` dla kolekcji `books`.</span><span class="sxs-lookup"><span data-stu-id="19af7-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="19af7-123">Klauzula `Order By` sortuje wyniki zapytania według ceny w kolejności rosnącej (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="19af7-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="19af7-124">Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="19af7-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="19af7-125">Klauzula `Select` wybiera właściwości `Title` i `Price` jako wartości zwracane przez zapytanie.</span><span class="sxs-lookup"><span data-stu-id="19af7-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="19af7-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="19af7-126">Example</span></span>  
 <span data-ttu-id="19af7-127">Następujące wyrażenie zapytania używa klauzuli `Order By`, aby posortować wyniki zapytania według ceny w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="19af7-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="19af7-128">Książki o tej samej cenie są sortowane według tytułu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="19af7-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="19af7-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="19af7-129">Example</span></span>  
 <span data-ttu-id="19af7-130">Poniższe wyrażenie zapytania używa klauzuli `Select`, aby wybrać tytuł książki, cenę, datę publikacji i autora.</span><span class="sxs-lookup"><span data-stu-id="19af7-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="19af7-131">Następnie wypełnia pola `Title`, `Price`, `PublishDate`i `Author` zmiennej zakresu dla nowego zakresu.</span><span class="sxs-lookup"><span data-stu-id="19af7-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="19af7-132">Klauzula `Order By` porządkuje nową zmienną zakresu według nazwy autora, tytułu książki, a następnie ceny.</span><span class="sxs-lookup"><span data-stu-id="19af7-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="19af7-133">Każda kolumna jest sortowana w kolejności domyślnej (rosnąco).</span><span class="sxs-lookup"><span data-stu-id="19af7-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="19af7-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19af7-134">See also</span></span>

- [<span data-ttu-id="19af7-135">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19af7-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="19af7-136">Zapytania</span><span class="sxs-lookup"><span data-stu-id="19af7-136">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="19af7-137">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="19af7-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="19af7-138">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="19af7-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
