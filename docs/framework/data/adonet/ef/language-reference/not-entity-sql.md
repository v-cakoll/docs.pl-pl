---
title: '! (NIE) (Jednostka SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 51d3bdbc4adb0b5fd6275629219698dd9b42fa86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760380"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="4a59f-103">!</span><span class="sxs-lookup"><span data-stu-id="4a59f-103">!</span></span> <span data-ttu-id="4a59f-104">(NIE) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4a59f-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="4a59f-105">Neguje `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4a59f-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a59f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a59f-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a59f-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4a59f-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="4a59f-108">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="4a59f-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a59f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a59f-109">Remarks</span></span>  
 <span data-ttu-id="4a59f-110">Wykrzyknika (!) ma taką samą funkcjonalność jak NOT operator.</span><span class="sxs-lookup"><span data-stu-id="4a59f-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a59f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a59f-111">Example</span></span>  
 <span data-ttu-id="4a59f-112">Następujące zapytanie SQL jednostki używa operatora NOT do neguje `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4a59f-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="4a59f-113">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4a59f-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4a59f-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4a59f-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4a59f-115">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4a59f-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4a59f-116">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="4a59f-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="4a59f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a59f-117">See also</span></span>

- [<span data-ttu-id="4a59f-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4a59f-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
