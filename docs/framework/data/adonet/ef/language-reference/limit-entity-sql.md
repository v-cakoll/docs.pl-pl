---
title: LIMIT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b267e97860a2cb071b857224455f01b73115c72d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760678"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="1aa6e-102">LIMIT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="1aa6e-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="1aa6e-103">Stronicowanie fizycznych można wykonać przy użyciu Podklauzula LIMIT w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="1aa6e-104">OGRANICZENIE nie może służyć oddzielnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa6e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1aa6e-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1aa6e-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1aa6e-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="1aa6e-107">Liczba elementów, które zostaną wybrane.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="1aa6e-108">Jeśli LIMIT wyrażenia Podklauzula znajduje się w klauzuli ORDER BY, zapytania będą sortowane według specyfikacji sortowania i wynikowa liczba wierszy, zostanie nałożone przez wyrażenie LIMIT.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="1aa6e-109">Na przykład LIMIT 5 ograniczyć zestaw wyników do 5 wystąpień lub wiersze.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="1aa6e-110">LIMIT jest funkcjonalnym odpowiednikiem GÓRNEJ z wyjątkiem, że LIMIT wymaga klauzuli ORDER BY być obecne.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="1aa6e-111">POMIŃ i LIMIT może służyć niezależnie wraz z klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1aa6e-112">Zapytanie Sql jednostki będą uznawane za nieprawidłowe w przypadku najważniejszych modyfikator i POMIŃ Podklauzula znajduje się w jednym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="1aa6e-113">Powinien zostać przepisany zapytania, zmieniając wyrażenia TOP i LIMIT wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa6e-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1aa6e-114">Example</span></span>  
 <span data-ttu-id="1aa6e-115">Następujące zapytanie SQL jednostki używa operatora klauzuli ORDER BY limit, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="1aa6e-116">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1aa6e-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1aa6e-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="1aa6e-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1aa6e-118">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1aa6e-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1aa6e-119">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1aa6e-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="1aa6e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1aa6e-120">See also</span></span>

- [<span data-ttu-id="1aa6e-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="1aa6e-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="1aa6e-122">[Instrukcje: Przejrzyj wyniki zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1aa6e-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="1aa6e-123">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="1aa6e-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="1aa6e-124">TOP</span><span class="sxs-lookup"><span data-stu-id="1aa6e-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
