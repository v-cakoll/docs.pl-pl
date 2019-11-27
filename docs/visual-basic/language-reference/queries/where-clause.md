---
title: Where — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 60b7ebe96ce0c4580c36675b2e4aa5f9888732c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349628"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="71638-102">Where — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71638-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="71638-103">Określa warunek filtrowania dla zapytania.</span><span class="sxs-lookup"><span data-stu-id="71638-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71638-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71638-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="71638-105">Części</span><span class="sxs-lookup"><span data-stu-id="71638-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="71638-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="71638-106">Required.</span></span> <span data-ttu-id="71638-107">Wyrażenie określające, czy wartości bieżącego elementu w kolekcji są uwzględniane w kolekcji wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="71638-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="71638-108">Wyrażenie musi mieć wartość `Boolean` lub być równoważną wartością `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="71638-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="71638-109">Jeśli warunek szacuje się `True`, element zostanie uwzględniony w wyniku zapytania; w przeciwnym razie element jest wykluczony z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="71638-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71638-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71638-110">Remarks</span></span>  
 <span data-ttu-id="71638-111">Klauzula `Where` umożliwia filtrowanie danych zapytania przez wybranie tylko elementów spełniających określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="71638-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="71638-112">Elementy, których wartości powodują, że `Where` klauzulę do oszacowania `True` są uwzględniane w wyniku zapytania; inne elementy są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="71638-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="71638-113">Wyrażenie, które jest używane w klauzuli `Where` musi oszacować do `Boolean` lub równoważnej `Boolean`, takiej jak liczba całkowita, która daje w wyniku `False`, gdy wartość wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="71638-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="71638-114">Można połączyć wiele wyrażeń w klauzuli `Where` za pomocą operatorów logicznych, takich jak `And`, `Or`, `AndAlso`, `OrElse`, `Is`i `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="71638-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="71638-115">Domyślnie wyrażenia zapytania nie są oceniane do momentu uzyskania dostępu do nich, na przykład gdy są one powiązane z danymi lub powtarzane przez pętlę `For`.</span><span class="sxs-lookup"><span data-stu-id="71638-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="71638-116">W efekcie klauzula `Where` nie jest oceniana do momentu uzyskania dostępu do zapytania.</span><span class="sxs-lookup"><span data-stu-id="71638-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="71638-117">Jeśli masz wartości spoza zapytania, które są używane w klauzuli `Where`, upewnij się, że odpowiednia wartość jest używana w klauzuli `Where` w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="71638-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="71638-118">Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="71638-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="71638-119">Możesz wywoływać funkcje w klauzuli `Where`, aby wykonać obliczenia lub operację na wartości z bieżącego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="71638-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="71638-120">Wywołanie funkcji w klauzuli `Where` może spowodować, że zapytanie ma być wykonywane natychmiast po jego zdefiniowaniu, a nie w momencie uzyskiwania do niego dostępu.</span><span class="sxs-lookup"><span data-stu-id="71638-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="71638-121">Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="71638-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71638-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="71638-122">Example</span></span>  
 <span data-ttu-id="71638-123">Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `cust` dla każdego obiektu `Customer` w kolekcji `customers`.</span><span class="sxs-lookup"><span data-stu-id="71638-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="71638-124">Klauzula `Where` używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu.</span><span class="sxs-lookup"><span data-stu-id="71638-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="71638-125">Pętla `For Each` wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="71638-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="71638-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="71638-126">Example</span></span>  
 <span data-ttu-id="71638-127">Poniższy przykład używa `And` i `Or` operatory logiczne w klauzuli `Where`.</span><span class="sxs-lookup"><span data-stu-id="71638-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="71638-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71638-128">See also</span></span>

- [<span data-ttu-id="71638-129">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71638-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="71638-130">Zapytania</span><span class="sxs-lookup"><span data-stu-id="71638-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="71638-131">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="71638-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="71638-132">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="71638-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="71638-133">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="71638-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
