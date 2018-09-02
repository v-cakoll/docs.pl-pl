---
title: LIMIT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 4534148279ece3b00c45f61c6a35a74a64ca3b6f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406890"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="b5b3b-102">LIMIT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="b5b3b-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="b5b3b-103">Stronicowanie fizycznych można wykonać przy użyciu Podklauzula LIMIT w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="b5b3b-104">OGRANICZENIE nie może służyć oddzielnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b3b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5b3b-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5b3b-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b5b3b-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="b5b3b-107">Liczba elementów, które zostaną wybrane.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="b5b3b-108">Jeśli LIMIT wyrażenia Podklauzula znajduje się w klauzuli ORDER BY, zapytania będą sortowane według specyfikacji sortowania i wynikowa liczba wierszy, zostanie nałożone przez wyrażenie LIMIT.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="b5b3b-109">Na przykład LIMIT 5 ograniczyć zestaw wyników do 5 wystąpień lub wiersze.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="b5b3b-110">LIMIT jest funkcjonalnym odpowiednikiem GÓRNEJ z wyjątkiem, że LIMIT wymaga klauzuli ORDER BY być obecne.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="b5b3b-111">POMIŃ i LIMIT może służyć niezależnie wraz z klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5b3b-112">Zapytanie Sql jednostki będą uznawane za nieprawidłowe w przypadku najważniejszych modyfikator i POMIŃ Podklauzula znajduje się w jednym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="b5b3b-113">Powinien zostać przepisany zapytania, zmieniając wyrażenia TOP i LIMIT wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5b3b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5b3b-114">Example</span></span>  
 <span data-ttu-id="b5b3b-115">Następujące zapytanie SQL jednostki używa operatora klauzuli ORDER BY limit, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="b5b3b-116">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b5b3b-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b5b3b-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b5b3b-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b5b3b-118">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytania, że zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b5b3b-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b5b3b-119">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b5b3b-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="b5b3b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5b3b-120">See Also</span></span>  
 [<span data-ttu-id="b5b3b-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="b5b3b-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="b5b3b-122">Porady: wyniki strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="b5b3b-122">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="b5b3b-123">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="b5b3b-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="b5b3b-124">TOP</span><span class="sxs-lookup"><span data-stu-id="b5b3b-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
