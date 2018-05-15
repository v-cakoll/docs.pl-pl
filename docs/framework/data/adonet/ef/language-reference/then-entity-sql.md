---
title: NASTĘPNIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 5f0bbb0cadd736d476077685e08ba1a03b9c4001
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="then-entity-sql"></a><span data-ttu-id="5f519-102">NASTĘPNIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="5f519-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="5f519-103">Wynik klauzuli WHEN podczas daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="5f519-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f519-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f519-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f519-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5f519-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="5f519-106">Prawidłowe wyrażenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="5f519-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="5f519-107">Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="5f519-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f519-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f519-108">Remarks</span></span>  
 <span data-ttu-id="5f519-109">Jeśli `when_expression` daje w wyniku wartość `true`, wynikiem jest odpowiednie `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="5f519-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="5f519-110">Jeśli żadna z WHEN warunki są spełnione, `else-expression` oceny.</span><span class="sxs-lookup"><span data-stu-id="5f519-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="5f519-111">Jednak w przypadku nie `else-expression`, wynikiem jest wartość null.</span><span class="sxs-lookup"><span data-stu-id="5f519-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="5f519-112">Na przykład zobacz [przypadku](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5f519-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f519-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f519-113">Example</span></span>  
 <span data-ttu-id="5f519-114">Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5f519-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="5f519-115">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5f519-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5f519-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="5f519-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5f519-117">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5f519-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="5f519-118">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="5f519-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="5f519-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f519-119">See Also</span></span>  
 [<span data-ttu-id="5f519-120">CASE</span><span class="sxs-lookup"><span data-stu-id="5f519-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="5f519-121">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5f519-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
