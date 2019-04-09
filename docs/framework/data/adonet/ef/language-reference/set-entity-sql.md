---
title: ZESTAW (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: dab124e139f3491c4a7a42eb90c4ffb3b3a92258
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158564"
---
# <a name="set-entity-sql"></a><span data-ttu-id="3a153-102">ZESTAW (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="3a153-102">SET (Entity SQL)</span></span>
<span data-ttu-id="3a153-103">Wyrażenie zestawu jest używana do konwersji kolekcji obiektów do zestawu, reaguje nową kolekcję z wszystkich elementów zduplikowane usunięte.</span><span class="sxs-lookup"><span data-stu-id="3a153-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a153-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a153-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a153-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3a153-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3a153-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="3a153-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a153-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a153-107">Remarks</span></span>  
 <span data-ttu-id="3a153-108">Wyrażenie zestawu `SET(c)` jest logicznie równoważne wybierz następującą instrukcję:</span><span class="sxs-lookup"><span data-stu-id="3a153-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` <span data-ttu-id="3a153-109">Przykładem jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a153-109">is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="3a153-110">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="3a153-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="3a153-111">Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a153-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a153-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a153-112">Example</span></span>  
 <span data-ttu-id="3a153-113">Następujące zapytanie SQL jednostki użyto wyrażenia zestawu do przekonwertowania kolekcji obiektów do zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a153-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="3a153-114">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3a153-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3a153-115">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3a153-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3a153-116">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3a153-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="3a153-117">Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="3a153-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="3a153-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a153-118">See also</span></span>

- [<span data-ttu-id="3a153-119">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3a153-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
