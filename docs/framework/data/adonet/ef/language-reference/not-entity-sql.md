---
title: '! NIEMOŻLIWE (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319517"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="ab1df-103">!</span><span class="sxs-lookup"><span data-stu-id="ab1df-103">!</span></span> <span data-ttu-id="ab1df-104">NIEMOŻLIWE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ab1df-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="ab1df-105">Wyklucza wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ab1df-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab1df-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab1df-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a><span data-ttu-id="ab1df-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ab1df-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="ab1df-108">Dowolne prawidłowe wyrażenie zwracające wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="ab1df-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab1df-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab1df-109">Remarks</span></span>  
 <span data-ttu-id="ab1df-110">Wykrzyknik (!) ma takie same funkcje jak operator NOT.</span><span class="sxs-lookup"><span data-stu-id="ab1df-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab1df-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab1df-111">Example</span></span>  
 <span data-ttu-id="ab1df-112">Poniższe zapytanie Entity SQL używa operatora NOT, aby negacja wyrażenia `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ab1df-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="ab1df-113">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ab1df-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ab1df-114">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="ab1df-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ab1df-115">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ab1df-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ab1df-116">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="ab1df-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="ab1df-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab1df-117">See also</span></span>

- [<span data-ttu-id="ab1df-118">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="ab1df-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
