---
title: A następnie (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: d5f9f2b8c9d7397cbcd91fa52a95544fc66e4dce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184598"
---
# <a name="then-entity-sql"></a><span data-ttu-id="1ded5-102">A następnie (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1ded5-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="1ded5-103">Wynik w klauzuli WHEN, gdy daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="1ded5-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ded5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ded5-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ded5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1ded5-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="1ded5-106">Dowolne prawidłowe wyrażenie logiczne.</span><span class="sxs-lookup"><span data-stu-id="1ded5-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="1ded5-107">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="1ded5-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ded5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ded5-108">Remarks</span></span>  
 <span data-ttu-id="1ded5-109">Jeśli `when_expression` daje w wyniku wartość `true`, wynik jest odpowiedni `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="1ded5-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="1ded5-110">Jeśli żaden z po spełnieniu warunków `else-expression` jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="1ded5-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="1ded5-111">Jednak w przypadku nie `else-expression`, wynikiem jest wartość null.</span><span class="sxs-lookup"><span data-stu-id="1ded5-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="1ded5-112">Aby uzyskać przykład, zobacz [przypadek](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1ded5-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ded5-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ded5-113">Example</span></span>  
 <span data-ttu-id="1ded5-114">Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1ded5-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="1ded5-115">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1ded5-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1ded5-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1ded5-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1ded5-117">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1ded5-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="1ded5-118">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1ded5-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="1ded5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ded5-119">See also</span></span>

- [<span data-ttu-id="1ded5-120">CASE</span><span class="sxs-lookup"><span data-stu-id="1ded5-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [<span data-ttu-id="1ded5-121">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1ded5-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
