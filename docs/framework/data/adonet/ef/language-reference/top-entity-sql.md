---
title: TOP (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 10967ac87fa8f8504dc9a6a29be99401e620085e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="top-entity-sql"></a><span data-ttu-id="c4631-102">TOP (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c4631-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="c4631-103">Klauzula SELECT może mieć opcjonalne TOP Podklauzula następujące opcjonalne modyfikator ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="c4631-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="c4631-104">Klauzul podrzędnych TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="c4631-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4631-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4631-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4631-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c4631-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="c4631-107">Wyrażenie liczbowe, która określa liczbę wierszy, które mają zostać zwrócone.</span><span class="sxs-lookup"><span data-stu-id="c4631-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="c4631-108">`n`może to być literał liczbowy jednego lub jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="c4631-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4631-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4631-109">Remarks</span></span>  
 <span data-ttu-id="c4631-110">Wyrażenia TOP musi być jednym literałem lub jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="c4631-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="c4631-111">Jeśli używana jest literałem stałej, typ literału musi być niejawnie Awansowanie do Edm.Int64 (byte, int16, int32 lub int64 lub dowolnego typu dostawcy, który jest mapowany na typ, który jest Awansowanie do Edm.Int64) i jego wartość musi być większa lub równa zero.</span><span class="sxs-lookup"><span data-stu-id="c4631-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="c4631-112">W przeciwnym razie zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c4631-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="c4631-113">Jeśli parametr jest używany jako wyrażenie, typ parametru musi być również niejawnie Awansowanie do Edm.Int64, ale nie będzie żadnych weryfikację wartości rzeczywisty parametr podczas kompilacji ponieważ wartości parametrów opóźnienia jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="c4631-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="c4631-114">Poniżej przedstawiono przykład stałe wyrażenie TOP:</span><span class="sxs-lookup"><span data-stu-id="c4631-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="c4631-115">Poniżej przedstawiono przykład wyrażenia TOP sparametryzowanego:</span><span class="sxs-lookup"><span data-stu-id="c4631-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="c4631-116">TOP jest deterministyczna, chyba że zapytania są sortowane.</span><span class="sxs-lookup"><span data-stu-id="c4631-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="c4631-117">Jeśli wymagane jest deterministyczna wyników, należy użyć [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c4631-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="c4631-118">TOP i SKIP/LIMIT wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="c4631-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4631-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4631-119">Example</span></span>  
 <span data-ttu-id="c4631-120">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa góry określić górny jeden wiersz zwrócony z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="c4631-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="c4631-121">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c4631-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c4631-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c4631-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c4631-123">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c4631-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="c4631-124">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c4631-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="c4631-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4631-125">See Also</span></span>  
 [<span data-ttu-id="c4631-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="c4631-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="c4631-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="c4631-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="c4631-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="c4631-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="c4631-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c4631-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="c4631-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c4631-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
