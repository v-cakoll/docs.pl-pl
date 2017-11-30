---
title: O (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a64bc0c9b5e1358046e78429780af796f60e404e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="having-entity-sql"></a><span data-ttu-id="7d6f9-102">O (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="7d6f9-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="7d6f9-103">Określa warunek wyszukiwania dla grupy lub agregacja.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d6f9-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d6f9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7d6f9-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="7d6f9-106">Określa warunek wyszukiwania dla grupy lub agregacji spełnić.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="7d6f9-107">Klauzula HAVING HAVING jest używana z GROUP BY ALL, zastępuje wszystkie.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d6f9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d6f9-108">Remarks</span></span>  
 <span data-ttu-id="7d6f9-109">Klauzula HAVING pozwala określić dodatkowy warunek filtrowania wyniku grupowanie.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="7d6f9-110">Jeśli nie określono żadnych klauzuli GROUP BY w wyrażeniu zapytania, przyjmowana jest niejawne grupy jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d6f9-111">HAVING może być używany tylko z [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="7d6f9-112">Gdy [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) jest nieużywane, HAVING zachowuje się jak klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="7d6f9-113">Klauzula HAVING działa jak w klauzuli WHERE, z tą różnicą, że jest stosowana po wykonaniu operacji GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="7d6f9-114">Oznacza to, że w klauzuli HAVING można tylko odwołuje się do grupowania aliasy i wartościami zagregowanymi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="7d6f9-115">Poprzedni ogranicza grupy tylko do tych zawierających więcej niż jeden produkt.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d6f9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d6f9-116">Example</span></span>  
 <span data-ttu-id="7d6f9-117">Następujące zapytanie SQL jednostki używa operatory HAVING i GROUP BY do określania warunku wyszukiwania dla grupy lub agregacja.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="7d6f9-118">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7d6f9-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7d6f9-119">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="7d6f9-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7d6f9-120">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7d6f9-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="7d6f9-121">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="7d6f9-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="7d6f9-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d6f9-122">See Also</span></span>  
 [<span data-ttu-id="7d6f9-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="7d6f9-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="7d6f9-124">Wyrażenia zapytań</span><span class="sxs-lookup"><span data-stu-id="7d6f9-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
