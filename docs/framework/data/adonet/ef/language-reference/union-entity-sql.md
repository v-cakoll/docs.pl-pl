---
title: Unii (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 52a7a332166250e8fa8084986fd0d89da6fdf42d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="union-entity-sql"></a><span data-ttu-id="cd83b-102">Unii (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="cd83b-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="cd83b-103">Łączy wyniki dwóch lub więcej kwerend w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cd83b-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd83b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd83b-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cd83b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cd83b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cd83b-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję do łączenia z kolekcji wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="cd83b-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="cd83b-107">UNION</span><span class="sxs-lookup"><span data-stu-id="cd83b-107">UNION</span></span>  
 <span data-ttu-id="cd83b-108">Określa, że wiele kolekcji są łączone i zwracane w postaci jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cd83b-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="cd83b-109">WSZYSTKIE</span><span class="sxs-lookup"><span data-stu-id="cd83b-109">ALL</span></span>  
 <span data-ttu-id="cd83b-110">Określa, że wiele kolekcji są łączone i zwracane w postaci jednej kolekcji, w tym duplikaty.</span><span class="sxs-lookup"><span data-stu-id="cd83b-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="cd83b-111">Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wynik.</span><span class="sxs-lookup"><span data-stu-id="cd83b-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd83b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd83b-112">Return Value</span></span>  
 <span data-ttu-id="cd83b-113">Kolekcji tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="cd83b-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd83b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd83b-114">Remarks</span></span>  
 <span data-ttu-id="cd83b-115">Unii jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.</span><span class="sxs-lookup"><span data-stu-id="cd83b-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="cd83b-116">Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="cd83b-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="cd83b-117">Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cd83b-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd83b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd83b-118">Example</span></span>  
 <span data-ttu-id="cd83b-119">Następujące zapytanie SQL jednostki używa operatora UNION ALL do łączenia wyniki dwa zapytania w jednej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cd83b-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="cd83b-120">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="cd83b-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cd83b-121">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="cd83b-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cd83b-122">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cd83b-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cd83b-123">Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="cd83b-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="cd83b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd83b-124">See Also</span></span>  
 [<span data-ttu-id="cd83b-125">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="cd83b-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
