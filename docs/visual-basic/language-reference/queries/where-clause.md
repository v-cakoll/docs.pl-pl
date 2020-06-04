---
title: Where, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359544"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="acf6c-102">Where — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acf6c-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="acf6c-103">Określa warunek filtrowania dla zapytania.</span><span class="sxs-lookup"><span data-stu-id="acf6c-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="acf6c-104">Syntax</span></span>  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="acf6c-105">Części</span><span class="sxs-lookup"><span data-stu-id="acf6c-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="acf6c-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="acf6c-106">Required.</span></span> <span data-ttu-id="acf6c-107">Wyrażenie określające, czy wartości bieżącego elementu w kolekcji są uwzględniane w kolekcji wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="acf6c-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="acf6c-108">Wyrażenie musi być szacowane do `Boolean` wartości lub równoważnej `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="acf6c-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="acf6c-109">Jeśli warunek ma wartość `True` , element zostanie uwzględniony w wyniku zapytania; w przeciwnym razie element jest wykluczony z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="acf6c-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acf6c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acf6c-110">Remarks</span></span>  
 <span data-ttu-id="acf6c-111">`Where`Klauzula umożliwia filtrowanie danych zapytania przez wybranie tylko elementów spełniających określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="acf6c-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="acf6c-112">Elementy, których wartości powodują, że `Where` klauzula do obliczenia, `True` są uwzględniane w wyniku zapytania; inne elementy są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="acf6c-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="acf6c-113">Wyrażenie, które jest używane w `Where` klauzuli musi być szacowane do `Boolean` lub równoważne `Boolean` , takie jak liczba całkowita, która daje w `False` wyniku wartość zero.</span><span class="sxs-lookup"><span data-stu-id="acf6c-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="acf6c-114">Można połączyć wiele wyrażeń w `Where` klauzuli przy użyciu operatorów logicznych, takich jak `And` , `Or` ,, `AndAlso` , `OrElse` `Is` i `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="acf6c-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="acf6c-115">Domyślnie wyrażenia zapytania nie są oceniane do momentu uzyskania dostępu do nich, na przykład gdy są one powiązane z danymi lub powtarzane przez `For` pętlę.</span><span class="sxs-lookup"><span data-stu-id="acf6c-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="acf6c-116">W związku z tym `Where` klauzula nie jest oceniana do momentu uzyskania dostępu do zapytania.</span><span class="sxs-lookup"><span data-stu-id="acf6c-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="acf6c-117">Jeśli masz wartości spoza zapytania, które są używane w `Where` klauzuli, upewnij się, że odpowiednia wartość jest używana w `Where` klauzuli w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="acf6c-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="acf6c-118">Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="acf6c-118">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="acf6c-119">Możesz wywoływać funkcje w `Where` klauzuli, aby wykonać obliczenia lub operację na wartości z bieżącego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="acf6c-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="acf6c-120">Wywołanie funkcji w `Where` klauzuli może spowodować, że zapytanie ma być wykonywane natychmiast po jego zdefiniowaniu, a nie w momencie uzyskiwania do niego dostępu.</span><span class="sxs-lookup"><span data-stu-id="acf6c-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="acf6c-121">Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="acf6c-121">For more information about query execution, see [Writing Your First LINQ Query](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf6c-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="acf6c-122">Example</span></span>  
 <span data-ttu-id="acf6c-123">Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="acf6c-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="acf6c-124">`Where`Klauzula używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu.</span><span class="sxs-lookup"><span data-stu-id="acf6c-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="acf6c-125">`For Each`Pętla wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="acf6c-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="acf6c-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="acf6c-126">Example</span></span>  
 <span data-ttu-id="acf6c-127">W poniższym przykładzie są `And` stosowane `Or` Operatory logiczne w `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="acf6c-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="acf6c-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="acf6c-128">See also</span></span>

- [<span data-ttu-id="acf6c-129">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acf6c-129">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="acf6c-130">Zapytania</span><span class="sxs-lookup"><span data-stu-id="acf6c-130">Queries</span></span>](index.md)
- [<span data-ttu-id="acf6c-131">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="acf6c-131">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="acf6c-132">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="acf6c-132">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="acf6c-133">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="acf6c-133">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
