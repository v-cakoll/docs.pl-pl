---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: e637218bb3db69d4b09fd734b939fd30f50ed806
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961890"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="d7efa-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d7efa-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="d7efa-103">Stronicowanie fizyczne można wykonać za pomocą klauzuli LIMIT w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d7efa-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="d7efa-104">Nie można użyć limitu niezależnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d7efa-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7efa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7efa-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7efa-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7efa-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="d7efa-107">Liczba elementów, które zostaną wybrane.</span><span class="sxs-lookup"><span data-stu-id="d7efa-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="d7efa-108">Jeśli Podklauzula wyrażenia limitu jest obecna w klauzuli ORDER BY, zapytanie zostanie posortowane zgodnie z specyfikacją sortowania, a wynikowa liczba wierszy zostanie ograniczona przez wyrażenie limitu.</span><span class="sxs-lookup"><span data-stu-id="d7efa-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="d7efa-109">Na przykład LIMIT 5 ograniczy wynik do 5 wystąpień lub wierszy.</span><span class="sxs-lookup"><span data-stu-id="d7efa-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="d7efa-110">LIMIT jest funkcjonalnie równoważny z GÓRNą opcją, ponieważ LIMIT wymaga obecności klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d7efa-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="d7efa-111">Nie można używać pominięcia i limitu niezależnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="d7efa-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7efa-112">Zapytanie SQL jednostki zostanie uznane za nieprawidłowe, jeśli w tym samym wyrażeniu zapytania występuje modyfikator TOP i SKIP sub.</span><span class="sxs-lookup"><span data-stu-id="d7efa-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="d7efa-113">Zapytanie powinno być ponownie zapisywane przez zmianę wyrażenia TOP na wyrażenie OGRANICZAjące.</span><span class="sxs-lookup"><span data-stu-id="d7efa-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7efa-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7efa-114">Example</span></span>  
 <span data-ttu-id="d7efa-115">Poniższe zapytanie Entity SQL używa operatora ORDER BY z LIMITem, aby określić kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="d7efa-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="d7efa-116">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d7efa-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7efa-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d7efa-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d7efa-118">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="d7efa-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d7efa-119">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d7efa-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="d7efa-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7efa-120">See also</span></span>

- [<span data-ttu-id="d7efa-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="d7efa-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="d7efa-122">[Instrukcje: Strona za poorednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d7efa-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="d7efa-123">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="d7efa-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="d7efa-124">TOP</span><span class="sxs-lookup"><span data-stu-id="d7efa-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
