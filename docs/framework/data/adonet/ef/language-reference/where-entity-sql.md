---
title: GDZIE (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 38d1b7e2b7662ef3b2fedbcce6ac23ce55a5468f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="where-entity-sql"></a><span data-ttu-id="38f58-102">GDZIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="38f58-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="38f58-103">Klauzula WHERE jest stosowana bezpośrednio po [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="38f58-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38f58-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="38f58-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38f58-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="38f58-106">Typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="38f58-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f58-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38f58-107">Remarks</span></span>  
 <span data-ttu-id="38f58-108">Klauzula WHERE ma tej samej semantyki zgodnie z opisem dla [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38f58-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="38f58-109">Ogranicza obiekty utworzone przez wyrażenie zapytania dzięki ograniczeniu liczby elementów kolekcji źródłowej do tych, które przekazują warunku.</span><span class="sxs-lookup"><span data-stu-id="38f58-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="38f58-110">Wyrażenie `e` musi być typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="38f58-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="38f58-111">Klauzula WHERE jest stosowana bezpośrednio po klauzuli FROM a przed grupowania, porządkowanie ani projekcji ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="38f58-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="38f58-112">Wszystkie nazwy elementów zdefiniowanych w klauzuli FROM są widoczne dla wyrażenia w klauzuli WHERE.</span><span class="sxs-lookup"><span data-stu-id="38f58-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f58-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38f58-113">See Also</span></span>  
 [<span data-ttu-id="38f58-114">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="38f58-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="38f58-115">Wyrażenia zapytań</span><span class="sxs-lookup"><span data-stu-id="38f58-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
