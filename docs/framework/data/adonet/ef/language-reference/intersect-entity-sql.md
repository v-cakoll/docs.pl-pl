---
title: INTERSECT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 85b0abb03161b2df0cfc4ddf6cafc92fb7de9d95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780383"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="632f9-102">INTERSECT (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="632f9-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="632f9-103">Zwraca kolekcję różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej stronie operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="632f9-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="632f9-104">Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="632f9-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="632f9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="632f9-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="632f9-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="632f9-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="632f9-107">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję do porównania z tą kolekcją zwrócony z innego wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="632f9-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="632f9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="632f9-108">Return Value</span></span>  
 <span data-ttu-id="632f9-109">Kolekcji tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="632f9-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="632f9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="632f9-110">Remarks</span></span>  
 <span data-ttu-id="632f9-111">INTERSECT jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu.</span><span class="sxs-lookup"><span data-stu-id="632f9-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="632f9-112">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="632f9-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="632f9-113">Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zestaw operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="632f9-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="632f9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="632f9-114">Example</span></span>  
 <span data-ttu-id="632f9-115">Następujące zapytanie SQL jednostki używa operatora INTERSECT zwrócić zbiór różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej stronie operandu INTERSECT.</span><span class="sxs-lookup"><span data-stu-id="632f9-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="632f9-116">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="632f9-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="632f9-117">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="632f9-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="632f9-118">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="632f9-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="632f9-119">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="632f9-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="632f9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="632f9-120">See also</span></span>

- [<span data-ttu-id="632f9-121">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="632f9-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
