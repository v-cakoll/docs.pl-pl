---
title: '! (NIE) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f2f8df14df3c4e330af20ff3691cbf266bb95da0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="-not-entity-sql"></a><span data-ttu-id="04374-103">!</span><span class="sxs-lookup"><span data-stu-id="04374-103">!</span></span> <span data-ttu-id="04374-104">(NIE) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="04374-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="04374-105">Negacja `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="04374-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04374-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="04374-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="04374-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="04374-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="04374-108">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="04374-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04374-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04374-109">Remarks</span></span>  
 <span data-ttu-id="04374-110">Wykrzyknika (!) ma te same funkcje co operatora NOT.</span><span class="sxs-lookup"><span data-stu-id="04374-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04374-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="04374-111">Example</span></span>  
 <span data-ttu-id="04374-112">Następujące zapytanie SQL jednostki nawiązywał Negacja operatora NOT `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="04374-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="04374-113">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="04374-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="04374-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="04374-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="04374-115">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="04374-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="04374-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="04374-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="04374-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04374-117">See Also</span></span>  
 [<span data-ttu-id="04374-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="04374-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
