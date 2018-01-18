---
title: LIMIT (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f6933c7e3d5b3e7ed5fd4b55974e5869ab83a982
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="limit-entity-sql"></a><span data-ttu-id="051f4-102">LIMIT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="051f4-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="051f4-103">Stronicowania fizycznych można przeprowadzić za pomocą Podklauzula LIMIT w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="051f4-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="051f4-104">LIMIT nie umożliwia oddzielnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="051f4-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="051f4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="051f4-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="051f4-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="051f4-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="051f4-107">Liczba elementów, które zostaną wybrane.</span><span class="sxs-lookup"><span data-stu-id="051f4-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="051f4-108">Jeśli LIMIT klauzul podrzędnych wyrażenia znajduje się w klauzuli ORDER BY, zapytanie będzie można sortować według specyfikacji sortowania i wynikowa liczba wierszy zostanie ograniczony przez wyrażenie LIMIT.</span><span class="sxs-lookup"><span data-stu-id="051f4-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="051f4-109">Na przykład LIMIT 5 ogranicza zestaw wyników do 5 wystąpień lub wierszy.</span><span class="sxs-lookup"><span data-stu-id="051f4-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="051f4-110">LIMIT jest funkcjonalnym odpowiednikiem TOP z wyjątkiem, że LIMIT wymaga klauzuli ORDER BY obecności.</span><span class="sxs-lookup"><span data-stu-id="051f4-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="051f4-111">POMIŃ i LIMIT można użyć niezależnie, wraz z klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="051f4-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="051f4-112">Zapytanie Sql jednostki będą uznawane za nieprawidłowe w przypadku GÓRNEGO modyfikator i klauzul podrzędnych SKIP znajduje się w jednym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="051f4-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="051f4-113">Zapytanie powinno ulegną, zmieniając LIMIT wyrażenie wyrażenia TOP.</span><span class="sxs-lookup"><span data-stu-id="051f4-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="051f4-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="051f4-114">Example</span></span>  
 <span data-ttu-id="051f4-115">Następujące zapytanie SQL jednostki używa operatora ORDER BY limit, aby określić kolejność sortowania użyć obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="051f4-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="051f4-116">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="051f4-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="051f4-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="051f4-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="051f4-118">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="051f4-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="051f4-119">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="051f4-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="051f4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="051f4-120">See Also</span></span>  
 [<span data-ttu-id="051f4-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="051f4-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="051f4-122">Porady: powoduje strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="051f4-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="051f4-123">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="051f4-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="051f4-124">TOP</span><span class="sxs-lookup"><span data-stu-id="051f4-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
