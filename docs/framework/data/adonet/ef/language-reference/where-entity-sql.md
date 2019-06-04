---
title: GDZIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489850"
---
# <a name="where-entity-sql"></a><span data-ttu-id="4f2ae-102">GDZIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="4f2ae-103">Bezpośrednio po zastosowaniu klauzuli WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f2ae-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4f2ae-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4f2ae-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4f2ae-106">Typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f2ae-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f2ae-107">Remarks</span></span>  
 <span data-ttu-id="4f2ae-108">Klauzula WHERE ma tą samą semantyką zgodnie z opisem języka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="4f2ae-109">Ogranicza obiekty utworzone przez wyrażenie zapytania, ograniczając elementy kolekcji źródłowej do tych, które upłynąć warunek.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="4f2ae-110">Wyrażenie `e` musi być typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="4f2ae-111">Klauzula WHERE jest stosowany bezpośrednio po elemencie klauzuli FROM a przed dowolnego grupowania, porządkowanie lub projekcji ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="4f2ae-112">Wszystkie nazwy elementów, które określono w klauzuli FROM są widoczne dla wyrażenia w klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2ae-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f2ae-113">See also</span></span>

- [<span data-ttu-id="4f2ae-114">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4f2ae-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="4f2ae-115">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="4f2ae-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
