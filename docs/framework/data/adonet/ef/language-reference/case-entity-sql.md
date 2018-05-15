---
title: W przypadku (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: ee878409e7698300b7bebbdac760422013f3b7de
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="case-entity-sql"></a><span data-ttu-id="cc8e1-102">W przypadku (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cc8e1-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="cc8e1-103">Ocenia zestaw `Boolean` wyrażeń w celu ustalenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc8e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc8e1-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc8e1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cc8e1-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="cc8e1-106">Jest to symbol zastępczy, która wskazuje, że wiele podczas `Boolean_expression` następnie `result_expression` klauzule można użyć.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="cc8e1-107">NASTĘPNIE `result_expression`</span><span class="sxs-lookup"><span data-stu-id="cc8e1-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="cc8e1-108">Wyrażenie zwracane, gdy `Boolean_expression` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="cc8e1-109">`result expression` Jest dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="cc8e1-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="cc8e1-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="cc8e1-111">Wyrażenie zwracane, jeśli żadna operacja porównania nie daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="cc8e1-112">Jeśli ten argument zostanie pominięty i żadna operacja porównania nie daje w wyniku `true`, przypadku zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="cc8e1-113">`else_result_expression` Jest dowolne prawidłowe wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="cc8e1-114">Typy danych `else_result_expression` oraz wszelkie `result_expression` muszą być takie same lub musi być niejawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="cc8e1-115">KIEDY `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="cc8e1-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="cc8e1-116">Jest `Boolean` wyrażenia obliczonego w przypadku użycia przeszukane formatu wielkość.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="cc8e1-117">`Boolean_expression` nadaje się żadnym `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc8e1-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc8e1-118">Return Value</span></span>  
 <span data-ttu-id="cc8e1-119">Zwraca typ najwyższy priorytet z zestawu typów w `result_expression` oraz opcjonalny `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc8e1-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc8e1-120">Remarks</span></span>  
 <span data-ttu-id="cc8e1-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Podobny wyrażenie case [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="cc8e1-122">Wyrażenie case umożliwia upewnij serii testów warunkowego, aby określić wyrażenie, które umożliwia uzyskanie odpowiedniego wynik.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="cc8e1-123">Ten formularz wyrażenia case dotyczy serii jednego lub więcej `Boolean` wyrażenia, aby określić poprawne wyrażenie wynikowe.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="cc8e1-124">Funkcja CASE ocenia `Boolean_expression` dla każdej klauzuli WHEN w kolejności określonej i zwraca `result_expression` pierwszego `Boolean_expression` który daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="cc8e1-125">Pozostałe wyrażenia nie są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="cc8e1-126">Jeśli nie `Boolean_expression` daje w wyniku `true`, aparatu bazy danych zwraca `else_result_expression` Jeśli określono klauzulę ELSE, lub wartość null, jeśli nie określono żadnych klauzuli ELSE.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="cc8e1-127">CASE — instrukcja nie może zwrócić zestawu wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc8e1-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc8e1-128">Example</span></span>  
 <span data-ttu-id="cc8e1-129">Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażeń w celu ustalenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="cc8e1-130">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cc8e1-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cc8e1-131">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cc8e1-131">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cc8e1-132">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cc8e1-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="cc8e1-133">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cc8e1-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="cc8e1-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc8e1-134">See Also</span></span>  
 [<span data-ttu-id="cc8e1-135">THEN</span><span class="sxs-lookup"><span data-stu-id="cc8e1-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [<span data-ttu-id="cc8e1-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="cc8e1-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="cc8e1-137">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cc8e1-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
