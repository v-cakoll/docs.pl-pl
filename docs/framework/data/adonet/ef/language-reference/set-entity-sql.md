---
title: Ustaw (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 9d4cdeac317509fd61741a19276a6764a1c2bfce
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319354"
---
# <a name="set-entity-sql"></a><span data-ttu-id="4dcd9-102">Ustaw (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4dcd9-102">SET (Entity SQL)</span></span>
<span data-ttu-id="4dcd9-103">Wyrażenie SET służy do konwertowania kolekcji obiektów do zestawu przez wypróbowanie nowej kolekcji z usuniętymi wszystkimi zduplikowanymi elementami.</span><span class="sxs-lookup"><span data-stu-id="4dcd9-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dcd9-104">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4dcd9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4dcd9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4dcd9-106">Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="4dcd9-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dcd9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dcd9-107">Remarks</span></span>  
 <span data-ttu-id="4dcd9-108">Wyrażenie Set `SET(c)` jest logicznym odpowiednikiem następującej instrukcji SELECT:</span><span class="sxs-lookup"><span data-stu-id="4dcd9-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="4dcd9-109">`SET` to jeden z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4dcd9-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4dcd9-110">Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="4dcd9-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4dcd9-111">Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla operatorów ustawionych [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4dcd9-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dcd9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4dcd9-112">Example</span></span>  
 <span data-ttu-id="4dcd9-113">Poniższe zapytanie Entity SQL używa wyrażenia zestawu do konwertowania kolekcji obiektów na zestaw.</span><span class="sxs-lookup"><span data-stu-id="4dcd9-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="4dcd9-114">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4dcd9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4dcd9-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4dcd9-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4dcd9-116">Postępuj zgodnie z procedurą w [instrukcje: wykonywanie zapytania, które zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4dcd9-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="4dcd9-117">Przekaż następujące zapytanie jako argument do metody `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="4dcd9-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="4dcd9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dcd9-118">See also</span></span>

- [<span data-ttu-id="4dcd9-119">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4dcd9-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
