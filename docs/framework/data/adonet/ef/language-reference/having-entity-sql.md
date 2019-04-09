---
title: POSIADANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 19da828d3c7e7763c3dd9ba0e34da8849f90cf0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155145"
---
# <a name="having-entity-sql"></a><span data-ttu-id="069ae-102">POSIADANIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="069ae-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="069ae-103">Określa warunek wyszukiwania dla grupy lub agregacji.</span><span class="sxs-lookup"><span data-stu-id="069ae-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="069ae-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="069ae-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="069ae-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="069ae-106">Określa warunek wyszukiwania określający grupę lub agregacji spełnić.</span><span class="sxs-lookup"><span data-stu-id="069ae-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="069ae-107">W klauzuli HAVING HAVING jest używany z GROUP BY ALL, zastępuje wszystkie.</span><span class="sxs-lookup"><span data-stu-id="069ae-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="069ae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="069ae-108">Remarks</span></span>  
 <span data-ttu-id="069ae-109">W klauzuli HAVING pozwala określić dodatkowy warunek filtrowania wynik grupowanie.</span><span class="sxs-lookup"><span data-stu-id="069ae-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="069ae-110">W przypadku braku klauzuli GROUP BY jest określona w wyrażeniu zapytania, przyjmowana jest niejawne grupy jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="069ae-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069ae-111">HAVING mogą być używane tylko z [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="069ae-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="069ae-112">Gdy [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) jest nie używane HAVING zachowuje się jak klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="069ae-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="069ae-113">W klauzuli HAVING działa jak klauzuli WHERE, chyba że zostanie zastosowane po wykonaniu operacji GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="069ae-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="069ae-114">Oznacza to, że w klauzuli HAVING można tylko odwołuje się do grupowania aliasów i agregacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="069ae-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="069ae-115">Poprzedni ogranicza grupy tylko do tych, które zawierają więcej niż jeden produkt.</span><span class="sxs-lookup"><span data-stu-id="069ae-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="069ae-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="069ae-116">Example</span></span>  
 <span data-ttu-id="069ae-117">Następujące zapytanie SQL jednostki używa operatorów HAVING i GROUP BY w celu określenia warunku wyszukiwania dla grupy lub agregacji.</span><span class="sxs-lookup"><span data-stu-id="069ae-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="069ae-118">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="069ae-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="069ae-119">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="069ae-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="069ae-120">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="069ae-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="069ae-121">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="069ae-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="069ae-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="069ae-122">See also</span></span>

- [<span data-ttu-id="069ae-123">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="069ae-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="069ae-124">Wyrażenia kwerend</span><span class="sxs-lookup"><span data-stu-id="069ae-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
