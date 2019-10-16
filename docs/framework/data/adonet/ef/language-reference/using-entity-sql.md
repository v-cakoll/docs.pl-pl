---
title: Używanie (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319208"
---
# <a name="using-entity-sql"></a><span data-ttu-id="f9a48-102">Używanie (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f9a48-102">USING (Entity SQL)</span></span>
<span data-ttu-id="f9a48-103">Określa przestrzenie nazw używane w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="f9a48-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9a48-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9a48-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f9a48-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="f9a48-106">Określa krótszy alias do kwalifikowania przestrzeni nazw za pomocą.</span><span class="sxs-lookup"><span data-stu-id="f9a48-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="f9a48-107">Dowolna prawidłowa przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f9a48-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9a48-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9a48-108">Example</span></span>  
 <span data-ttu-id="f9a48-109">Poniższe zapytanie Entity SQL używa operatora USING, aby określić przestrzenie nazw używane w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="f9a48-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="f9a48-110">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f9a48-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f9a48-111">Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f9a48-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f9a48-112">Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f9a48-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9a48-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9a48-113">See also</span></span>

- [<span data-ttu-id="f9a48-114">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="f9a48-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="f9a48-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f9a48-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
