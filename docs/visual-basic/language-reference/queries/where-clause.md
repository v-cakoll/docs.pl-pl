---
title: Where — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 0b61a52a366fb37a0834c9223bc8b7f099354d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="f3fc1-102">Where — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3fc1-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="f3fc1-103">Określa warunek filtrowania dla zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fc1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3fc1-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="f3fc1-105">Części</span><span class="sxs-lookup"><span data-stu-id="f3fc1-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="f3fc1-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-106">Required.</span></span> <span data-ttu-id="f3fc1-107">Wyrażenie, które określa, czy wartości dla bieżącego elementu w kolekcji są dołączane do kolekcji danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="f3fc1-108">Wyrażenia musi być `Boolean` wartość lub odpowiednikiem `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="f3fc1-109">Jeśli wynikiem warunku jest `True`, element jest uwzględnione w wynikach zapytania; w przeciwnym razie, element są wykluczane w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3fc1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3fc1-110">Remarks</span></span>  
 <span data-ttu-id="f3fc1-111">`Where` Klauzuli umożliwia filtrowanie danych zapytania, wybierając tylko te elementy, które spełniają określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="f3fc1-112">Elementy, których wartości powodują `Where` klauzuli mogła zwrócić `True` znajdują się w wynikach zapytania; inne elementy są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="f3fc1-113">Wyrażenie, które jest używane w `Where` musi mieć klauzulę `Boolean` lub odpowiednikiem `Boolean`, takie jak liczba całkowita, która daje w wyniku `False` po jego wartość wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="f3fc1-114">Można połączyć wiele wyrażeń w `Where` klauzuli przy użyciu operatorów logicznych, takich jak `And`, `Or`, `AndAlso`, `OrElse`, `Is`, i `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="f3fc1-115">Domyślnie wyrażenia zapytania nie są obliczane aż do uzyskiwania do nich — na przykład, gdy są one powiązane z danymi lub powtórzyć za pośrednictwem w `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="f3fc1-116">W związku z tym `Where` klauzula nie jest oceniany, aż do uzyskiwania dostępu do zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="f3fc1-117">Jeśli masz wartości zewnętrznych do zapytania, które są używane w `Where` klauzuli, upewnij się, że odpowiednią wartość jest używana w `Where` klauzuli w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="f3fc1-118">Aby uzyskać więcej informacji na temat wykonywania zapytania, zobacz [Your pierwszego zapytania LINQ zapisu](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="f3fc1-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="f3fc1-119">Można wywołać funkcji w ramach `Where` klauzuli, aby wykonać obliczenie lub operacja na wartości z bieżącego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="f3fc1-120">Wywoływanie funkcji w `Where` klauzuli może spowodować wykonanie zapytania w celu wykonania natychmiast, gdy jest on zdefiniowany zamiast, gdy jest on dostępny.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="f3fc1-121">Aby uzyskać więcej informacji na temat wykonywania zapytania, zobacz [Your pierwszego zapytania LINQ zapisu](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="f3fc1-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3fc1-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3fc1-122">Example</span></span>  
 <span data-ttu-id="f3fc1-123">Następujące zapytanie używa wyrażenia `From` klauzuli, aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="f3fc1-124">`Where` Klauzuli używa zmiennej zakresu, aby ograniczyć dane wyjściowe do klientów z określonego regionu.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="f3fc1-125">`For Each` Pętli Wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f3fc1-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3fc1-126">Example</span></span>  
 <span data-ttu-id="f3fc1-127">W poniższym przykładzie użyto `And` i `Or` operatory logiczne w `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f3fc1-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f3fc1-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3fc1-128">See Also</span></span>  
 [<span data-ttu-id="f3fc1-129">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3fc1-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="f3fc1-130">Zapytania</span><span class="sxs-lookup"><span data-stu-id="f3fc1-130">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="f3fc1-131">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="f3fc1-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="f3fc1-132">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="f3fc1-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="f3fc1-133">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f3fc1-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
