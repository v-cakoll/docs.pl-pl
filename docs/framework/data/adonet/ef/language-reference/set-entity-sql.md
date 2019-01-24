---
title: ZESTAW (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: b6adce314e5d4fb1e4077b0efef758d07444e496
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744443"
---
# <a name="set-entity-sql"></a><span data-ttu-id="e72a1-102">ZESTAW (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="e72a1-102">SET (Entity SQL)</span></span>
<span data-ttu-id="e72a1-103">Wyrażenie zestawu jest używana do konwersji kolekcji obiektów do zestawu, reaguje nową kolekcję z wszystkich elementów zduplikowane usunięte.</span><span class="sxs-lookup"><span data-stu-id="e72a1-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e72a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e72a1-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e72a1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e72a1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e72a1-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="e72a1-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e72a1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e72a1-107">Remarks</span></span>  
 <span data-ttu-id="e72a1-108">Wyrażenie zestawu `SET(c)` jest logicznie równoważne wybierz następującą instrukcję:</span><span class="sxs-lookup"><span data-stu-id="e72a1-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="e72a1-109">`SET` Przykładem jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="e72a1-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e72a1-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="e72a1-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e72a1-111">Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="e72a1-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e72a1-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e72a1-112">Example</span></span>  
 <span data-ttu-id="e72a1-113">Następujące zapytanie SQL jednostki użyto wyrażenia zestawu do przekonwertowania kolekcji obiektów do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e72a1-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="e72a1-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e72a1-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e72a1-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e72a1-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e72a1-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e72a1-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="e72a1-117">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e72a1-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="e72a1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e72a1-118">See also</span></span>
- [<span data-ttu-id="e72a1-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e72a1-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
