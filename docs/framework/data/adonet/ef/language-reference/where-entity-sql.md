---
title: GDZIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 02eeaeb8cfa335e5545b26d3d52b91c4e1614629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879440"
---
# <a name="where-entity-sql"></a><span data-ttu-id="ff4b1-102">GDZIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="ff4b1-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="ff4b1-103">Bezpośrednio po zastosowaniu klauzuli WHERE [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ff4b1-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff4b1-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff4b1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ff4b1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ff4b1-106">Typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="ff4b1-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff4b1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff4b1-107">Remarks</span></span>  
 <span data-ttu-id="ff4b1-108">Klauzula WHERE ma tą samą semantyką zgodnie z opisem dla [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff4b1-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ff4b1-109">Ogranicza obiekty utworzone przez wyrażenie zapytania, ograniczając elementy kolekcji źródłowej do tych, które upłynąć warunek.</span><span class="sxs-lookup"><span data-stu-id="ff4b1-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="ff4b1-110">Wyrażenie `e` musi być typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="ff4b1-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="ff4b1-111">Klauzula WHERE jest stosowany bezpośrednio po elemencie klauzuli FROM a przed dowolnego grupowania, porządkowanie lub projekcji ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="ff4b1-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="ff4b1-112">Wszystkie nazwy elementów, które określono w klauzuli FROM są widoczne dla wyrażenia w klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="ff4b1-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4b1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff4b1-113">See also</span></span>

- [<span data-ttu-id="ff4b1-114">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ff4b1-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="ff4b1-115">Wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="ff4b1-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
