---
title: GDZIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 43c038e9ff0acfdeff88492aa2ca34fbf4ada94a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764317"
---
# <a name="where-entity-sql"></a><span data-ttu-id="b3fe9-102">GDZIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="b3fe9-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="b3fe9-103">Klauzula WHERE jest stosowana bezpośrednio po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b3fe9-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3fe9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3fe9-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3fe9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b3fe9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b3fe9-106">Typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="b3fe9-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3fe9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3fe9-107">Remarks</span></span>  
 <span data-ttu-id="b3fe9-108">Klauzula WHERE ma tej samej semantyki zgodnie z opisem dla [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3fe9-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b3fe9-109">Ogranicza obiekty utworzone przez wyrażenie zapytania dzięki ograniczeniu liczby elementów kolekcji źródłowej do tych, które przekazują warunku.</span><span class="sxs-lookup"><span data-stu-id="b3fe9-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="b3fe9-110">Wyrażenie `e` musi być typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="b3fe9-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="b3fe9-111">Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM a przed grupowania, porządkowanie ani projekcji ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="b3fe9-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="b3fe9-112">Wszystkie nazwy elementów zdefiniowanych w klauzuli FROM są widoczne dla wyrażenia w klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="b3fe9-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fe9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3fe9-113">See Also</span></span>  
 [<span data-ttu-id="b3fe9-114">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b3fe9-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b3fe9-115">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="b3fe9-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
