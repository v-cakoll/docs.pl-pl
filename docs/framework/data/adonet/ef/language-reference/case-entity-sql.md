---
title: PRZYPADEK (ENTITY SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150470"
---
# <a name="case-entity-sql"></a><span data-ttu-id="b64f0-102">PRZYPADEK (ENTITY SQL)</span><span class="sxs-lookup"><span data-stu-id="b64f0-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="b64f0-103">Ocenia zestaw `Boolean` wyrażeń w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="b64f0-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b64f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b64f0-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="b64f0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b64f0-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="b64f0-106">Jest symbolem zastępczym, który `Boolean_expression` wskazuje, że można użyć wielu klauzul WHEN THEN. `result_expression`</span><span class="sxs-lookup"><span data-stu-id="b64f0-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="b64f0-107">Następnie`result_expression`</span><span class="sxs-lookup"><span data-stu-id="b64f0-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="b64f0-108">Czy wyrażenie jest `Boolean_expression` zwracane `true`po dodaniu .</span><span class="sxs-lookup"><span data-stu-id="b64f0-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="b64f0-109">`result expression`jest dowolnym prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="b64f0-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="b64f0-110">Innego`else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="b64f0-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="b64f0-111">Czy wyrażenie jest zwracane, jeśli `true`żadna operacja porównania nie ma oceny .</span><span class="sxs-lookup"><span data-stu-id="b64f0-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="b64f0-112">Jeśli ten argument zostanie pominięty i `true`żadna operacja porównania nie ma do tej wartości , case zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="b64f0-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="b64f0-113">`else_result_expression`jest dowolnym prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="b64f0-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="b64f0-114">Typy danych `else_result_expression` i `result_expression` wszelkie muszą być takie same lub musi być niejawna konwersja.</span><span class="sxs-lookup"><span data-stu-id="b64f0-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="b64f0-115">Kiedy`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="b64f0-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="b64f0-116">Czy `Boolean` wyrażenie jest oceniane podczas wyszukiwania formatu CASE jest używany.</span><span class="sxs-lookup"><span data-stu-id="b64f0-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="b64f0-117">`Boolean_expression`jest dowolnym `Boolean` prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="b64f0-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b64f0-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b64f0-118">Return Value</span></span>  
 <span data-ttu-id="b64f0-119">Zwraca najwyższy typ pierwszeństwa z zestawu `result_expression` typów w `else_result_expression`i opcjonalnym .</span><span class="sxs-lookup"><span data-stu-id="b64f0-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b64f0-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b64f0-120">Remarks</span></span>  
 <span data-ttu-id="b64f0-121">Wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sprawy przypomina wyrażenie przypadku Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b64f0-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="b64f0-122">Wyrażenie przypadku służy do wykonania serii testów warunkowych w celu określenia, które wyrażenie przyniesie odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="b64f0-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="b64f0-123">Ta forma wyrażenia case ma zastosowanie do serii `Boolean` jednego lub więcej wyrażeń w celu określenia poprawnego wyrażenia wynikowego.</span><span class="sxs-lookup"><span data-stu-id="b64f0-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="b64f0-124">Funkcja CASE ocenia `Boolean_expression` dla każdej klauzuli WHEN w `result_expression` określonej `Boolean_expression` kolejności i `true`zwraca pierwszą, która ocenia .</span><span class="sxs-lookup"><span data-stu-id="b64f0-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="b64f0-125">Pozostałe wyrażenia nie są oceniane.</span><span class="sxs-lookup"><span data-stu-id="b64f0-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="b64f0-126">Jeśli `Boolean_expression` nie ma `true`żadnych obliczeń, `else_result_expression` Aparat baz danych zwraca, jeśli else klauzuli jest określony lub wartość null, jeśli nie else klauzuli jest określony.</span><span class="sxs-lookup"><span data-stu-id="b64f0-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="b64f0-127">Instrukcja CASE nie może zwrócić zestawu wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="b64f0-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b64f0-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="b64f0-128">Example</span></span>  
 <span data-ttu-id="b64f0-129">Następująca kwerenda SQL jednostki używa wyrażenia `Boolean` CASE do oceny zestawu wyrażeń w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="b64f0-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="b64f0-130">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b64f0-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b64f0-131">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b64f0-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b64f0-132">Postępuj zgodnie z procedurą [w : Jak wykonać kwerendę, która zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b64f0-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="b64f0-133">Przekaż następującą kwerendę jako `ExecutePrimitiveTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="b64f0-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="b64f0-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b64f0-134">See also</span></span>

- [<span data-ttu-id="b64f0-135">Następnie</span><span class="sxs-lookup"><span data-stu-id="b64f0-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="b64f0-136">Wybierz</span><span class="sxs-lookup"><span data-stu-id="b64f0-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="b64f0-137">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b64f0-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
