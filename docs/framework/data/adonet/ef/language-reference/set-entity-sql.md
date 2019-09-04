---
title: Ustaw (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249238"
---
# <a name="set-entity-sql"></a><span data-ttu-id="b705d-102">Ustaw (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b705d-102">SET (Entity SQL)</span></span>
<span data-ttu-id="b705d-103">Wyrażenie SET służy do konwertowania kolekcji obiektów do zestawu przez wypróbowanie nowej kolekcji z usuniętymi wszystkimi zduplikowanymi elementami.</span><span class="sxs-lookup"><span data-stu-id="b705d-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b705d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b705d-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b705d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b705d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b705d-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="b705d-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b705d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b705d-107">Remarks</span></span>  
 <span data-ttu-id="b705d-108">Wyrażenie `SET(c)` Set jest logicznie równoważne z następującą instrukcją SELECT:</span><span class="sxs-lookup"><span data-stu-id="b705d-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="b705d-109">`SET`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="b705d-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="b705d-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="b705d-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="b705d-111">Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.</span><span class="sxs-lookup"><span data-stu-id="b705d-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b705d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b705d-112">Example</span></span>  
 <span data-ttu-id="b705d-113">Poniższe zapytanie Entity SQL używa wyrażenia zestawu do konwertowania kolekcji obiektów na zestaw.</span><span class="sxs-lookup"><span data-stu-id="b705d-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="b705d-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b705d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b705d-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="b705d-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b705d-116">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="b705d-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="b705d-117">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b705d-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="b705d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b705d-118">See also</span></span>

- [<span data-ttu-id="b705d-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b705d-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
