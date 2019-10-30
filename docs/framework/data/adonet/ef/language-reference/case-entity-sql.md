---
title: PRZYPADEK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 7c1e02d44c674bf262f92df1c43bec6e9f2143c5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039930"
---
# <a name="case-entity-sql"></a><span data-ttu-id="7df44-102">PRZYPADEK (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7df44-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="7df44-103">Oblicza zestaw wyrażeń `Boolean`, aby określić wynik.</span><span class="sxs-lookup"><span data-stu-id="7df44-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7df44-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="7df44-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7df44-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="7df44-106">Jest symbolem zastępczym, który wskazuje, że można używać wielu klauzul `result_expression` `Boolean_expression`.</span><span class="sxs-lookup"><span data-stu-id="7df44-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="7df44-107">NASTĘPNIE `result_expression`</span><span class="sxs-lookup"><span data-stu-id="7df44-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="7df44-108">Jest wyrażeniem zwracanym, gdy `Boolean_expression` oblicza `true`.</span><span class="sxs-lookup"><span data-stu-id="7df44-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="7df44-109">`result expression` jest dowolnym prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="7df44-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="7df44-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="7df44-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="7df44-111">Jest wyrażeniem zwracanym, jeśli żadna operacja porównania nie zostanie obliczona do `true`.</span><span class="sxs-lookup"><span data-stu-id="7df44-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="7df44-112">Jeśli ten argument zostanie pominięty i żadna operacja porównania nie zostanie obliczona do `true`, przypadek zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="7df44-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="7df44-113">`else_result_expression` jest dowolnym prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="7df44-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="7df44-114">Typy danych `else_result_expression` i wszystkie `result_expression` muszą być takie same lub muszą być niejawną konwersją.</span><span class="sxs-lookup"><span data-stu-id="7df44-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="7df44-115">GDY `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="7df44-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="7df44-116">Jest wyrażeniem `Boolean` obliczanym, gdy jest używany przeszukiwany format przypadku.</span><span class="sxs-lookup"><span data-stu-id="7df44-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="7df44-117">`Boolean_expression` jest dowolnym prawidłowym wyrażeniem `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7df44-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7df44-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7df44-118">Return Value</span></span>  
 <span data-ttu-id="7df44-119">Zwraca typ najwyższego pierwszeństwa z zestawu typów w `result_expression` i opcjonalne `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="7df44-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7df44-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7df44-120">Remarks</span></span>  
 <span data-ttu-id="7df44-121">Wyrażenie CASE [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przypomina wyrażenie CASE języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="7df44-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="7df44-122">Wyrażenie CASE służy do tworzenia serii testów warunkowych, aby określić, które wyrażenie zwróci odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="7df44-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="7df44-123">Ta forma wyrażenia case ma zastosowanie do serii co najmniej jednego wyrażenia `Boolean`, aby określić poprawne wyrażenie wyniku.</span><span class="sxs-lookup"><span data-stu-id="7df44-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="7df44-124">Funkcja CASE oblicza `Boolean_expression` dla każdej klauzuli WHEN w określonej kolejności i zwraca `result_expression` pierwszego `Boolean_expression`, który jest obliczany jako `true`.</span><span class="sxs-lookup"><span data-stu-id="7df44-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="7df44-125">Pozostałe wyrażenia nie są oceniane.</span><span class="sxs-lookup"><span data-stu-id="7df44-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="7df44-126">Jeśli żadna `Boolean_expression` nie zostanie obliczona do `true`, aparat bazy danych zwróci `else_result_expression` Jeśli określono klauzulę ELSE lub wartość null, jeśli nie określono klauzuli ELSE.</span><span class="sxs-lookup"><span data-stu-id="7df44-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="7df44-127">Instrukcja CASE nie może zwracać zestawu wielokrotnego.</span><span class="sxs-lookup"><span data-stu-id="7df44-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7df44-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7df44-128">Example</span></span>  
 <span data-ttu-id="7df44-129">Poniższe zapytanie Entity SQL używa wyrażenia CASE do obliczenia zestawu `Boolean` wyrażeń w celu określenia wyniku.</span><span class="sxs-lookup"><span data-stu-id="7df44-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="7df44-130">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7df44-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7df44-131">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="7df44-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7df44-132">Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7df44-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="7df44-133">Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="7df44-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="7df44-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7df44-134">See also</span></span>

- [<span data-ttu-id="7df44-135">THEN</span><span class="sxs-lookup"><span data-stu-id="7df44-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="7df44-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="7df44-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="7df44-137">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="7df44-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
