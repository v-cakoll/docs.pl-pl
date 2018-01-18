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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f3786724280cc077574f37e4d373c85faf5340f3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="-not-entity-sql"></a><span data-ttu-id="6ee0c-103">!</span><span class="sxs-lookup"><span data-stu-id="6ee0c-103">!</span></span> <span data-ttu-id="6ee0c-104">(NIE) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="6ee0c-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="6ee0c-105">Negacja `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6ee0c-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee0c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ee0c-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ee0c-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6ee0c-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="6ee0c-108">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="6ee0c-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ee0c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ee0c-109">Remarks</span></span>  
 <span data-ttu-id="6ee0c-110">Wykrzyknika (!) ma te same funkcje co operatora NOT.</span><span class="sxs-lookup"><span data-stu-id="6ee0c-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee0c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ee0c-111">Example</span></span>  
 <span data-ttu-id="6ee0c-112">Następujące zapytanie SQL jednostki nawiązywał Negacja operatora NOT `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6ee0c-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="6ee0c-113">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6ee0c-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6ee0c-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="6ee0c-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6ee0c-115">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6ee0c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6ee0c-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="6ee0c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="6ee0c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ee0c-117">See Also</span></span>  
 [<span data-ttu-id="6ee0c-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="6ee0c-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
