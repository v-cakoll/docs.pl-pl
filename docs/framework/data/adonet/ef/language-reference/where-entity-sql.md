---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319182"
---
# <a name="where-entity-sql"></a><span data-ttu-id="8f2fb-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8f2fb-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="8f2fb-103">Klauzula WHERE jest stosowana bezpośrednio po klauzuli [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="8f2fb-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f2fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f2fb-104">Syntax</span></span>  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f2fb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8f2fb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8f2fb-106">Typ wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="8f2fb-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f2fb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f2fb-107">Remarks</span></span>  
 <span data-ttu-id="8f2fb-108">Klauzula WHERE ma tę samą semantykę, jak opisano w języku Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="8f2fb-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="8f2fb-109">Ogranicza obiekty utworzone przez wyrażenie zapytania przez ograniczenie elementów kolekcji źródłowych do tych, które przechodzą warunek.</span><span class="sxs-lookup"><span data-stu-id="8f2fb-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```sql  
select c from cs as c where e  
```  
  
 <span data-ttu-id="8f2fb-110">Wyrażenie `e` musi mieć typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="8f2fb-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="8f2fb-111">Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM i przed utworzeniem grupowania, porządkowania lub projekcji.</span><span class="sxs-lookup"><span data-stu-id="8f2fb-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="8f2fb-112">Wszystkie nazwy elementów zdefiniowane w klauzuli FROM są widoczne dla wyrażenia klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="8f2fb-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2fb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f2fb-113">See also</span></span>

- [<span data-ttu-id="8f2fb-114">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="8f2fb-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8f2fb-115">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="8f2fb-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
