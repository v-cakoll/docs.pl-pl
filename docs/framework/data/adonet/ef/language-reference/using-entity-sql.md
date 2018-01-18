---
title: "Za pomocą (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d1a47102c7057918c981b53f920afef09b20afad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="using-entity-sql"></a><span data-ttu-id="6ff39-102">Za pomocą (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="6ff39-102">USING (Entity SQL)</span></span>
<span data-ttu-id="6ff39-103">Określa obszarów nazw używanych w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="6ff39-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ff39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ff39-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ff39-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6ff39-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="6ff39-106">Określa krótszą alias na kwalifikować się obszar nazw o.</span><span class="sxs-lookup"><span data-stu-id="6ff39-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="6ff39-107">Dowolny prawidłowy obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="6ff39-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff39-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ff39-108">Example</span></span>  
 <span data-ttu-id="6ff39-109">Następujące zapytanie SQL jednostki używa operatora USING do określania przestrzeni nazw używany w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="6ff39-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="6ff39-110">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="6ff39-110">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6ff39-111">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6ff39-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="6ff39-112">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="6ff39-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ff39-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ff39-113">See Also</span></span>  
 [<span data-ttu-id="6ff39-114">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="6ff39-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [<span data-ttu-id="6ff39-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="6ff39-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
