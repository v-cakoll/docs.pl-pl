---
title: '! NIEMOŻLIWE (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 4055d56d878b817fe88bb0dacb53ea39061bc4b2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249861"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="c8311-103">!</span><span class="sxs-lookup"><span data-stu-id="c8311-103">!</span></span> <span data-ttu-id="c8311-104">NIEMOŻLIWE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c8311-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="c8311-105">`Boolean` Wyklucza wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="c8311-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8311-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8311-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8311-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c8311-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="c8311-108">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="c8311-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8311-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8311-109">Remarks</span></span>  
 <span data-ttu-id="c8311-110">Wykrzyknik (!) ma takie same funkcje jak operator NOT.</span><span class="sxs-lookup"><span data-stu-id="c8311-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8311-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8311-111">Example</span></span>  
 <span data-ttu-id="c8311-112">Poniższe zapytanie Entity SQL używa operatora not, aby Negacja `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c8311-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="c8311-113">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c8311-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c8311-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c8311-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c8311-115">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="c8311-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c8311-116">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c8311-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="c8311-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8311-117">See also</span></span>

- [<span data-ttu-id="c8311-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c8311-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
