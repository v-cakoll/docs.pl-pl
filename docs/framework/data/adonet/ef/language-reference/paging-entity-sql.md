---
title: Stronicowania (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6188587a8b588128092f5d9f02f6962159b928e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="paging-entity-sql"></a><span data-ttu-id="fa9a9-102">Stronicowania (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="fa9a9-102">Paging (Entity SQL)</span></span>
<span data-ttu-id="fa9a9-103">Stronicowanie fizycznych można wykonać za pomocą [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-103">Physical paging can be performed by using the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="fa9a9-104">Do wykonania fizycznego stronicowania w sposób niejednoznaczny, należy używać SKIP i LIMIT.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="fa9a9-105">Jeśli chcesz ograniczyć liczbę wierszy w wyniku w sposób z systemem innym niż determinsitic, należy użyć [GÓRNEJ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fa9a9-105">If you only want to restrict the number of rows in the result in a non-determinsitic way, you should use [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span> <span data-ttu-id="fa9a9-106">TOP i SKIP/LIMIT wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="fa9a9-107">TOP — omówienie</span><span class="sxs-lookup"><span data-stu-id="fa9a9-107">TOP Overview</span></span>  
 <span data-ttu-id="fa9a9-108">Klauzula SELECT może mieć opcjonalne TOP Podklauzula następujące opcjonalne modyfikator ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="fa9a9-109">Klauzul podrzędnych TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="fa9a9-110">Aby uzyskać więcej informacji, zobacz [GÓRNEJ](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fa9a9-110">For more information, see [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="fa9a9-111">POMIŃ i LIMIT — omówienie</span><span class="sxs-lookup"><span data-stu-id="fa9a9-111">SKIP And LIMIT Overview</span></span>  
 <span data-ttu-id="fa9a9-112">POMIŃ i LIMIT są częścią klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="fa9a9-113">Jeśli klauzul podrzędnych SKIP w wyrażeniu znajduje się w klauzuli ORDER BY, będzie można posortować wyników według specyfikacji sortowania i zestaw wyników zawiera wiersze, zaczynając od następnego wiersza od razu po wyrażeniu SKIP.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="fa9a9-114">Na przykład 5 POMIŃ Pomiń pierwsze pięć wiersze i zwrócenia z wiersza szóstego do przodu.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="fa9a9-115">Jeśli LIMIT klauzul podrzędnych wyrażenia znajduje się w klauzuli ORDER BY, zapytanie będzie można sortować według specyfikacji sortowania i wynikowa liczba wierszy zostanie ograniczony przez wyrażenie LIMIT.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="fa9a9-116">Na przykład LIMIT 5 ogranicza zestaw wyników do pięciu wystąpień lub wierszy.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="fa9a9-117">POMIŃ i LIMIT nie muszą być używane razem; można użyć tylko POMIŃ lub po prostu ograniczenia z klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="fa9a9-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="fa9a9-118">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="fa9a9-118">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="fa9a9-119">POMIŃ</span><span class="sxs-lookup"><span data-stu-id="fa9a9-119">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [<span data-ttu-id="fa9a9-120">LIMIT</span><span class="sxs-lookup"><span data-stu-id="fa9a9-120">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [<span data-ttu-id="fa9a9-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="fa9a9-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa9a9-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa9a9-122">See Also</span></span>  
 [<span data-ttu-id="fa9a9-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="fa9a9-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="fa9a9-124">Omówienie SQL jednostki</span><span class="sxs-lookup"><span data-stu-id="fa9a9-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="fa9a9-125">Porady: powoduje strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="fa9a9-125">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
