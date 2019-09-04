---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248486"
---
# <a name="where-entity-sql"></a><span data-ttu-id="3af1a-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3af1a-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="3af1a-103">Klauzula WHERE jest stosowana bezpośrednio po klauzuli [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="3af1a-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3af1a-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3af1a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3af1a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3af1a-106">Typ wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="3af1a-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3af1a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3af1a-107">Remarks</span></span>  
 <span data-ttu-id="3af1a-108">Klauzula WHERE ma tę samą semantykę, jak opisano w języku Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="3af1a-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="3af1a-109">Ogranicza obiekty utworzone przez wyrażenie zapytania przez ograniczenie elementów kolekcji źródłowych do tych, które przechodzą warunek.</span><span class="sxs-lookup"><span data-stu-id="3af1a-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="3af1a-110">Wyrażenie `e` musi mieć typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="3af1a-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="3af1a-111">Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM i przed utworzeniem grupowania, porządkowania lub projekcji.</span><span class="sxs-lookup"><span data-stu-id="3af1a-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="3af1a-112">Wszystkie nazwy elementów zdefiniowane w klauzuli FROM są widoczne dla wyrażenia klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="3af1a-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af1a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3af1a-113">See also</span></span>

- [<span data-ttu-id="3af1a-114">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3af1a-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3af1a-115">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="3af1a-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
