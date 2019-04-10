---
title: Za pomocą (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: e14b7857a65898683939647c872c48d0b3fe458a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297866"
---
# <a name="using-entity-sql"></a><span data-ttu-id="0e0a7-102">Za pomocą (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="0e0a7-102">USING (Entity SQL)</span></span>
<span data-ttu-id="0e0a7-103">Określa przestrzeń nazw używaną w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="0e0a7-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e0a7-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e0a7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0e0a7-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="0e0a7-106">Określa krótszy alias do kwalifikowania przestrzeni nazw za pomocą.</span><span class="sxs-lookup"><span data-stu-id="0e0a7-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="0e0a7-107">Dowolny prawidłowy obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="0e0a7-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e0a7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e0a7-108">Example</span></span>  
 <span data-ttu-id="0e0a7-109">Następujące zapytanie SQL jednostki używa operatora USING do określania przestrzeni nazw używany w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="0e0a7-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="0e0a7-110">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="0e0a7-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0e0a7-111">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0e0a7-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="0e0a7-112">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0e0a7-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e0a7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e0a7-113">See also</span></span>

- [<span data-ttu-id="0e0a7-114">Namespaces</span><span class="sxs-lookup"><span data-stu-id="0e0a7-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [<span data-ttu-id="0e0a7-115">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0e0a7-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
