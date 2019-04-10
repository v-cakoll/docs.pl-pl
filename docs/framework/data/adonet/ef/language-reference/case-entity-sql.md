---
title: W przypadku (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: e44f48d040fc77bf702759be0c53a618cd84f9fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334890"
---
# <a name="case-entity-sql"></a><span data-ttu-id="f9bd3-102">W przypadku (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f9bd3-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="f9bd3-103">Obliczenie zestawu `Boolean` wyrażenia do obliczenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9bd3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9bd3-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9bd3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f9bd3-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="f9bd3-106">Jest symbolem zastępczym, która wskazuje, że wiele podczas `Boolean_expression` następnie `result_expression` klauzule można użyć.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="f9bd3-107">THEN</span><span class="sxs-lookup"><span data-stu-id="f9bd3-107">THEN</span></span> `result_expression`  
 <span data-ttu-id="f9bd3-108">Wyrażenie zwracane, gdy `Boolean_expression` daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> `result expression` <span data-ttu-id="f9bd3-109">Jest dowolnym prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-109">is any valid expression.</span></span>  
  
 <span data-ttu-id="f9bd3-110">ELSE</span><span class="sxs-lookup"><span data-stu-id="f9bd3-110">ELSE</span></span> `else_result_expression`  
 <span data-ttu-id="f9bd3-111">Wyrażenie zwracane, jeśli żadna operacja porównania nie daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="f9bd3-112">Jeśli ten argument zostanie pominięty, a żadna operacja porównania, które daje w wyniku `true`, przypadek zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> `else_result_expression` <span data-ttu-id="f9bd3-113">Jest dowolnym prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-113">is any valid expression.</span></span> <span data-ttu-id="f9bd3-114">Typy danych `else_result_expression` oraz wszelką `result_expression` musi być taka sama lub musi być niejawną konwersję.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="f9bd3-115">KIEDY</span><span class="sxs-lookup"><span data-stu-id="f9bd3-115">WHEN</span></span> `Boolean_expression`  
 <span data-ttu-id="f9bd3-116">Jest `Boolean` wyrażenia obliczonego stosowania wyszukiwanych format wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> `Boolean_expression` <span data-ttu-id="f9bd3-117">jest dowolne, prawidłowe `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-117">is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9bd3-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f9bd3-118">Return Value</span></span>  
 <span data-ttu-id="f9bd3-119">Zwraca typ najwyższy priorytet z zestawu typów w `result_expression` i opcjonalną `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9bd3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9bd3-120">Remarks</span></span>  
 <span data-ttu-id="f9bd3-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Przypomina wyrażenia case [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] zamierzone, Zapisz wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="f9bd3-122">Wyrażenie case umożliwia wprowadzając szereg testów warunkowych, aby określić wyrażenie, które umożliwia uzyskanie odpowiednich wyników.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="f9bd3-123">Ta forma wyrażenia case dotyczy serii co najmniej jednego `Boolean` wyrażenia, aby określić poprawne wyrażenie wynikowe.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="f9bd3-124">Funkcja CASE ocenia `Boolean_expression` dla każdej klauzuli WHEN w kolejności określonej, a następnie zwraca `result_expression` pierwszego `Boolean_expression` która daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="f9bd3-125">Pozostałe wyrażenia nie są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="f9bd3-126">Jeśli nie `Boolean_expression` daje w wyniku `true`, aparat bazy danych zwraca `else_result_expression` Jeśli określono klauzulę ELSE, lub wartość null, jeśli określono żadnej klauzuli ELSE.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="f9bd3-127">CASE — instrukcja nie może zwrócić zestawu wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9bd3-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9bd3-128">Example</span></span>  
 <span data-ttu-id="f9bd3-129">Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażenia w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="f9bd3-130">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f9bd3-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f9bd3-131">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f9bd3-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f9bd3-132">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f9bd3-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f9bd3-133">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="f9bd3-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="f9bd3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9bd3-134">See also</span></span>

- [<span data-ttu-id="f9bd3-135">THEN</span><span class="sxs-lookup"><span data-stu-id="f9bd3-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [<span data-ttu-id="f9bd3-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="f9bd3-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="f9bd3-137">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f9bd3-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
